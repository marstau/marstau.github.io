---
layout: post
title: loadrunner
category: 书籍与软件工具
tags: software／tool
keywords: 
description: 
---

\
 Action()\
 {\
  web\_custom\_request("request", //随便写个名字\
     "Method=POST",                         //请求的方法\
    
"URL=http://115.29.176.151:8123/\_wack-android-server/user/order\_form",       
//请求地址\
     "RecContentType=application/json",   
//指定相应头的Content-Type，这里是JSON\
     "EncType=application/json",              
//指定请求头的Content-Type，这里也是JSON\
     "Mode=HTML",\
     RAW\_BODY\_START,                      //请求BODY开始的标识符\
    
"{\\"MOrdersForm\\":\\"{\\"address\\":\\"4412\\",\\"bookTime\\":1384269177072,\\"items\\":[{\\"commentLevel\\":0,\\"commentTime\\":1384269177072,\\"id\\":0,\\"name\\":\\"土泥鳅\\",\\"totalNum\\":1,\\"unitPrice\\":45.00}],\\"phoneNumber\\":15658568898,\\"remark\\":\\"无\\",\\"sendingTime\\":0,\\"storeID\\":677311,\\"userID\\":653339}\\"}", 
//BODY的内容\
     257,                                    //上面一行BODY内容的长度\
     RAW\_BODY\_END,                  //请求BODY结束的标识符\
     LAST);\
 return 0;\
 }





