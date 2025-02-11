---
UID: NF:winsock2.WSANtohl
title: WSANtohl function (winsock2.h)
description: The WSANtohl function converts a u_long from network byte order to host byte order.
old-location: winsock\wsantohl_2.htm
tech.root: WinSock
ms.assetid: 7e3b42eb-3b93-459f-828a-c19e277882c7
ms.date: 12/05/2018
ms.keywords: WSANtohl, WSANtohl function [Winsock], _win32_wsantohl_2, winsock.wsantohl_2, winsock2/WSANtohl
f1_keywords:
- winsock2/WSANtohl
dev_langs:
- c++
req.header: winsock2.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: Windows 8.1, Windows Vista [desktop apps \| UWP apps]
req.target-min-winversvr: Windows Server 2003 [desktop apps \| UWP apps]
req.kmdf-ver: 
req.umdf-ver: 
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Ws2_32.lib
req.dll: Ws2_32.dll
req.irql: 
topic_type:
- APIRef
- kbSyntax
api_type:
- DllExport
api_location:
- Ws2_32.dll
api_name:
- WSANtohl
targetos: Windows
req.typenames: 
req.redist: 
ms.custom: 19H1
---

# WSANtohl function


## -description


The 
<b>WSANtohl</b> function converts a <b>u_long</b> from network byte order to host byte order.


## -parameters




### -param s [in]

A descriptor identifying a socket.


### -param netlong [in]

A 32-bit number in network byte order.


### -param lphostlong [out]

A pointer to a 32-bit number to receive the number in host byte order.


## -returns



If no error occurs, 
<b>WSANtohl</b> returns zero. Otherwise, a value of SOCKET_ERROR is returned, and a specific error code can be retrieved by calling 
<a href="https://docs.microsoft.com/windows/desktop/api/winsock/nf-winsock-wsagetlasterror">WSAGetLastError</a>.

<table>
<tr>
<th>Error code</th>
<th>Meaning</th>
</tr>
<tr>
<td width="40%">
<dl>
<dt><b><a href="https://docs.microsoft.com/windows/desktop/WinSock/windows-sockets-error-codes-2">WSANOTINITIALISED</a></b></dt>
</dl>
</td>
<td width="60%">
A successful 
<a href="https://docs.microsoft.com/windows/desktop/api/winsock/nf-winsock-wsastartup">WSAStartup</a> call must occur before using this function.

</td>
</tr>
<tr>
<td width="40%">
<dl>
<dt><b><a href="https://docs.microsoft.com/windows/desktop/WinSock/windows-sockets-error-codes-2">WSAENETDOWN</a></b></dt>
</dl>
</td>
<td width="60%">
The network subsystem has failed.

</td>
</tr>
<tr>
<td width="40%">
<dl>
<dt><b><a href="https://docs.microsoft.com/windows/desktop/WinSock/windows-sockets-error-codes-2">WSAENOTSOCK</a></b></dt>
</dl>
</td>
<td width="60%">
The descriptor is not a socket.

</td>
</tr>
<tr>
<td width="40%">
<dl>
<dt><b><a href="https://docs.microsoft.com/windows/desktop/WinSock/windows-sockets-error-codes-2">WSAEFAULT</a></b></dt>
</dl>
</td>
<td width="60%">
The <i>lphostlong</i> parameter is <b>NULL</b> or the address pointed to is not completely contained in a valid part of the user address space.

</td>
</tr>
</table>
 




## -remarks



The 
<b>WSANtohl</b> function takes a 32-bit number in network byte order and returns a 32-bit number in host byte order in the 32-bit number pointed to by the <i>lphostlong</i> parameter. The socket passed in the <i>s</i> parameter is used to determine the network byte order required based on the Winsock catalog protocol entry associated with the socket. This feature supports Winsock providers that use different network byte orders. 

If the socket is for the AF_INET or AF_INET6 address family, the 
<b>WSANtohl</b> function can be used to convert an IPv4 address in network byte order to the IPv4 address in host byte order. This function does not do any checking to determine if the <i>netlong</i> parameter is a valid IPv4 address.

The 
<b>WSANtohl</b> function requires that the Winsock DLL has previously been loaded with a successful 
call to the <a href="https://docs.microsoft.com/windows/desktop/api/winsock/nf-winsock-wsastartup">WSAStartup</a> function. For use with the AF_INET or AF_INET6 family, the <a href="https://docs.microsoft.com/windows/desktop/api/winsock/nf-winsock-ntohl">ntohl</a> function does not require that the Winsock DLL be loaded. 

<b>Windows Phone 8:</b> This function is supported for Windows Phone Store apps on Windows Phone 8 and later.

<b>Windows 8.1</b> and <b>Windows Server 2012 R2</b>: This function is supported for Windows Store apps on Windows 8.1, Windows Server 2012 R2, and later.




## -see-also




<a href="https://docs.microsoft.com/windows/desktop/api/ws2tcpip/nf-ws2tcpip-inetntopw">InetNtop</a>



<a href="https://docs.microsoft.com/windows/desktop/api/winsock2/nf-winsock2-wsahtonl">WSAHtonl</a>



<a href="https://docs.microsoft.com/windows/desktop/api/winsock2/nf-winsock2-wsahtons">WSAHtons</a>



<a href="https://docs.microsoft.com/windows/desktop/api/winsock2/nf-winsock2-wsantohs">WSANtohs</a>



<a href="https://docs.microsoft.com/windows/desktop/WinSock/winsock-functions">Winsock Functions</a>



<a href="https://docs.microsoft.com/windows/desktop/WinSock/winsock-reference">Winsock Reference</a>



<a href="https://docs.microsoft.com/windows/desktop/api/winsock/nf-winsock-htonl">htonl</a>



<a href="https://docs.microsoft.com/windows/desktop/api/winsock/nf-winsock-htons">htons</a>



<a href="https://docs.microsoft.com/windows/desktop/api/wsipv6ok/nf-wsipv6ok-inet_addr">inet_addr</a>



<a href="https://docs.microsoft.com/windows/desktop/api/wsipv6ok/nf-wsipv6ok-inet_ntoa">inet_ntoa</a>



<a href="https://docs.microsoft.com/windows/desktop/api/winsock/nf-winsock-ntohl">ntohl</a>



<a href="https://docs.microsoft.com/windows/desktop/api/winsock/nf-winsock-ntohs">ntohs</a>
 

 

