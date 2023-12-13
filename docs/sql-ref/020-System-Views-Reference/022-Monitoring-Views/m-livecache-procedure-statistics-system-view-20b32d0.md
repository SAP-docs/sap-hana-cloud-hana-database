<!-- loio20b32d0775191014a17986473fd358b2 -->

# M\_LIVECACHE\_PROCEDURE\_STATISTICS System View

Provides accumulated LiveCache procedure statistics.



<a name="loio20b32d0775191014a17986473fd358b2___m__l_i_v_e_c_a_c_h_e__p_r_o_c_e_d_u_r_e__s_t_a_t_i_s_t_i_c_s_1struct_M_LIVECACHE_PROCEDURE_STATISTICS"/>

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

OBJECT\_NAME

</td>
<td valign="top">

NVARCHAR\(128\)

</td>
<td valign="top">

Displays the object name.

</td>
</tr>
<tr>
<td valign="top">

METHOD\_NAME

</td>
<td valign="top">

NVARCHAR\(128\)

</td>
<td valign="top">

Displays the method name.

</td>
</tr>
<tr>
<td valign="top">

CALL\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of calls of the procedure.

</td>
</tr>
<tr>
<td valign="top">

SUM\_RUN\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total runtime of the procedure in microseconds.

</td>
</tr>
<tr>
<td valign="top">

MAX\_RUN\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum runtime of the procedure in microseconds.

</td>
</tr>
<tr>
<td valign="top">

MIN\_RUN\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the minimum runtime of the procedure in microseconds.

</td>
</tr>
<tr>
<td valign="top">

AVERAGE\_RUN\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the average runtime of the procedure in microseconds.

</td>
</tr>
<tr>
<td valign="top">

DEREF\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of OID derefs.

</td>
</tr>
<tr>
<td valign="top">

DEREF\_BASE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of OID derefs against basis.

</td>
</tr>
<tr>
<td valign="top">

DEREF\_BASE\_IN\_VERSION\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of OID derefs against basis from within an Object Management System version.

</td>
</tr>
<tr>
<td valign="top">

DEREF\_KEYED\_OBJECT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of key derefs.

</td>
</tr>
<tr>
<td valign="top">

DEREF\_KEYED\_OBJECT\_BASE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of key derefs against basis.

</td>
</tr>
<tr>
<td valign="top">

DEREF\_KEYED\_OBJECT\_BASE\_IN\_VERSION\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of key derefs against basis from within an OMS version.

</td>
</tr>
<tr>
<td valign="top">

ITER\_BASE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of objects read via an OID-iterator from the basis.

</td>
</tr>
<tr>
<td valign="top">

ITER\_KEYED\_OBJECT\_BASE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of objects read via a key-iterator from the basis.

</td>
</tr>
<tr>
<td valign="top">

ITER\_BASE\_IN\_VERSION\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of objects read via an OID-iterator from the basis from within an OMS version.

</td>
</tr>
<tr>
<td valign="top">

ITER\_IN\_VERSION\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of objects, created in an OMS-version, read via an OID-iterator .

</td>
</tr>
<tr>
<td valign="top">

ITER\_KEYED\_OBJECT\_BASE\_IN\_VERSION\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of objects read via an OID-iterator from the basis from within an OMS version.

</td>
</tr>
<tr>
<td valign="top">

ITER\_KEYED\_OBJECT\_IN\_VERSION\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of objects, created in an OMS version, read via a key-iterator.

</td>
</tr>
<tr>
<td valign="top">

DEREF\_VAR\_OBJECT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of derefs of var objects.

</td>
</tr>
<tr>
<td valign="top">

DEREF\_VAR\_OBJECT\_BASE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of derefs of var objects against basis.

</td>
</tr>
<tr>
<td valign="top">

DEREF\_VAR\_OBJECT\_BASE\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the accumulated size of var objects read from the basis in bytes.

</td>
</tr>
<tr>
<td valign="top">

DEREF\_VAR\_OBJECT\_BASE\_IN\_VERSION\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of derefs of var objects against basis from within an OMS version.

</td>
</tr>
<tr>
<td valign="top">

DEREF\_VAR\_OBJECT\_BASE\_IN\_VERSION\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the accumulated size of var objects read from the basis from within an OMS version in bytes.

