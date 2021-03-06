# Testing and Debugging

<PageHeader />

MV Dashboard provides several tools to aid in debugging dashboard widgets: debug mode, logging and a special debugging execution environment.

Common widget programming errors are:

- Terminating your widget subroutine with a STOP instead of RETURN.
- Failing to catalog your widget subroutine.
- Failing to open a file before reading data.
- Using "ELSE STOP" on an OPEN statement when proper Q-pointers have not been configured in the dashboard account.
- Calling a subroutine from your widget program that has not been cataloged in the dashboard account.
- Having an extra END statement in your widget subroutine.
- Allowing your widget subroutine to generate output to the screen.

## Using Widget Debug Mode

In normal usage, if dashboard controller program (MVDB.MAIN) detects that a widget has failed to execute properly, the widget is automatically placed into "debug mode" and removed from dashboard until it has been returned to "normal mode". An administrator can toggle the widget mode (normal or debug) by clicking the "i" icon on the widget control menu. When a widget is in "debug mode", instead of displaying normal content, debugging information about the widget is displayed. This includes the name of the widget subroutine, any runtime errors generated by the widget subroutine (if the MultiValue platform supports logging of runtime errors), and variables from WIDGET.USER.DATA.

## Using SUB.LOG.DEBUG.INFO to debug widgets

The SUB.LOG.DEBUG.INFO subroutine is provided to allow widget code to save important information in a log, for review after the widget has been run. Up to 100 lines of information may be saved in the widget log. To enable the logging feature, you must create a log file. SUB.LOG.DEBUG.INFO writes the widget log in the WDB.DEBUG file. The data section of this file is not normally created by the MV Dashboard installation, only the dictionary. Log in to the MVDB account and manually create the data section for WDB.DEBUG. Add CALL SUB.LOG.DEBUG.INFO to your widget code to save important information in the log. The SUB.LOG.DEBUG.INFO subroutine requires two arguments: widget name, and message. When the message is saved in the log, a timestamp is written before the message text. It is possible to send a dynamic array as part of the message; each attribute is saved on its own line in the log. To view the log, place the widget into debug mode, as described in the previous topic. The log contents are displayed after any runtime errors. To disable logging, delete the data section of the WDB.DEBUG file.

## Using MVDB.DEBUG to debug widgets

It is easier to identify and resolve problems by testing a new or modified widget program before running it in the dashboard environment. This can be done using the widget debugging program, MVDB.DEBUG.

The MVDB.DEBUG program requires the MVDB.DEBUG.INFO file. This file is not normally created by MV Dashboard installation. Log in to the MVDB account and manually create the MVDB.DEBUG.INFO file before using MVDB.DEBUG.

At TCL, type MVDB.DEBUG to start the testing process. This is a simple program that configures the widget runtime environment and calls your widget subroutine. It does not show you the results created by the widget program, the dashboard environment is the best place to see what your widget does. However, if your widget program encounters runtime warnings or errors, it can prematurely terminate the dashboard controller program.

The MVDB.DEBUG program provides an easy way for you to make sure your widget subroutine returns control back to the dashboard controller program and doesn???t produce any screen output. This program will also tell you the execute duration of your widget subroutine in milliseconds.

The example below shows that the widget subroutine SUB.LISTU ran in 217 milliseconds and did not produce any screen output:

```
Calling SUB.LISTU
Call completed. Duration: 217
```

The following example shows a widget subroutine that is generating a runtime-error which will impact the display of the dashboard in a web browser:

```
Calling SUB.TEST2
[B10] in program "SUB.TEST2", Line 22:
    Variable has not been assigned a value; zero used.
0
Call completed. Duration: 283
```

<PageFooter />
