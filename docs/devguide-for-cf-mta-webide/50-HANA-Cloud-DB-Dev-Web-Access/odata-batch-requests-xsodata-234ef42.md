<!-- loio234ef42fca2e4b92997e1d07cae61d3e -->

# OData Batch Requests \(XSOData\)

The OData standard allows the collection of multiple individual HTTP requests into one single batched HTTP request.

Clients using a defined OData service to consume exposed data can collect multiple, individual HTTP requests, for example, retrieve, create, update and delete \(GET, POST, PUT, DELETE\), in a single “batch” and send the batched request to the OData service as a single HTTP request. You can compile the batch request manually \(by creating the individual requests in the batch document by hand\) or automatically, for example, with an AJAX call that adds requests to a queue and loops through the queues to build the batch request. In both cases, the OData standard specifies the syntax required for the header and body elements of a valid batch request document.

SAP HANA XSOData supports the OData `$batch` feature out-of-the-box; there is nothing to configure in SAP HANA XSOData to use $batch to perform operations in SAP HANA using an OData service. To understand how the $batch feature works, you need to look at the following phases of the operation:

-   Batch Request
-   Batch Response

A batch request is split into two parts: the request header and the request body. The body of a batch request consists of a list of operations in a specific order where each operation either retrieves data \(for example, using the HTTP `GET` command\) or requests a change. A change request involves one or more insert, update or delete operations using the `POST`, `PUT`, or `DELETE` commands.

> ### Note:  
> A change request must not contain either a **retrieve** request or any nested change requests.

The batch request must contain a `Content-Type` header specifying the value “`multipart/mixed`” and a boundary ID `boundary=batch_#`; the batch boundary ID is then used to indicate the start of each batch request, as illustrated in the following example.

```
POST /service/$batch HTTP/1.1 
Host: host 
Content-Type: multipart/mixed;boundary=batch_8219-6895         // Define batch ID

--batch_8219-6895                                              // Batch 1 start

  Content-Type: multipart/mixed; boundary=changeset_a4e3-a738 // Define changeset ID
  --changeset_a4e3-a738                                        // Changeset 1 start
    Content-Type: application/http 
    Content-Transfer-Encoding: binary 
    [PUT...]  
 
  --changeset_a4e3-a738                                        // Changeset 2 start
    Content-Type: application/http 
    Content-Transfer-Encoding: binary 
    [POST...]

  --changeset_a4e3-a738--                                     // Changeset (all) end

--batch_8219-6895                                              // Batch part 2 start
  Content-Type: application/http 
  Content-Transfer-Encoding:binary 
  [GET...]

--batch_8219-6895--                                            // Batch (all) end
```

Within the batch request, change set is defined by another boundary ID \(for example, `boundary=changeset_123`\), which is then used to indicate the start and end of the change requests. The batch request must be closed, too.

> ### Note:  
> In the following example of a simple OData batch request, some content has been removed to emphasize the structure and layout.

```
POST http://localhost:8002/sap/sample/odata/syntax.xsodata/$batch HTTP/1.1
Host: localhost:8002
Connection: keep-alive
Content-Length: 471
User-Agent: Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/30.0.1599.101 Safari/537.36
Cache-Control: no-cache
Content-Type: multipart/mixed; boundary=batch_123
Accept: */*
Accept-Encoding: identity
Accept-Language: en-US,en;q=0.8
x-sap-request-language: en-US

--batch_123
Content-Type:multipart/mixed;boundary=changeset_456
Content-Transfer-Encoding:binary

--changeset_456
Content-Type:application/http
Content-Transfer-Encoding:binary

POST BatchSample HTTP/1.1
Content-Type:application/json
Content-Length:11

{"ID" : 14}
--changeset_456
Content-Type:application/http
Content-Transfer-Encoding:binary

POST BatchSample HTTP/1.1
Content-Type:application/json
Content-Length:11
Accept: application/json

{"ID" : 15}
--changeset_456--

--batch_123--

```

The batch response includes a response for each of the retrieve or change operations included in the corresponding batch request. The order of the responses in the response body must match the order of requests in the batch request. In the context of the batch response, the following is true:

