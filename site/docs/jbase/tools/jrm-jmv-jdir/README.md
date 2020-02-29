# jrm jmv jdir

**Created At:** 8/30/2018 2:13:28 PM  
**Updated At:** 10/25/2018 8:55:23 AM  
**Original Doc:** [jrm-jmv-jdir](https://docs.jbase.com/48399-tools/jrm-jmv-jdir)  
**Original ID:** 336923  
**Internal:** No  

## Description

Many commands are built-in to the Windows command shell and so can be executed like other executables.  

The following commands have been provided to use in either [jsh](./../../jshell) or cmd shell.  

As they are executables to use in place of **cmd.exe** functionality, the commands are provided **only on Windows**.

| Command | Description |
| --- | --- |
| jrm file | jrm -r directory | remove file or directory, recursively |
| jmv oldfile newfile | move oldfile to newfile |
| jdir {directory|file} | list directory |

## Note

> If [Transaction Journaling](../../transactions/README.md) is active, the actions performed by jrm and jmv are **not** logged.

[Back to Tools](./../README.md)