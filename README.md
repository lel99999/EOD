# EOD
***
Monolithic EOD for RHEL7.x

##### Fixes for RHEL 7 Issues
Timeout issue with applications:<br/>
- Edit /etc/ssh/sshd_config<br/>

1) ClientAliveCountMax
             Sets the number of client alive messages (see below) which may be sent without sshd(8) receiving any messages back from the client. If this threshold is reached while client alive messages are being sent, sshd will disconnect the client, terminating the session. It is important to note that the use of client alive messages is very different from TCPKeepAlive (below). The client alive messages are sent through the encrypted channel and therefore will not be spoofable. The TCP keepalive option enabled by TCPKeepAlive is spoofable.  The client alive mechanism is valuable when the client or server depend on knowing when a connection has become inactive. The default value is 3. If ClientAliveInterval (see below) is set to 15, and ClientAliveCountMax is left at the default, unresponsive SSH clients will be disconnected after approximately 45 seconds. This option applies to protocol version 2 only.<br/>

2) ClientAliveInterval
             Sets a timeout interval in seconds after which if no data has been received from the client, sshd(8) will send a message through the encrypted channel to request a response from the client. The default is 0, indicating that these messages will not be sent to the client. This option applies to protocol version 2 only.<br/>

3) TESTING: add ServerAlive Interval <time_value> to /etc/ssh/sshd_config to ping server for <time_value> interval, to keep connection alive<br/>
