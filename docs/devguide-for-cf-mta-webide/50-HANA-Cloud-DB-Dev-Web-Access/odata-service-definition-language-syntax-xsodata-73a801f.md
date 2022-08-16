<!-- loio73a801f25cbf425994f22b06d3850591 -->

# OData Service Definition Language Syntax \(XSOData\)

The OData Service Definition Language \(OSDL\) provides a set of keywords that enable you to set up an ODATA service definition file that specifies what data to expose, in what way, and to whom.



The following list shows the syntax of the OData Service Definition Language \(OSDL\) in an EBNF-like format; conditions that apply for usage are listed after the table.

```
definition             :=service [annotations]
service				:='service' [namespace] body
namespace              :='namespace' quotedstring
quotedstring           :=quote string quote
string                 :=UTF8
quote                  :='"'
body                   :='{' content '}'
content                :=entry [content]
entry                  :=( entity | association ) ';'
entity                 :=object [entityset] [with] [keys] [navigates] [aggregates] [parameters] [modification]
object                 :=['entity'] ( repoobject | catalogobject )
repoobject             :=quote repopackage '/' reponame '.' repoextension quote
repopackage            :=string
reponame               :=string
repoextension          :=string
catalogobject          :=catalogobjectschema '.' catalogobjectname
catalogobjectschema    :=quotedstring
catalogobjectname      :=quotedstring
entityset              :='as' entitysetname
entitysetname          :=quotedstring
with                   :=( 'with' | 'without' ) propertylist
propertylist           :='(' columnlist ')'
columnlist             :=columnname [',' columnlist]
columnname             :=quotedstring
keys                   :='keys' ( keylist | keygenerated )
keylist                :=propertylist
keygenerated           :='generate' ( keygenlocal ) 
keygenlocal            :='local' columnname
navigates              :='navigates' '(' navlist ')'
navlist                :=naventry [',' navlist]
naventry               :=assocname 'as' navpropname [fromend]
assocname              :=quotedstring
navpropname            :=quotedstring
fromend                :='from' ( 'principal' | 'dependent' )
aggregates             :='aggregates' 'always' [aggregatestuple]
aggregatestuple        :='(' aggregateslist ')'
aggregateslist         :=aggregate [',' aggregateslist]
aggregate              :=aggregatefunction 'of' columnname
aggregatefunction      :=( 'SUM' | 'AVG' | 'MIN' | 'MAX' )
parameters             :='parameters' 'via' [parameterskeyand] 'entity' [parameterentitysetname] [parametersresultsprop]
parameterskeyand       :='key' 'and'
parameterentitysetname :=quotedstring
parametersresultsprop  :='results' 'property' quotedstring
modification           :=[create] [update] [delete]	
create                 :='create' modificationspec
update                 :='update' modificationspec
delete                 :='delete' modificationspec
modificationspec	   :=( modificationaction [events] | events | 'forbidden' )
modificationaction	 :='using' action
action                 :=quotedstring
events                 :='events' '(' eventlist ')'
eventlist              :=eventtype action [',' eventlist]
eventtype              :=( 'before' | 'after' | 'precommit' | 'postcommit' )
association            :=associationdef [assocrefconstraint] principalend dependentend [( assoctable | storage | modification )]
associationdef         :='association' assocname
assocrefconstraint     :=‘with’ ‘referential’ ‘constraint'
principalend           :='principal' end
dependentend           :='dependent' end
end                    :=endref multiplicity
endref                 :=endtype [joinpropertieslist]
endtype                :=entitysetname
joinpropertieslist	 :='(' joinproperties ')'
joinproperties         :=columnlist
multiplicity           :='multiplicity' quote multiplicityvalue quote
multiplicityvalue      :=( '1' | '0..1' | '1..*' | '*' )
assoctable             :='over' repoobject overprincipalend overdependentend [modification]
overprincipalend       :='principal' overend
overdependentend       :='dependent' overend
overend                :=propertylist 
storage                :=( nostorage | storageend [modification] )
nostorage              :='no' 'storage'
storageend             :='storage' 'on' ( 'principal' | 'dependent' )
annotations            :='annotations' annotationsbody
annotationsbody        :='{' annotationscontent '}'
annotationscontent     :=annotationconfig [annotationscontent]
annotationconfig       :='enable' annotation
annotation             :='OData4SAP' 
```

> ### Note:  
> Support for OData annotations is currently not available in SAP HANA XSOData.



<a name="loio73a801f25cbf425994f22b06d3850591__section_N10023_N10012_N10001"/>

## Conditions

The following conditions apply when using the listed keywords:

1.  If the `namespace` is not specified, the schema namespace in the EDMX metadata document will be the repository package of the service definition file concatenated with the repository object name. E.g. if the repository design time name of the `.xsodata` file is`sap.hana.xs.doc/hello.xsodata` the namespace will implicitly be `sap.hana.xs.doc.hello`.
2.  `keyslist` must not be specified for objects of type 'table'. They must only be applied to objects referring a view type. `keygenerated` in turn, can be applied to table objects.
3.  If the `entityset` is not specified in an entity, the EntitySet for this object is named after the repository object name or the `catalogobjectname`. For example, if `object` is "`sap.hana.xs.doc/odata_docu`", then the `entitysetname` is implicitly set to `odata_docu`, which then can also be referenced in associations.
4.  The `fromend` in a `naventry` must be specified if the `endtype` is the same for both the `principalend` and the `dependentend` of an association.
5.  The number of `joinproperties` in the `principalend` must be the same as in the `dependentend`.
6.  Ordering in the `joinproperties` of `ends` is relevant. The first `columnname` in the `joinproperties` of the `principalend` is compared with the first `columnname` of the `dependentend`, the second with the second, and so on.
7.  The `overprincipalend` corresponds to the `principalend`. The number of properties in the `joinproperties` and the `overproperties` must be the same and their ordering is relevant. The same statement is true for the dependent end.
8.  `aggregates` can only be applied in combination with `keygenerated`.
9.  If `aggregatestuple` is omitted, the aggregation functions are derived from the database. This is only possible for calculation views and analytic views.
10. Specifying `parameters` is only possible for calculation views and analytic views.
11. The default `parameterentitysetname` is the `entitysetname` of the entity concatenated with the suffix "`Parameters`".
12. If the `parametersresultsprop` is omitted, the navigation property from the parameter entity set to the entity is called "`Results`".
13. Support for OData `annotations` is currently under development. For more information about the SAP-specific metadata annotations that become available with the `enable OData4SAP` statement in an `.xsodata` file, see the Related Links below. Note that not all annotations allowed by OData are supported by SAP HANA XS.

**Related Information**  


[SAP Annotations for OData](http://scn.sap.com/docs/DOC-44986)

[Open Data Protocol](http://www.odata.org)