</td>
</tr>
<tr>
<td valign="top">

NEW\_OBJECT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of newly created standard objects.

</td>
</tr>
<tr>
<td valign="top">

NEW\_KEYED\_OBJECT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of newly created keyed objects.

</td>
</tr>
<tr>
<td valign="top">

NEW\_VAR\_OBJECT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of newly created var objects.

</td>
</tr>
<tr>
<td valign="top">

NEW\_OBJECT\_IN\_VERSION\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of newly created standard objects in an OMS version.

</td>
</tr>
<tr>
<td valign="top">

NEW\_KEYED\_OBJECT\_IN\_VERSION\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of newly created keyed objects in an OMS version.

</td>
</tr>
<tr>
<td valign="top">

NEW\_VAR\_OBJECT\_IN\_VERSION\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of newly created var objects in an OMS version.

</td>
</tr>
<tr>
<td valign="top">

STORE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of store calls on standard objects.

</td>
</tr>
<tr>
<td valign="top">

STORE\_IN\_VERSION\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of store calls on standard objects in an OMS version.

</td>
</tr>
<tr>
<td valign="top">

STORE\_KEYED\_OBJECT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of store calls on keyed objects.

</td>
</tr>
<tr>
<td valign="top">

STORE\_KEYED\_OBJECT\_IN\_VERSION\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of store calls on keyed objects in an OMS version.

</td>
</tr>
<tr>
<td valign="top">

STORE\_VAR\_OBJECT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of store calls on var objects.

</td>
</tr>
<tr>
<td valign="top">

STORE\_VAR\_OBJECT\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the accumulated size of store calls on var objects in bytes.

</td>
</tr>
<tr>
<td valign="top">

STORE\_VAR\_OBJECT\_IN\_VERSION\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of store calls on var objects in an OMS version.

</td>
</tr>
<tr>
<td valign="top">

STORE\_VAR\_OBJECT\_IN\_VERSION\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the accumulated size of store calls on var objects in an OMS version in bytes.

</td>
</tr>
<tr>
<td valign="top">

STORE\_BASE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of updates of standard objects in the basis.

</td>
</tr>
<tr>
<td valign="top">

STORE\_KEYED\_OBJECT\_BASE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of updates of keyed objects in the basis.

</td>
</tr>
<tr>
<td valign="top">

STORE\_VAR\_OBJECT\_BASE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of updates of var objects in the basis.

</td>
</tr>
<tr>
<td valign="top">

STORE\_VAR\_OBJECT\_BASE\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the accumulated sizes of updated objects in the basis in bytes.

</td>
</tr>
<tr>
<td valign="top">

DELETE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of delete calls on standard objects.

</td>
</tr>
<tr>
<td valign="top">

DELETE\_KEYED\_OBJECT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of delete calls on keyed objects.

</td>
</tr>
<tr>
<td valign="top">

DELETE\_VAR\_OBJECT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of delete calls on var objects.

</td>
</tr>
<tr>
<td valign="top">

DELETE\_IN\_VERSION\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of delete calls on standard objects in an OMS version.

</td>
</tr>
<tr>
<td valign="top">

DELETE\_KEYED\_OBJECT\_IN\_VERSION\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of delete calls on keyed objects in an OMS version.

</td>
</tr>
<tr>
<td valign="top">

DELETE\_VAR\_OBJECT\_IN\_VERSION\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of delete calls on var objects in an OMS version.

</td>
</tr>
<tr>
<td valign="top">

DELETE\_BASE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of deleted standard objects in the basis.

</td>
</tr>
<tr>
<td valign="top">

DELETE\_KEYED\_OBJECT\_BASE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of deleted keyed objects in the basis.

</td>
</tr>
<tr>
<td valign="top">

DELETE\_VAR\_OBJECT\_BASE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of deleted var objects in the basis.

</td>
</tr>
<tr>
<td valign="top">

LOCK\_EXCLUSIVE\_BASE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of exclusive lock requests on standard objects in the basis.

</td>
</tr>
<tr>
<td valign="top">

LOCK\_SHARE\_BASE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of share lock requests on standard objects in the basis.

