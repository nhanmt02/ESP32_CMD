1. Restart ESP8266 
AT+RST$0D$0A
>>>>>>>>> If connected wifi
AT+RST{0D}{0A}{0D}{0A}OK{0D}{0A}{0D}{0A}ready{0D}{0A}WIFI CONNECTED{0D}{0A}WIFI GOT IP{0D}{0A}
>>>>>>>>> If not connected wifi
AT+RST{0D}{0A}AT+RST{0D}{0A}{0D}{0A}OK{0D}{0A}{0D}{0A}ready{0D}{0A}

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
2.View AP connected
AT+CWJAP?$0D$0A
>>>>>>>>>
AT+CWJAP?
+CWJAP:"SHCVN02","48:f8:b3:2e:f1:76",11,-59

3.Set Station mode:
AT+CWMODE=1$0D$0A
>>>>>>>>>
AT+CWMODE=1

OK
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
4.Question mode setting:
AT+CWMODE?$0D$0A
>>>>>>>>>
AT+CWMODE?
+CWMODE:1

OK
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
5.Truy van cac mang wifi co the ket noi
AT+CWLAP$0D$0A
>>>>>>>>>
AT+CWLAP
+CWLAP:(4,"Gontek2.4G",-57,"10:62:eb:3c:f1:72",1)
+CWLAP:(3,"SHCVN02",-61,"48:f8:b3:2e:f1:76",1)
+CWLAP:(3,"CTNP",-67,"b0:b8:67:07:3f:a0",11)
+CWLAP:(3,"CTNP2",-68,"b0:b8:67:07:3f:a1",11)
+CWLAP:(3,"GKV-IT",-69,"50:c7:bf:91:3e:de",5)
+CWLAP:(3,"GKV-IT-GUEST",-69,"54:c7:bf:91:3e:de",5)
+CWLAP:(4,"ADMS",-70,"30:b5:c2:4e:a2:4a",8)
+CWLAP:(3,"Telenor 4G-9669",-72,"78:62:56:ef:96:69",5)
+CWLAP:(4,"GKV_TECH",-77,"18:d6:c7:22:bf:a0",7)
+CWLAP:(4,"ASVSoftware",-81,"c4:e9:84:f3:c1:c7",13)
+CWLAP:(4,"HCM2",-85,"02:67:1c:40:43:9b",6)
+CWLAP:(4,"Ho Chi Minh",-86,"bc:67:1c:40:43:9a",6)

OK
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
6.Ket noi vao mang wifi
AT+CWJAP="SHCVN02","khongduoc"$0D$0A
>>>>>>>>>
AT+CWJAP="SHCVN02","khongduoc"
WIFI CONNECTED
WIFI GOT IP

OK
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
7.Xem dia chi module
AT+CIFSR$0D$0A
>>>>>>>>>
AT+CIFSR
+CIFSR:STAIP,"192.168.0.123"
+CIFSR:STAMAC,"a4:cf:12:24:3b:18"

OK
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
8.Set time
AT+CIPSNTPCFG=1,1,"sg.pool.ntp.org"$0D$0A
>>>>>>>>>
AT+CIPSNTPCFG=1,1,"sg.pool.ntp.org"

OK
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
9. Question time
AT+CIPSNTPTIME?$0D$0A
>>>>>>>>>
AT+CIPSNTPTIME?
+CIPSNTPTIME:Thu Aug 22 03:08:04 2019

OK
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
AT+CIPSSLCCONF=3,0,0$0D$0A
AT+CIPSSLCCONF=3,0,0

OK
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
AT+CIPSTART="SSL","a2oss9xummq06l-ats.iot.ap-southeast-1.amazonaws.com",8443$0D$0A
>>>>>>>>>
AT+CIPSTART="SSL","a2oss9xummq06l-ats.iot.ap-southeast-1.amazonaws.com",8443
CONNECT

OK

AT+CIPSTART="TCP","52.219.40.235",80$0D$0A
AT+CIPSEND=86$0D$0A
GET /helloWorld.txt HTTP/1.1$0D$0A
Host: imic-backet-s3.s3-ap-southeast-1.amazonaws.com$0D$0A$0D$0A
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
202 is length of POST
AT+CIPSEND=202$0D$0A
>>>>>>>>>
AT+CIPSEND=202

