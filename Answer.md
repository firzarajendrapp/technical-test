# Question 1 :

$ vim house-keeping.sh

```
#!/bin/bash
find /var/log/nginx/*.log -mtime +7 -type f -exec rm -rf {} \; 
```
$ chmod +x house-keeping.sh

$ crontab -e

```
@weekly ~/house-keeping.sh
```
----

$ vim /etc/logrotate.d/nginx
```
/var/log/nginx/*.log {
    size 100M
    weekly
    compress
    rotate 4
    missingok
    create 0664 root root
}
```

===============================
# Question 2

https://github.com/firzarajendrapp/Task2-Devops/tree/master

=================================

# Question 3

## INPUT
2017-08-01 01:11:33,999|9999{"channelSessionId":"10100000000123456789","remark":"BillPayment","OriginatorConversationID":"ASSTR0123123456456789789","Msisdn":"6281xxxxxxxxx","CommandId":"PreValConfirmation"}

## PATTERN
%{DATESTAMP}\|%{INT:ServiceID}\{"channelSessionId":"%{INT:ChannelID}\","remark":"%{WORD:Remark}\","OriginatorConversationID":"%{WORD:OriginatorConversationID}\","Msisdn":"%{WORD:MSISDN}\","CommandId":"%{WORD:CommandID}

===================================

# Question 4

## INPUT
{"uuid":"59bd2e00-465b-11ea-987a-b74a8d671e08","rt":999,"port":"65530","ip":"123.123.123.123","appli":"abcd","versi":"v99","path":"/xx/yy/xyz/aha"}

## PATTERN
%{UUID:uuid}\","rt":%{INT:rt}\,"port":"%{INT:port}\","ip":"%{IPV4:ip}\","appli":"%{WORD:appli}\","versi":"%{WORD:versi}\","path":"%{PATH:path}