</td>
</tr>
<tr>
<td valign="top">

LOCK\_EXCLUSIVE\_KEYED\_OBJECT\_BASE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of exclusive lock requests on keyed objects in the basis.

</td>
</tr>
<tr>
<td valign="top">

LOCK\_SHARE\_KEYED\_OBJECT\_BASE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of share lock requests on keyed objects in the basis.

</td>
</tr>
<tr>
<td valign="top">

LOCK\_EXCLUSIVE\_VAR\_OBJECT\_BASE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of exclusive lock requests on var objects in the basis.

</td>
</tr>
<tr>
<td valign="top">

LOCK\_SHARE\_VAR\_OBJECT\_BASE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the nNumber of share lock requests on var objects in the basis.

</td>
</tr>
<tr>
<td valign="top">

RELEASE\_CALLED\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of OMS release calls.

</td>
</tr>
<tr>
<td valign="top">

RELEASE\_EXECUTED\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of released standard objects.

</td>
</tr>
<tr>
<td valign="top">

RELEASE\_EXECUTED\_KEYED\_OBJECT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of releases keyed objects.

</td>
</tr>
<tr>
<td valign="top">

RELEASE\_EXECUTED\_VAR\_OBJECT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of releases var objects.

</td>
</tr>
<tr>
<td valign="top">

HISTORY\_HOP\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of hops in the history chain during deref.

</td>
</tr>
<tr>
<td valign="top">

ITER\_HISTORY\_HOP\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of hops in the history chain during iteration.

</td>
</tr>
<tr>
<td valign="top">

EXCEPTION\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of dbp-exceptions thrown.

</td>
</tr>
<tr>
<td valign="top">

OUT\_OF\_DATE\_EXCEPTION\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of out-of-date-exceptions thrown.

</td>
</tr>
<tr>
<td valign="top">

OUT\_OF\_MEMORY\_EXCEPTION\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of out-of-memory-exceptions thrown.

</td>
</tr>
<tr>
<td valign="top">

TIMEOUT\_EXCEPTION\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of timeout-exceptions thrown.

</td>
</tr>
<tr>
<td valign="top">

OMS\_TERMINATE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of Object Management System \(OMS\) terminate calls.

</td>
</tr>
<tr>
<td valign="top">

SUBTRANSACTION\_ROLLBACK\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of rolled back sub-transactions.

</td>
</tr>
<tr>
<td valign="top">

SUBTRANSACTION\_COMMIT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of committed sub-transactions.

</td>
</tr>
<tr>
<td valign="top">

MAX\_SUBTRANSACTION\_LEVEL

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum subtransaction level.

</td>
</tr>
<tr>
<td valign="top">

NEW\_CONSISTENT\_VIEW\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of new-consistent-view calls with objects.

</td>
</tr>
<tr>
<td valign="top">

SUM\_NEW\_CONSISTENT\_VIEW\_WAIT\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the sum of the wait times of the new-consistent-view calls with objects.

</td>
</tr>
<tr>
<td valign="top">

AVERAGE\_NEW\_CONSISTENT\_VIEW\_WAIT\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the average wait time of new-consistent-view calls with objects in seconds.

</td>
</tr>
<tr>
<td valign="top">

NEW\_CONSISTENT\_VIEW\_MAX\_WAIT\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximal wait time of new-consistent-view calls with objects in seconds.

</td>
</tr>
<tr>
<td valign="top">

KEY\_CACHE\_HIT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of cache hits in the key-cache.

</td>
</tr>
<tr>
<td valign="top">

KEY\_MISS\_CACHE\_HIT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of cache hits in the key-miss-cache.

</td>
</tr>
<tr>
<td valign="top">

DEREF\_VERSION\_KEYED\_OBJECT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of key-derefs in an OMS version on objects created in this version.

</td>
</tr>
<tr>
<td valign="top">

OMS\_REHASH\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of rehashes of the OMS-object-hash.

</td>
</tr>
<tr>
<td valign="top">

AVERAGE\_HASH\_CHAIN\_SEARCH\_LENGTH

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the average search length on the hash-chains, in microseconds, of the OMS-object-hash.

</td>
</tr>
<tr>
<td valign="top">

