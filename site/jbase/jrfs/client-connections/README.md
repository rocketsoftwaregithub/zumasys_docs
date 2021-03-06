# Client Connections

<PageHeader />

## DescriptionÂ  

Client connections can be configured to map client connect request components to alternative values by using the client mapping feature of the jConnect library. The client mapping feature requires that certain components from the client connect request match an entry in the jnet\_map file. If a valid entry is found then some of the components can be mapped to alternatives before executing the connect request proper. The components that can be mapped are the hostname, the servername and the remoteusername. This feature enables administrators to configure an alternative remoteusername for specific clients or rename a remote system without having to change all the references in the local SYSTEM file.

### Note

Client mapping is invoked before the resolution of the network address and service, therefore the mapped names will be used in place of original to obtain the connection parameters.

Back to [Remote Files](./../jbase-remote-file-service/README.md)

<PageFooter />
