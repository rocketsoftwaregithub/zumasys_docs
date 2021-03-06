# jSQL

<PageHeader />

**Tags:**
<badge text='jsql' vertical='middle' />

## Using SQL against a jBASE Database  

jBASE includes support for a subset of the ANSI standard for SQL (Structured Query Language). Typical use of SQL against a jBASE database is via ODBC and JODBC but the same query structure can be used in any jBASE environment/program preceding the command with **SQL**.

In this document the term *tables* is synonymous with *files*.

> ***Note***: all commands that incur database updates will impact the jBASE database
in the same way as other I/O operations (i.e. [Transaction Journalling](../../transactions/transaction-journaling/#transaction-journaling-the-manual), [Auditing](../../faq/introduction-to-audit-logging/#document-scope)).

See also [Introduction to ODBC](../../connectivity/ODBC/README.md)

## Commands used against tables  

**SQLDELETE**  
**SQLDESCRIBE**  
**SQLINSERT**  
**SQLSELECT**  
**SQLUPDATE**  

The following command is a special case query command that returns an active select list:  

**SQLSELECTL**  
 (see [jQL](../../jql/README.md) for more information on *select lists*)

## Commands for administering tables

**SQLALTERTABLE**  
**SQLDROPTABLE**  
**SQLCREATETABLE**  

## Examples

### SQLCREATETABLE

Example usage:

``` sql
jsh -->SQLCREATETABLE JSQLDEMO (FIRSTNAME VARCHAR(30) NOT NULL, LASTNAME VARCHAR(30) NOT NULL, BIRTHDAY DATE)
Table JSQLDEMO created successfully.
```

### Note

>In the above example no PRIMARY KEY was specified.

``` shell
jsh -->LISTDICT JSQLDEMO

DICT PATH : DICT JSQLDEMO                                                                          Page   1 08:49:07  30 JAN 20

*A0...........    D/CODE...    A/AMC....    S/NAME...    V/CONV...    V/CORR...    V/TYPE...    V/MAX

RECID             A            0            RECID                                  R               20
BIRTHDAY          A            1            BIRTHDAY     DOD                       R               10
FIRSTNAME         A            2            FIRSTNAME                              L               30
LASTNAME          A            3            LASTNAME                               L               30

 4 Records Listed
```

As you can see the dictionary portion of the file generated by the CREATE TABLE command was populated including a default **RECID** column which was added and will auto increment starting at **1**. The next key value is stored in the DESCRIPTION field in the [Extended Dictionary](../../files/extended-dictionary/README.md) of **RECID**.

Another example this time specifying the primary key:

``` sql
jsh -->SQLCREATETABLE CATEGORY (ID INT NOT NULL, DESCRIPTION VARCHAR(30) NOT NULL, PRIMARY KEY(ID))
Table CATEGORY created successfully.
```

### SQLDESCRIBE

Example usage:

``` sql
jsh -->SQLDESCRIBE JSQLDEMO
COL_NO  NAME                 HEADING              TYPE                 SQLNULL READ_ONLY  BLOB  VISIBLE  PRIMARY_Controller PRIMARY_PART    USER_VIEW
------- -------------------- -------------------- -------------------- ------- ---------- ----- -------- ------------------ --------------- ------------------------------
1       BIRTHDAY             BIRTHDAY             DATE                 YES     NO         NO    YES      NO                 NO              DOD
2       FIRSTNAME            FIRSTNAME            CSTRING(30)          YES     NO         NO    YES      NO                 NO
3       LASTNAME             LASTNAME             CSTRING(30)          YES     NO         NO    YES      NO                 NO
4       RECID                RECID                AUTONUMBER           YES     NO         NO    YES      NO                 NO

Selected 4 rows.
```

The following properties - **SQLNULL**, **BLOB**, **PRIMARY_Controls**, **PRIMARY_PART** are only relevant if your SQL Catalog entry is pointing to an Oracle or DB2 jEDI type file.

### SQLINSERT

Example usage:

``` sql
jsh -->SQLINSERT INTO JSQLDEMO (FIRSTNAME, LASTNAME, BIRTHDAY) VALUES ('ANSI', 'SQL', '01 JAN 1986')
1 Records INSERTED successfully.
jsh -->SQLSELECT * FROM JSQLDEMO
RECID                BIRTHDAY   FIRSTNAME                      LASTNAME
-------------------- ---------- ------------------------------ ------------------------------
                   1 1986-01-01 ANSI                           SQL

Selected 1 rows.
```

### SQLALTERTABLE

Example usage: add a new column with a default value:

``` sql
jsh -->SQLALTERTABLE JSQLDEMO ADD (CATEGORY VARCHAR(20) DEFAULT 'DATABASE')
Updated 1 rows.
jsh -->SQLINSERT INTO JSQLDEMO (ID, FIRSTNAME, LASTNAME, BIRTHDAY) VALUES (1, 'PICK', 'SYSTEMS', '01 JAN 1968')
1 Records INSERTED successfully.
jsh -->SQLSELECT * FROM JSQLDEMO
RECID                BIRTHDAY   FIRSTNAME                      LASTNAME                       CATEGORY
-------------------- ---------- ------------------------------ ------------------------------ --------------------
                   1 1986-01-01 ANSI                           SQL
                   2 1968-01-01 PICK                           SYSTEMS                        DATABASE

Selected 2 rows.
```

### SQLUPDATE

Example usage:

``` sql
jsh -->SQLUPDATE JSQLDEMO SET CATEGORY = 'TYPE OF DATABASE' WHERE RECID = '2'
Updated 1 rows.
jsh -->SQLSELECT * FROM JSQLDEMO
RECID                BIRTHDAY   FIRSTNAME                      LASTNAME                       CATEGORY
-------------------- ---------- ------------------------------ ------------------------------ --------------------
                   2 1968-01-01 PICK                           SYSTEMS                        DATABASE
                   1 1986-01-01 ANSI                           SQL                            TYPE OF DATABASE

Selected 2 rows.
```

***CAUTION:***  
> Take care when using **SQLUPDATE** that your *WHERE* clause does not inadvertently match more records than you intended.

### SQLSELECTL

Example usage:

``` sql
jsh -->SQLSELECTL RECID FROM JSQLDEMO WHERE FIRSTNAME = 'PICK'
1 Items selected
```

Now with an active select list you can save it or use any other applicable [jQL](../../jql/README.md) command.

``` shell
>SAVE-LIST PICK
1 record(s) saved to list 'PICK'
jsh -->EDIT-LIST PICK
.jBASE.el.7
TOP
.P
TOP
001 2
BOTTOM
.EX
Record '.jBASE.el.7' exited from file '.'
List 'PICK' exited
```

One of the advantages of using **SQLSELECTL** instead of regular **{S}SELECT** is that in situations where you have a large table/file and you want to get a result set based on a value in another table/file, otherwise known as a *foreign table*.

e.g. a **DESCRIPTION** column.  

And if the *foreign table* is large you could also index the **DESCRIPTION** column (see [Indexes](../../indexes/README.md)).

Let's propose in the **JSQLDEMO** table above that **CATEGORY**, instead of being a *VARCHAR*, was an *INT* and keyed to another table/file called **CATEGORY**:

``` sql
jsh -->SQLSELECTL A.RECID FROM JSQLDEMO A, CATEGORY B WHERE B.DESCRIPTION = 'DATABASE' AND A.CATEGORY = B.ID
```

While you could achieve the same in [jQL](../../jql/README.md) using a translate function to the **CATEGORY** file it is not a simple task to have an index on the **DESCRIPTION** field as you would have to have triggers on both files and potentially perform an expensive index updated if a **DESCRIPTION** changed.

#### SQLDELETE

Example usage:

``` sql
jsh -->SQLDELETE JSQLDEMO WHERE RECID = '1'
Deleted 1 rows.
jsh -->SQLSELECT * FROM JSQLDEMO
RECID                BIRTHDAY   FIRSTNAME                      LASTNAME                       CATEGORY
-------------------- ---------- ------------------------------ ------------------------------ --------------------
                   2 1968-01-01 PICK                           SYSTEMS                        DATABASE

Selected 1 rows.
```

***CAUTION:***  
> Take care when using **SQLDELETE** that your *WHERE* clause does not inadvertently match more records than you intended.

### SQLDROPTABLE

Example usage:

``` sql
jsh -->SQLDROPTABLE JSQLDEMO
Table JSQLDEMO Deleted successfully.
```

### SQL Compliance

A common problem with using SQL with a jBASE database is existence of illegal characters in filenames and dictionaries (*tables* and *columns* from a SQL perspective).  

For example:

```INVOICE-HISTORY```  
or  
```INVOICE.HISTORY```

are both invalid.

To correct this problem without affecting the existing applications, jBASE provides a SQL Catalog file (see [SQLCATMAN](../../tools-and-utilities/sqlcatman/README.md)).

Once you have your SQL Catalog file/directory created you could then create an entry like:

``` shell
INVOICE_HISTORY
001 /dbms/ACCOUNTS/INVOICE-HISTORY
002 /dbms/ACCOUNTS/INVOICE-HISTORY]D
```

### SQL Column Names

Similar to file names being non-SQL compliant, dictionaries also need addressing as valid *column* names. There are two recommended ways of achieving this goal:

1. Create a separate SQL compliant dictionary file which would then be applied to attribute <2> of the SQL Catalog entry. Then populate with table defining dictionaries.
2. Use **jDP_Options** to control which dictionaries are visible to any SQL query.

In both cases it is recommended to make use of the [jBASE Extended Dictionary](../../files/extended-dictionary/README.md).

As an example, given the following dictionary:

``` shell
PAID.DATE
001 A
002 11
003 Date Paid
004
005
006
007 D2/
008
009 R
010 8
```

an extended dictionary version could be:

``` shell
PAID.DATE
001 A
002 11
003 Date Paid
004
005
006
007 D2/
008
009 R
010 8
011
...
030 JBASE_EDICT_START
031 123
032 12
033
034 PAID_DATE
035
036
037
038
039 1073741825
...
054 JBASE_EDICT_END
```

Note that the dictionary id is still **PAID.DATE** which is not a valid SQL column but attribute 34 has a valid column name - **PAID_DATE** - so from an SQL/ODBC perspective you would use **PAID_DATE**.

Example

``` sql
jsh -->SQLSELECT ORDER_NBR, PAID_AMOUNT FROM INVOICE_HISTORY WHERE PAID_DATE BETWEEN {d '2010-01-01'} AND {d '2010-12-31'}
```

See also [jDP_Options](../../files/extended-dictionary/#jdp-options).

<PageFooter />