MAX\_HASH\_CHAIN\_LENGTH

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum length of a hash-chain of the OMS-object-hash.

</td>
</tr>
<tr>
<td valign="top">

VERSION\_CREATE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of created OMS versions.

</td>
</tr>
<tr>
<td valign="top">

VERSION\_OPEN\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of open-version calls.

</td>
</tr>
<tr>
<td valign="top">

VERSION\_CLOSE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of close-version calls.

</td>
</tr>
<tr>
<td valign="top">

VERSION\_DROP\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of dropped OMS versions.

</td>
</tr>
<tr>
<td valign="top">

USER\_ALLOC\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of allocations via a user allocator.

</td>
</tr>
<tr>
<td valign="top">

USER\_MAX\_CHUNK\_ALLOCATED\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum size of a chunk allocated via a user allocator in bytes.

</td>
</tr>
<tr>
<td valign="top">

USER\_MIN\_CHUNK\_ALLOCATED\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the minimum size of a chunk allocated via a user allocator in bytes.

</td>
</tr>
<tr>
<td valign="top">

USER\_AVERAGE\_CHUNK\_ALLOCATED\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the average size of a chunk allocated via a user allocator in bytes.

</td>
</tr>
<tr>
<td valign="top">

USER\_DELETE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of deallocations via a user allocator.

</td>
</tr>
<tr>
<td valign="top">

USER\_MAX\_CHUNK\_DELETED\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum size of a chunk deallocated via a user allocator in bytes.

Displays the maximum size of a chunk deallocated via a user allocator in

</td>
</tr>
<tr>
<td valign="top">

USER\_MIN\_CHUNK\_DELETED\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the minimum size of a chunk deallocated via a user allocator in bytes.

</td>
</tr>
<tr>
<td valign="top">

USER\_AVERAGE\_CHUNK\_DELETED\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the average size of a chunk deallocated via a user allocator in bytes.

</td>
</tr>
<tr>
<td valign="top">

USER\_DELTA\_MAX\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximal difference in size between allocation and deallocation on a user allocator during the execution of a method in bytes.

</td>
</tr>
<tr>
<td valign="top">

OMS\_ALLOC\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of allocations via an OMS internal allocator.

</td>
</tr>
<tr>
<td valign="top">

OMS\_MAX\_CHUNK\_ALLOCATED\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum size of a chunk allocated via an OMS internal allocator in bytes.

</td>
</tr>
<tr>
<td valign="top">

OMS\_MIN\_CHUNK\_ALLOCATED\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the minimum size of a chunk allocated via an OMS internal allocator in bytes.

</td>
</tr>
<tr>
<td valign="top">

OMS\_AVERAGE\_CHUNK\_ALLOCATED\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the average size of a chunk allocated via an OMS internal allocator in bytes.

</td>
</tr>
<tr>
<td valign="top">

OMS\_DELETE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of deallocations via an OMS internal allocator.

</td>
</tr>
<tr>
<td valign="top">

OMS\_MAX\_CHUNK\_DELETED\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum size of a chunk deallocated via an OMS internal allocator in bytes.

</td>
</tr>
<tr>
<td valign="top">

OMS\_MIN\_CHUNK\_DELETED\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the minimum size of a chunk deallocated via an OMS internal allocator in bytes.

</td>
</tr>
<tr>
<td valign="top">

OMS\_AVERAGE\_CHUNK\_DELETED\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the average size of a chunk deallocated via an OMS internal allocator in bytes.

</td>
</tr>
<tr>
<td valign="top">

OMS\_DELTA\_MAX\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum difference in size between allocation and deallocation on an OMS internal allocator during the execution of a method in bytes.

</td>
</tr>
<tr>
<td valign="top">

LAST\_USER\_DELTA\_MAX\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the last peak delta of the user heap consumption during procedure execution in bytes.

</td>
</tr>
<tr>
<td valign="top">

MAX\_USER\_DELTA\_MAX\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum peak delta of the user heap consumption during procedure execution in bytes.

</td>
</tr>
<tr>
<td valign="top">

MIN\_USER\_DELTA\_MAX\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the minimum peak delta of the user heap consumption during procedure execution in bytes.

</td>
</tr>
<tr>
<td valign="top">

