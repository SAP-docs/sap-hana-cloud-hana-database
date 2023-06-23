<!-- loio20c98ad77519101490dedad2c724cdd3 -->

# M\_UNDO\_CLEANUP\_FILES System View

Provides information about undo files and cleanup files.



<a name="loio20c98ad77519101490dedad2c724cdd3___m__u_n_d_o__c_l_e_a_n_u_p__f_i_l_e_s_1struct_M_UNDO_CLEANUP_FILES"/>

## Structure


<table>
<tr>
<th valign="top">

Column name



</th>
<th valign="top">

Data type



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

HOST



</td>
<td valign="top">

NVARCHAR\(64\)



</td>
<td valign="top">

Displays the host name.



</td>
</tr>
<tr>
<td valign="top">

PORT



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the internal port number.



</td>
</tr>
<tr>
<td valign="top">

VOLUME\_ID



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the persistence volume ID.



</td>
</tr>
<tr>
<td valign="top">

TYPE



</td>
<td valign="top">

NVARCHAR\(16\)



</td>
<td valign="top">

Displays the file type: UNDO, CLEANUP, or FREE.



</td>
</tr>
<tr>
<td valign="top">

TID



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the transaction ID.



</td>
</tr>
<tr>
<td valign="top">

PAGE\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the page count.



</td>
</tr>
<tr>
<td valign="top">

RAW\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the raw size in bytes.



</td>
</tr>
<tr>
<td valign="top">

CLEANUP\_MARK



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the cleanup position mark.



</td>
</tr>
<tr>
<td valign="top">

NESTED\_SESSION\_ID



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the nested session ID.



</td>
</tr>
<tr>
<td valign="top">

NESTED\_SESSION\_PARENT\_ID



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the nested session parent ID.



</td>
</tr>
<tr>
<td valign="top">

DEPENDENT\_INDEX



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the dependent index during redo.



</td>
</tr>
<tr>
<td valign="top">

INDOUBT\_FLAG



</td>
<td valign="top">

NVARCHAR\(5\)



</td>
<td valign="top">

Displays the indoubt flag for distributed transaction: TRUE/FALSE.



</td>
</tr>
<tr>
<td valign="top">

TENTATIVE\_PRECOMMIT\_POSITION



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the tentative precommit position.



</td>
</tr>
<tr>
<td valign="top">

COMMIT\_ID



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the commit ID. This value is -1 for non-committed transactions.



</td>
</tr>
</table>



<a name="loio20c98ad77519101490dedad2c724cdd3___m__u_n_d_o__c_l_e_a_n_u_p__f_i_l_e_s_1fulldesc_M_UNDO_CLEANUP_FILES"/>

## Additional Information

Each undo or cleanup file in the system is represented by one row in this view. Undo files contain information needed for transaction rollback. These files are removed on transaction end. If data is deleted but must still be accessible because of MVCC isolation, then the corresponding information is written to cleanup files..

At the end of the transaction, cleanup files are passed to history management. Garbage collection uses the cleanup files to finally remove data. Undo files and cleanup files may be cached and reused because of performance issues. Cached files are assigned the type FREE. Undo files for row store are assigned the type EXTERNALUNDO.

**Related Information**  


[M\_GARBAGE\_COLLECTION\_STATISTICS System View](m-garbage-collection-statistics-system-view-20b04b8.md "Provides garbage collection and history manager statistics.")