OK

>
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
*Run commmand POST after character '>', 52 length of json
POST /things/blinky/shadow HTTP/1.1$0D$0AHost: a2oss9xummq06l-ats.iot.ap-southeast-1.amazonaws.com$0D$0AContent-Type: application/json$0D$0AContent-Length: 52$0D$0A$0D$0A{"state":{"desired":{"prop1":"13"},"reported":{}}}$0D$0A
>>>>>>>>>
Recv 202 bytes

SEND OK

+IPD,189:HTTP/1.1 200 OK
content-type: application/json
content-length: 157
date: Thu, 22 Aug 2019 14:25:58 GMT
x-amzn-RequestId: 1aa22ab4-8e27-ddfb-c48d-113d330350e9
connection: keep-alive


+IPD,157:{"state":{"desired":{"prop1":"12"},"reported":{}},"metadata":{"desired":{"prop1":{"timestamp":1566483958}},"reported":{}},"version":5,"timestamp":1566483958}
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
AT+CIPSTART="SSL","a2oss9xummq06l-ats.iot.ap-southeast-1.amazonaws.com",8443$0D$0A
>>>>>>>>>
AT+CIPSTART="SSL","a2oss9xummq06l-ats.iot.ap-southeast-1.amazonaws.com",8443
CONNECT

OK
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Note: on visual code start count is 1. Therefor -1.$0D$0A is 2 character
AT+CIPSEND=97$0D$0A
>>>>>>>>>
AT+CIPSEND=97

OK

>
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
*Run commmand POST after character '>':
GET /things/blinky/shadow HTTP/1.1$0D$0AHost: a2oss9xummq06l-ats.iot.ap-southeast-1.amazonaws.com$0D$0A$0D$0A

>
Recv 97 bytes

SEND OK

+IPD,189:HTTP/1.1 200 OK
content-type: application/json
content-length: 152
date: Fri, 23 Aug 2019 08:38:41 GMT
x-amzn-RequestId: 99ec36e7-2710-1e4f-ef0b-f8279e96bcbd
connection: keep-alive


+IPD,152:{"state":{"desired":{"prop1":"12"},"delta":{"prop1":"12"}},"metadata":{"desired":{"prop1":{"timestamp":1566483958}}},"version":5,"timestamp":1566549521}

>
Recv 97 bytes

SEND OK

+IPD,189:HTTP/1.1 200 OK
content-type: application/json
content-length: 315
date: Thu, 05 Sep 2019 11:02:46 GMT
x-amzn-RequestId: 20e8388e-ff58-5669-1b27-1496175bf509
connection: keep-alive


+IPD,315:{"state":{"desired":{"prop1":"13","led1":"0","led2":"1","led3":"1"},"delta":{"prop1":"13","led1":"0","led2":"1","led3":"1"}},"metadata":{"desired":{"prop1":{"timestamp":1567680744},"led1":{"timestamp":1567680744},"led2":{"timestamp":1567680744},"led3":{"timestamp":1567680744}}},"version":11,"timestamp":1567681366}

>
Recv 97 bytes

SEND OK

+IPD,241:HTTP/1.1 404 Not Found
content-type: application/json
content-length: 72
date: Wed, 04 Sep 2019 03:58:24 GMT
x-amzn-RequestId: 47e0eda8-5cad-1dd8-0a56-28ab96535910
connection: keep-alive
x-amzn-ErrorType: ResourceNotFoundException:


+IPD,72:{"message":"Not Found","traceId":"47e0eda8-5cad-1dd8-0a56-28ab96535910"}CLOSED

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
AT+UART_DEF=9600,8,1,0,0$0D$0A
>>>AT+UART_DEF=9600,8,1,0,0

OK
Note: Step connect to aws:
1.Config WIFI
AT+CWJAP="SHCVN02","khongduoc"$0D$0A
2.Config SSL
AT+CIPSSLCCONF=3,0,0$0D$0A
3.Config mode
AT+CWMODE=1$0D$0A
4.Config time server
AT+CIPSNTPCFG=1,1,"sg.pool.ntp.org"$0D$0A