SUM\_USER\_DELTA\_MAX\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total peak delta of the user heap consumption during procedure execution in bytes.

</td>
</tr>
<tr>
<td valign="top">

AVG\_USER\_DELTA\_MAX\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the peak delta of the user heap consumption during procedure execution in bytes.

</td>
</tr>
<tr>
<td valign="top">

LAST\_OMS\_DELTA\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the last delta of the OMS heap consumption between start and end of the procedure execution in bytes.

</td>
</tr>
<tr>
<td valign="top">

MAX\_OMS\_DELTA\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum delta of the OMS heap consumption between the start and end of the procedure execution in bytes.

</td>
</tr>
<tr>
<td valign="top">

MIN\_OMS\_DELTA\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the minimum delta of the OMS heap consumption between the start and end of the procedure execution in bytes.

</td>
</tr>
<tr>
<td valign="top">

SUM\_OMS\_DELTA\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total delta of the OMS heap consumption between the start and end of the procedure execution in bytes.

</td>
</tr>
<tr>
<td valign="top">

AVG\_OMS\_DELTA\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the average delta of the OMS heap consumption between the start and end of the procedure execution in bytes.

</td>
</tr>
<tr>
<td valign="top">

LAST\_VERSION\_DELTA\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the last delta of the OMS version heap consumption between the start and end of the procedure execution in bytes.

</td>
</tr>
<tr>
<td valign="top">

MAX\_VERSION\_DELTA\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum delta of the OMS version heap consumption between the start and end of the procedure execution in bytes.

</td>
</tr>
<tr>
<td valign="top">

MIN\_VERSION\_DELTA\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the minimum delta of the OMS version heap consumption between the start and end of the procedure execution in bytes.

</td>
</tr>
<tr>
<td valign="top">

SUM\_VERSION\_DELTA\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total delta of the OMS version heap consumption between the start and end of the procedure execution in bytes.

</td>
</tr>
<tr>
<td valign="top">

AVG\_VERSION\_DELTA\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the average delta of the OMS version heap consumption between the start and end of the procedure execution in bytes.

</td>
</tr>
<tr>
<td valign="top">

LAST\_HEAP\_DELTA\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the last delta of the overall heap consumption \(user + OMS + OMS version\) between the start and end of the procedure execution.

</td>
</tr>
<tr>
<td valign="top">

MAX\_HEAP\_DELTA\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum delta of the overall heap consumption \(user + OMS + OMS version\) between the start and end of the procedure execution in bytes.

</td>
</tr>
<tr>
<td valign="top">

MIN\_HEAP\_DELTA\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the minimum delta of the overall heap consumption \(user + OMS + OMS version\) between the start and end of the procedure execution in bytes.

</td>
</tr>
<tr>
<td valign="top">

SUM\_HEAP\_DELTA\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total delta of the overall heap consumption \(user + OMS + OMS version\) between the start and end of the procedure execution in bytes.

</td>
</tr>
<tr>
<td valign="top">

AVG\_HEAP\_DELTA\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the average delta of the overall heap consumption \(user + OMS + OMS version\) between the start and end of the procedure execution in bytes.

</td>
</tr>
<tr>
<td valign="top">

STREAM\_COMMUNICATION\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total stream communication time in microseconds.

</td>
</tr>
<tr>
<td valign="top">

MAX\_STREAM\_COMMUNICATION\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum stream communication time in microseconds.

</td>
</tr>
<tr>
<td valign="top">

MIN\_STREAM\_COMMUNICATION\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the minimum stream communication time in microseconds.

</td>
</tr>
<tr>
<td valign="top">

AVG\_STREAM\_COMMUNICATION\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the average stream communication time in microseconds.

</td>
</tr>
<tr>
<td valign="top">

STREAM\_READ\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of communications for reading ABAP tables.

</td>
</tr>
<tr>
<td valign="top">

STREAM\_WRITE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of communications for writing ABAP tables.

</td>
</tr>
<tr>
<td valign="top">

STREAM\_READ\_ROW\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of rows read from ABAP tables.

</td>
</tr>
<tr>
<td valign="top">

STREAM\_WRITE\_ROW\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of rows written to ABAP tables.

</td>
</tr>
<tr>
<td valign="top">