-   The response to a retrieve request is always formatted in the same way regardless of whether it is sent individually or as part of batch.
-   The body of the collected response to a set of change-requests is one of the following:
    -   A response for **all** the successfully processed change requests within the change set, in the correct order and formatted exactly as it would have appeared outside of a batch
    -   A single response indicating the failure of the entire change set


The following example shows the form and syntax of the OData batch response to the request illustrated above.

```
HTTP/1.1 202 Accepted
content-type: multipart/mixed; boundary=0CDF14D90919CC8B4A32BD0E0B330DA10
content-length: 2029
content-language: en-US
cache-control: no-cache
expires: Thu, 01 Jan 1970 00:00:00 GMT

--0CDF14D90919CC8B4A32BD0E0B330DA10
Content-Type: multipart/form-data; boundary=0CDF14D90919CC8B4A32BD0E0B330DA11
Content-Length:      1843

--0CDF14D90919CC8B4A32BD0E0B330DA11
Content-Type: application/http
Content-Length: 1118
content-transfer-encoding: binary

HTTP/1.1 201 Created
Content-Type: application/atom+xml;charset=utf-8
location: http://localhost:8002/sap/sample/odata/syntax.xsodata/BatchSample(14)/
Content-Length: 943

<?xml version="1.0" encoding="utf-8" standalone="yes"?><entry xml:base="http://localhost:8002/sap/sample/odata/syntax.xsodata/" xmlns:d="http://schemas.microsoft.com/ado/2007/08/dataservices" xmlns:m="http://schemas.microsoft.com/ado/2007/08/dataservices/metadata" xmlns="http://www.w3.org/2005/Atom"><id>http://localhost:8002/sap/sample/odata/syntax.xsodata/BatchSample(14)</id><title type="text"></title><author><name /></author><link rel="edit" title="BatchSample" href="BatchSample(14)"/><link rel="http://schemas.microsoft.com/ado/2007/08/dataservices/related/Ref" type="application/atom+xml;type=entry" title="Ref" href="BatchSample(14)/Ref"></link><category term="sap.sample.odata.syntax.BatchSampleType" scheme="http://schemas.microsoft.com/ado/2007/08/dataservices/scheme" /><content type="application/xml"><m:properties><d:ID m:type="Edm.Int32">14</d:ID><d:SELFID m:type="Edm.Int32" m:null="true"></d:SELFID></m:properties></content></entry>
--0CDF14D90919CC8B4A32BD0E0B330DA11
Content-Type: application/http
Content-Length: 427
content-transfer-encoding: binary

HTTP/1.1 201 Created
Content-Type: application/json
location: http://localhost:8002/sap/sample/odata/syntax.xsodata/BatchSample(15)
Content-Length: 271

{"d":{"__metadata": {"uri":"http://localhost:8002/sap/sample/odata/syntax.xsodata/BatchSample(15)","type":"sap.sample.odata.syntax.BatchSampleType"},"ID":15,"SELFID":null,"Ref":{"__deferred":{"uri":"http://localhost:8002/sap/sample/odata/syntax.xsodata/BatchSample(15)/Ref"}}}}
--0CDF14D90919CC8B4A32BD0E0B330DA11--

--0CDF14D90919CC8B4A32BD0E0B330DA10--

```



## OData Batch Requests in SAPUI5 Applications

If you are developing a UI client using SAPUI5, you can make use of the ODataModel tools to ensure that the data requests generated by the various UI controls bound to an OData service are collected and sent in batches. The SAPUI5 ODataModel toolset includes a large selection of tools you can use to configure the use of the OData batch feature, for example:

-   `setUseBatch`

    Enable or disable batch processing for all requests \(read and change\)

-   `addBatchChangeOperations`

    Appends the change operations to the end of the batch stack, which is sent with the `submitBatch` function

-   `addBatchReadOperations`

    Appends the read operations to the end of the batch stack, which is sent with the `submitBatch` function

-   `submitBatch`

    Submits the collected changes in the batch which were collected via `addBatchReadOperations` or `addBatchChangeOperations`.


**Related Information**  


[Open Data Protocol](http://www.odata.org)

[SAPUI5 ODataModel Reference](https://sapui5.hana.ondemand.com/sdk/#docs/api/symbols/sap.ui.model.odata.html)

