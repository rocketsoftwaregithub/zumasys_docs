# jRCS Licensing  

<PageHeader />

## Note

>On jBASE versions 5.5.0 and above, a jRCS license is no longer required and both the server and the .NET client binaries are included in the jBASE install.

## Overview

When the jRCS Activation Program is run, it generates an installation identifier which has to be returned to Zumasys/jBASE International, via email, in order to obtain a license key. The license key is tied to the specific server using one of the following identifiers:

- Machine serial number on AIX
- MAC address on Linux
- Processor ID on Solaris
- Windows serial number on Win32

This licensing model ensures that a jRCS license will not operate on any other server.

Replacing a CPU board on a SPARC or changing the primary network card on a Linux box may result in the customer having to re-apply for a replacement license.

On start-up the licensed jRCS server will re-compute the hardware ID and use it to validate the key and to obtain the licensing information from it. Deleting the license file will cause the server to operate in “demo” mode.

## Demo Mode

jRCS in Demo Mode allows for a single connection to be made to the jRCS Server. This connection may be from any of the jRCS client types.

## License Generation and Installation

The installation identifier for a particular server is generated by means of the ‘jrcslicensetool’ utility, which should be run with the ‘-g’ option:

```
>jrcslicensetool -g
```

Details of the ‘jrcslicensetool’ functionality can be obtained by running the utility without any options:

```
>jrcslicensetool
```

Generates an installation identifier or installs a jRCS license key.

```
jjrcslicensetool [-i [key]] [-g] [-p]

Options:
  -i [key]      Installs a new license key.
                If a key is not specified, prompts for the key.
  -g            Generates an installation identifier for the current machine.
  -p            Prints license information, including installed and used license counts.
```

The Installation ID generated will be used by Zumasys/jBASE International in the generation of the license key. The license key is also generated using the number of users by connection type required, i.e. conventional, .NET and java, or a combination of the types, and may be generated with an end date to allow for the provision of evaluation keys. For example :

```
Platform: Microsoft Windows
License key: G5Y0Z-ZNJJ7-K0D0L-05U9E-LDR5L
Conventional licenses: 0
.NET client licenses: 5
Java client licenses: 0
Expiration date: Thursday, May 31, 2007
```

The license key should be installed on the specific system using the command:

```
>jrcslicensetool –i <installation key>
```

Once the key has been installed, jRCS will need to be restarted in order for the key to be recognised by the system.

The license key is stored in encrypted format in file jrcs.lic in the config subdirectory of JBCRELEASEDIR.

If a license key is not installed, or if one has expired, jRCS will revert to the [demo mode](#demo-mode), where the user can open only one connection at any given time, regardless of the type of client used.

jBASE connections used by jRCS are also subject to jBASE licensing.  

In jBASE 4.1, irrespective of the type of jRCS client, if an Enterprise license is obtained on its initial connection, then multiple jRCS sessions from that same IP address are allowed.

If, on initial connect, a Server license is obtained, further jRCS connections from this IP address will use one or more additional jRCS licenses, depending on the type of jBASE license obtained. In other words, if the port connected to is assigned a jBASE multi-session license, jRCS will also provide multi-session capability. If the port connected to obtains a jBASE server license, jRCS will only allow a single session for that license token.

[Back to Connectivity](./../README.md)

<PageFooter />