LAST\_INTERNAL\_SQL\_PREPARE\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays last the internal SQL prepare time.

</td>
</tr>
<tr>
<td valign="top">

MAX\_INTERNAL\_SQL\_PREPARE\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum internal SQL prepare time.

</td>
</tr>
<tr>
<td valign="top">

MIN\_INTERNAL\_SQL\_PREPARE\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the minimum internal SQL prepare time.

</td>
</tr>
<tr>
<td valign="top">

SUM\_INTERNAL\_SQL\_PREPARE\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total internal SQL prepare time.

</td>
</tr>
<tr>
<td valign="top">

AVG\_INTERNAL\_SQL\_PREPARE\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the average internal SQL prepare time.

</td>
</tr>
<tr>
<td valign="top">

LAST\_INTERNAL\_SQL\_EXECUTE\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the last internal SQL execute time.

</td>
</tr>
<tr>
<td valign="top">

MAX\_INTERNAL\_SQL\_EXECUTE\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum internal SQL execute time.

</td>
</tr>
<tr>
<td valign="top">

MIN\_INTERNAL\_SQL\_EXECUTE\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the minimum internal SQL execute time.

</td>
</tr>
<tr>
<td valign="top">

SUM\_INTERNAL\_SQL\_EXECUTE\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total internal SQL execute time.

</td>
</tr>
<tr>
<td valign="top">

AVG\_INTERNAL\_SQL\_EXECUTE\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the average internal SQL execute time.

</td>
</tr>
<tr>
<td valign="top">

LAST\_INTERNAL\_SQL\_FETCH\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the last internal SQL fetch time.

</td>
</tr>
<tr>
<td valign="top">

MAX\_INTERNAL\_SQL\_FETCH\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum internal SQL fetch time.

</td>
</tr>
<tr>
<td valign="top">

MIN\_INTERNAL\_SQL\_FETCH\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the minimum internal SQL fetch time.

</td>
</tr>
<tr>
<td valign="top">

SUM\_INTERNAL\_SQL\_FETCH\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total internal SQL fetch time.

</td>
</tr>
<tr>
<td valign="top">

AVG\_INTERNAL\_SQL\_FETCH\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the avg internal SQL fetch time.

</td>
</tr>
</table>



<a name="loio20b32d0775191014a17986473fd358b2___m__l_i_v_e_c_a_c_h_e__p_r_o_c_e_d_u_r_e__s_t_a_t_i_s_t_i_c_s_1fulldesc_M_LIVECACHE_PROCEDURE_STATISTICS"/>

## Additional Information

This view can only be used if liveCache is enabled.

For each liveCache procedure called since the last restart, statistics are shown.

This view has a resettable counterpart; you can see the values since the last reset in the M\_LIVECACHE\_PROCEDURE\_STATISTICS\_RESET system view. To reset the view, execute the following statement: `ALTER SYSTEM RESET MONITORING VIEW SYS.M_LIVECACHE_PROCEDURE_STATISTICS_RESET;`.

**Related Information**  


[M\_LIVECACHE\_PROCEDURE\_STATISTICS\_RESET System View](m-livecache-procedure-statistics-reset-system-view-20b351e.md "LiveCache procedure statistics (since last reset).")

[ALTER SYSTEM RESET MONITORING VIEW Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-reset-monitoring-view-statement-system-management-20d27aa.md "Resets statistics data for the specified monitoring view.")

[STATISTICS_OBJECTS Table (Embedded Statistics Service)](https://help.sap.com/viewer/323c57a017234d47a0e7da3e22345822/2023_4_QRC/en-US/cadabaac2e1749f79294970c1ec74b4c.html "Statistics of objects per host. This view contains information only for the last 7 days.") :arrow_upper_right:

[Managing Statistics](https://help.sap.com/viewer/477aa413a36c4a95878460696fcc8896/2023_4_QRC/en-US/0a9ae9e9ccc743f4a2808399da354657.html "Statistics assist the query optimizer in making better decisions and work for both virtual tables and linked database.") :arrow_upper_right:

[Procedures](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2023_4_QRC/en-US/d43d91578c3b42b3bacfd89aacf0d62f.html "") :arrow_upper_right:

