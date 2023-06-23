<!-- loio20d39db97519101480e7f9b76f48c2c4 -->

# COMMIT Statement \(Transaction Management\)

Makes changes to the database permanent, or terminates a user-defined transaction.



<a name="loio20d39db97519101480e7f9b76f48c2c4__sql_commit_1sql_commit_syntax"/>

## Syntax

```
COMMIT
```



<a name="loio20d39db97519101480e7f9b76f48c2c4__sql_commit_1sql_commit_description"/>

## Description

The system supports transactional consistency that guarantees the current job to be either completely applied to the system or disposed of.

If a user wants to apply the current job to the system persistently, then the user should issue a COMMIT command. If a COMMIT command is issued and successfully processed, then any change on the system that the current transaction has done is applied to the system and the change is visible to other jobs that start later. A job that has already been committed a via COMMIT command cannot be reverted.

In a distributed system, a standard two-phase-commit protocol is complied. In the first phase, transaction coordinator consults every participant whether if it is ready to commit, and sends the result to the participants in the second phase. The COMMIT command only works with an autocommit-disabled session.



<a name="loio20d39db97519101480e7f9b76f48c2c4__sql_commit_1sql_commit_example"/>

## Example

```
COMMIT;
```

