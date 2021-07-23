### Below is code for email module that was pulled for personal security reasons.
### Runressults and reasoning follow after code.

## Below is run result from email Module. This worked with my real email server inserted.
## Pulled from main program for security reasons. Below demonstrates that module attempts
## send email but connecttion is rejected due to no login provided.

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

 * Super-optimized for small spaces - read how we shrank the memory
   footprint of MicroK8s to make it the smallest full K8s around.

   https://ubuntu.com/blog/microk8s-memory-optimisation

 * Canonical Livepatch is available for installation.
   - Reduce system reboots and improve kernel security. Activate at:
     https://ubuntu.com/livepatch
 *
 * Welcome to the Codio Terminal!
 *
 * https://docs.codio.com/project/ide/boxes/#overview
 *
 * Your Codio Box domain is: right-cuba.codio.io
 *
Last login: Thu Jul 22 20:18:53 2021 from 192.168.10.156
codio@right-cuba:~/workspace$ python3 email
Traceback (most recent call last):
  File "email", line 17, in <module>
    s = smtplib.SMTP('localhost')
  File "/usr/lib/python3.6/smtplib.py", line 251, in __init__
    (code, msg) = self.connect(host, port)
  File "/usr/lib/python3.6/smtplib.py", line 336, in connect
    self.sock = self._get_socket(host, port, self.timeout)
  File "/usr/lib/python3.6/smtplib.py", line 307, in _get_socket
    self.source_address)
  File "/usr/lib/python3.6/socket.py", line 724, in create_connection
    raise err
  File "/usr/lib/python3.6/socket.py", line 713, in create_connection
    sock.connect(sa)
ConnectionRefusedError: [Errno 111] Connection refused
codio@right-cuba:~/workspace$ 