# fluentd_config
This repository includes the fluentd configuration file to be used to parse logs sent by multiple devices including cisoc ASA


### How to use
- Download the contents of this repository on your /etc/fluent directory
- You will need to install three fluentd/tdagent plugins
    - fluent-plugin-elasticsearch 
    - fluent-plugin-grok-parser 
    - fluent-plugin-rewrite-tag-filter 


**Note:**
make sure to backup fluent.conf file if you already have one in your directory otherwise it might be overwritten.

- Restart your fluentd 
- The configuraiton file has been set so that fluentd will read from the data stored inside /var/log/syslog,<br> so to test the code, go to the (tests) directory, then copy and paste the contents of the test_echo inside your shell terminal. this will populate your syslog log file with some ASA logs to be parsed by fluentd.

echo \"Jul 31 16:29:08 ASA-TEST-1 : %ASA-4-106023: Deny tcp src Some-int_2:192.168.1.1/54246(ABCD-ms01) dst ABCD:172.16.1.1/443 by access-group \"Some-int_2_access_in\" [0xcb01c404, 0x0]\" >> /var/log/syslog


### working version
The fluent configuration file was tested on 
- Kibana Version 	4.6.1
- ElasticSearch Version 2.4.1
- fluentd Version 1.2.3

### Troubleshooting
issue the command ```$ fluentd -v``` on your terminal 
to troubleshoot if something didn't work as expected.

### Warning
The file was tested under a small testing environment,
without heavy logging load and it is still under deveopment.
some perfomrance issues has to be considered before applying 
this configuraiton to your fluentd configuriation.
Take your backup and use at your own risk.

### License
fluentd_config is free file: you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or (at your option) any later version.

fluentd_config is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details.
