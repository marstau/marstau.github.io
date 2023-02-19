---
layout: post
title: android 国际化语言 locale缩写
category: 编程开发
tags: Android-Java
keywords: 
description: 
---


我们建好一个android 的项目后，默认的res下面 有layout、values、drawable等目录

这些都是程序默认的资源文件目录，如果要实现多语言版本的话，我们就要添加要实现语言的对应的资源文件。

首先我们点击添加Android Xml File按钮，会出现下面的界面：

![](/Resources/android_国际化语言_locale缩写_1.png)

输入文件名：string.xml，选中Values单选框，并把下面左列表中的Region添加到左边的列表里面，并在Region输入框里输入cn，如下图

![](/Resources/android_国际化语言_locale缩写_2.png)

这时，上面的消息提示：如果用Region的话，需要使用语言项，和Region一样，我们把Language也添加到右面的列表里面，填入zh，如下图

![](/Resources/android_国际化语言_locale缩写_3.png)

 

点击Finish按钮，资源文件就会建好了，目录：res\values-zh-rCN（其实上面一大堆操作，就是为生成这个目录）

![](/Resources/android_国际化语言_locale缩写_4.png)

默认生成的string.xml的代码：

    <?xml version="1.0" encoding="utf-8"?> <resources> <string name="hello">Hello World, Test!</string> <string name="app_name">Test-Multilingual</string> </resources>
修改刚刚生成的res\values-zh-rCN目录下的string.xml：

    <?xml version="1.0" encoding="utf-8"?> <resources> <string name="app_name">测试多语言</string> <string name="hello">你好 多语言测试</string> </resources>
运行结果：

en-us：英文

![](/Resources/android_国际化语言_locale缩写_5.png) ![](/Resources/android_国际化语言_locale缩写_6.png)

zh-cn：中国大陆

![](/Resources/android_国际化语言_locale缩写_7.png) ![](/Resources/android_国际化语言_locale缩写_8.png) ![](/Resources/android_国际化语言_locale缩写_9.png)

zh-tw：台湾

![](/Resources/android_国际化语言_locale缩写_10.png) ![](/Resources/android_国际化语言_locale缩写_11.png) ![](/Resources/android_国际化语言_locale缩写_12.png)

 

因为设置了region为CN，所以zh-tw的时候，没有找到res\values-zh-rTW的目录，加载了默认的res\values目录下的string.xml

 

这里只用了Values做例子，其余的Resource都可以，图片了，布局了等等

这里只是简单的介绍了一下多语言对应，剩下的大家自己深入研究吧！

 

Second:

 

 

1.  
 
    很大程度上，为什么我们能如此方便的实现国际化、分辨率匹配等？ 
 
    主要就是得益于 Android 中这种独特的资源管理方式。程序员的代码可以不直接和资源发生关系。Android 中，我们通常通过 R 文件提供的索引来间接的引用某一个资源。而如何维护资源索引和真正的资源之间的关系，这个活，却是 Android 系统来做的。 
 
    这里面就可以大作文章了不是么？ 
 
    我说过，最了解用户手机的，不是用户也不是程序员，而是操作系统，是 Android。它最了解用户当前使用的是什么语言，最了解用户当前手机的分辨率是多少，了解电量，了解内存情况...等等。 
 
    既然你自个的情况这么了解，为什么不自己把所有能完成的事情都做了？不麻烦程序员了好吧？好的，所以 Android 在这方面做得非常优秀。 
 
    基于这个角度，我们要转换的观念为：有可能，R 文件中的索引，并非是和资源一对一的。例如我们以前认为它就一定是对应了一张图片，对应了一个字符串，对应了一个布局文件。 
 
    而很可能，Android 其实会根据用户当前使用的环境对应几套方案：例如本文所讲的主题，从国际化角度，可能对应中文环境方案，英文环境方案？那么，这时候 R 文件对应的这个资源便不确定起来，当我们通过 R 文件调用一个图片资源显示在窗口上时，Android 操作系统会自动根据用户当前的环境，而选用最合适的图片（这个挑选过程却是透明的）。 
 
 
 
   程序员可以干预的是：英文环境到底对应哪套方案？中文环境对应到底哪套方案？ 
 
   OK。这就简单了。 
 
2. Android 中要实现国际化比较简单。 
 
   字符串国际化：只要在 res 文件夹下新建对应语言的 values 文件夹就好了， 
 
   如，英语环境下的，文件夹命名为：values-en 
 
   美国英文环境：values-en-rUS 
 
   中文环境为：values-zh 
 
   大陆地区中文环境： 
 
   在 eclipse 下新建 Android 项目时，会在 res 目录下自动创建一个默认语言环境的文件夹 : values 
 
   当某一个资源没有在语言环境的对应的资源集合中找到时，就会使用 values 下的资源。 
 
   若某一个语言环境没有在项目中定义语言环境，那么也会使用 values 下的资源。 
 
3. 图片国际化 
 
   同理。 
 
   在 res 下新建 drawable-zh 文件夹，存放中文环境下的图片 
   新建 drawable-en 作为英语环境下的图片 
    
   在 eclipse 下新建 Android 项目时，会在 res 目录下自动创建三个默认语言环境的文件夹： 
   drawable-hdpi 
 
   drawable-ldpi 
 
   drawable-mdpi 
 
   分别用于存放高、中。低分辨率的图片。Android 系统会根据手机的分辨率，而自动从不同的对应的某一个文件夹下去加载图片。 
 
   同样，它们也可以国际化，命名规则如： 
 
   drawable-zh-hdpi 
   drawable-en-ldpi 
   drawable-en-rUS-mdpi 
   使用，在 XML 中需要使用到图片的地方用表达式： @drawable/icon 
   代码中使用：R.drawable.icon。因为图片资源同样也会在 R 文件中生成一个索引
# Third:
## Android国际化资源 文件夹命名规范
android多国语言文件夹文件汇总如下：

中文（中国）：values-zh-rCN

中文（台湾）：values-zh-rTW

中文（香港）：values-zh-rHK

英语（美国）：values-en-rUS

英语（英国）：values-en-rGB

英文（澳大利亚）：values-en-rAU

英文（加拿大）：values-en-rCA

英文（爱尔兰）：values-en-rIE

英文（印度）：values-en-rIN

英文（新西兰）：values-en-rNZ

英文（新加坡）：values-en-rSG

英文（南非）：values-en-rZA

阿拉伯文（埃及）：values-ar-rEG

阿拉伯文（以色列）：values-ar-rIL

保加利亚文:  values-bg-rBG

加泰罗尼亚文：values-ca-rES

捷克文：values-cs-rCZ

丹麦文：values-da-rDK

德文（奥地利）：values-de-rAT

德文（瑞士）：values-de-rCH

德文（德国）：values-de-rDE

德文（列支敦士登）：values-de-rLI

希腊文：values-el-rGR

西班牙文（西班牙）：values-es-rES

西班牙文（美国）：values-es-rUS

芬兰文（芬兰）：values-fi-rFI

法文（比利时）：values-fr-rBE

法文（加拿大）：values-fr-rCA

法文（瑞士）：values-fr-rCH

法文（法国）：values-fr-rFR

希伯来文：values-iw-rIL

印地文：values-hi-rIN

克罗里亚文：values-hr-rHR

匈牙利文：values-hu-rHU

印度尼西亚文：values-in-rID

意大利文（瑞士）：values-it-rCH

意大利文（意大利）：values-it-rIT

日文：values-ja-rJP

韩文：values-ko-rKR

立陶宛文：valueslt-rLT

拉脱维亚文：values-lv-rLV

挪威博克马尔文：values-nb-rNO

荷兰文(比利时)：values-nl-BE

荷兰文（荷兰）：values-nl-rNL

波兰文：values-pl-rPL

葡萄牙文（巴西）：values-pt-rBR

葡萄牙文（葡萄牙）：values-pt-rPT

罗马尼亚文：values-ro-rRO

俄文：values-ru-rRU

斯洛伐克文：values-sk-rSK

斯洛文尼亚文：values-sl-rSI

塞尔维亚文：values-sr-rRS

瑞典文：values-sv-rSE

泰文：values-th-rTH

塔加洛语：values-tl-rPH

土耳其文：values--r-rTR

乌克兰文：values-uk-rUA

越南文：values-vi-rVN
# FORTH:

  Code  | Country Name
:-----: | ------------
AF	    | AFGHANISTAN
AX	    | ÅLAND ISLANDS
AL	    | ALBANIA
DZ	    | ALGERIA
AS	    | AMERICAN SAMOA
AD	    | ANDORRA
AO	    | ANGOLA
AI	    | ANGUILLA
AQ	    | ANTARCTICA
AG	    | ANTIGUA AND BARBUDA
AR	    | ARGENTINA
AM	    | ARMENIA
AW	    | ARUBA
AU	    | AUSTRALIA
AT	    | AUSTRIA
AZ	    | AZERBAIJAN
BS	    | BAHAMAS
BH	    | BAHRAIN
BD	    | BANGLADESH
BB	    | BARBADOS
BY	    | BELARUS
BE	    | BELGIUM
BZ	    | BELIZE
BJ	    | BENIN
BM	    | BERMUDA
BT	    | BHUTAN
BO	    | BOLIVIA, PLURINATIONAL STATE OF
BQ	    | BONAIRE, SINT EUSTATIUS AND SABA
BA	    | BOSNIA AND HERZEGOVINA
BW	    | BOTSWANA
BV	    | BOUVET ISLAND
BR	    | BRAZIL
IO	    | BRITISH INDIAN OCEAN TERRITORY
BN	    | BRUNEI DARUSSALAM
BG	    | BULGARIA
BF	    | BURKINA FASO
BI	    | BURUNDI
KH	    | CAMBODIA
CM	    | CAMEROON
CA	    | CANADA
CV	    | CAPE VERDE
KY	    | CAYMAN ISLANDS
CF	    | CENTRAL AFRICAN REPUBLIC
TD	    | CHAD
CL	    | CHILE
CN	    | CHINA
CX	    | CHRISTMAS ISLAND
CC	    | COCOS (KEELING) ISLANDS
CO	    | COLOMBIA
KM	    | COMOROS
CG	    | CONGO
CD	    | CONGO, THE DEMOCRATIC REPUBLIC OF THE
CK	    | COOK ISLANDS
CR	    | COSTA RICA
CI	    | CÔTE D'IVOIRE
HR	    | CROATIA
CU	    | CUBA
CW	    | CURAÇAO
CY	    | CYPRUS
CZ	    | CZECH REPUBLIC
DK	    | DENMARK
DJ	    | DJIBOUTI
DM	    | DOMINICA
DO	    | DOMINICAN REPUBLIC
EC	    | ECUADOR
EG	    | EGYPT
SV	    | EL SALVADOR
GQ	    | EQUATORIAL GUINEA
ER	    | ERITREA
EE	    | ESTONIA
ET	    | ETHIOPIA
FK	    | FALKLAND ISLANDS (MALVINAS)
FO	    | FAROE ISLANDS
FJ	    | FIJI
FI	    | FINLAND
FR	    | FRANCE
GF	    | FRENCH GUIANA
PF	    | FRENCH POLYNESIA
TF	    | FRENCH SOUTHERN TERRITORIES
GA	    | GABON
GM	    | GAMBIA
GE	    | GEORGIA
DE	    | GERMANY
GH	    | GHANA
GI	    | GIBRALTAR
GR	    | GREECE
GL	    | GREENLAND
GD	    | GRENADA
GP	    | GUADELOUPE
GU	    | GUAM
GT	    | GUATEMALA
GG	    | GUERNSEY
GN	    | GUINEA
GW	    | GUINEA-BISSAU
GY	    | GUYANA
HT	    | HAITI
HM	    | HEARD ISLAND AND MCDONALD ISLANDS
VA	    | HOLY SEE (VATICAN CITY STATE)
HN	    | HONDURAS
HK	    | HONG KONG
HU	    | HUNGARY
IS	    | ICELAND
IN	    | INDIA
ID	    | INDONESIA
IR	    | IRAN, ISLAMIC REPUBLIC OF
IQ	    | IRAQ
IE	    | IRELAND
IM	    | ISLE OF MAN
IL	    | ISRAEL
IT	    | ITALY
JM	    | JAMAICA
JP	    | JAPAN
JE	    | JERSEY
JO	    | JORDAN
KZ	    | KAZAKHSTAN
KE	    | KENYA
KI	    | KIRIBATI
KP	    | KOREA, DEMOCRATIC PEOPLE'S REPUBLIC OF
KR	    | KOREA, REPUBLIC OF
KW	    | KUWAIT
KG	    | KYRGYZSTAN
LA	    | LAO PEOPLE'S DEMOCRATIC REPUBLIC
LV	    | LATVIA
LB	    | LEBANON
LS	    | LESOTHO
LR	    | LIBERIA
LY	    | LIBYA
LI	    | LIECHTENSTEIN
LT	    | LITHUANIA
LU	    | LUXEMBOURG
MO	    | MACAO
MK	    | MACEDONIA, THE FORMER YUGOSLAV REPUBLIC OF
MG	    | MADAGASCAR
MW	    | MALAWI
MY	    | MALAYSIA
MV	    | MALDIVES
ML	    | MALI
MT	    | MALTA
MH	    | MARSHALL ISLANDS
MQ	    | MARTINIQUE
MR	    | MAURITANIA
MU	    | MAURITIUS
YT	    | MAYOTTE
MX	    | MEXICO
FM	    | MICRONESIA, FEDERATED STATES OF
MD	    | MOLDOVA, REPUBLIC OF
MC	    | MONACO
MN	    | MONGOLIA
ME	    | MONTENEGRO
MS	    | MONTSERRAT
MA	    | MOROCCO
MZ	    | MOZAMBIQUE
MM	    | MYANMAR
NA	    | NAMIBIA
NR	    | NAURU
NP	    | NEPAL
NL	    | NETHERLANDS
NC	    | NEW CALEDONIA
NZ	    | NEW ZEALAND
NI	    | NICARAGUA
NE	    | NIGER
NG	    | NIGERIA
NU	    | NIUE
NF	    | NORFOLK ISLAND
MP	    | NORTHERN MARIANA ISLANDS
NO	    | NORWAY
OM	    | OMAN
PK	    | PAKISTAN
PW	    | PALAU
PS	    | PALESTINIAN TERRITORY, OCCUPIED
PA	    | PANAMA
PG	    | PAPUA NEW GUINEA
PY	    | PARAGUAY
PE	    | PERU
PH	    | PHILIPPINES
PN	    | PITCAIRN
PL	    | POLAND
PT	    | PORTUGAL
PR	    | PUERTO RICO
QA	    | QATAR
RE	    | RÉUNION
RO	    | ROMANIA
RU	    | RUSSIAN FEDERATION
RW	    | RWANDA
BL	    | SAINT BARTHÉLEMY
SH	    | SAINT HELENA, ASCENSION AND TRISTAN DA CUNHA
KN	    | SAINT KITTS AND NEVIS
LC	    | SAINT LUCIA
MF	    | SAINT MARTIN (FRENCH PART)
PM	    | SAINT PIERRE AND MIQUELON
VC	    | SAINT VINCENT AND THE GRENADINES
WS	    | SAMOA
SM	    | SAN MARINO
ST	    | SAO TOME AND PRINCIPE
SA	    | SAUDI ARABIA
SN	    | SENEGAL
RS	    | SERBIA
SC	    | SEYCHELLES
SL	    | SIERRA LEONE
SG	    | SINGAPORE
SX	    | SINT MAARTEN (DUTCH PART)
SK	    | SLOVAKIA
SI	    | SLOVENIA
SB	    | SOLOMON ISLANDS
SO	    | SOMALIA
ZA	    | SOUTH AFRICA
GS	    | SOUTH GEORGIA AND THE SOUTH SANDWICH ISLANDS
SS	    | SOUTH SUDAN
ES	    | SPAIN
LK	    | SRI LANKA
SD	    | SUDAN
SR	    | SURINAME
SJ	    | SVALBARD AND JAN MAYEN
SZ	    | SWAZILAND
SE	    | SWEDEN
CH	    | SWITZERLAND
SY	    | SYRIAN ARAB REPUBLIC
TW	    | TAIWAN, PROVINCE OF CHINA
TJ	    | TAJIKISTAN
TZ	    | TANZANIA, UNITED REPUBLIC OF
TH	    | THAILAND
TL	    | TIMOR-LESTE
TG	    | TOGO
TK	    | TOKELAU
TO	    | TONGA
TT	    | TRINIDAD AND TOBAGO
TN	    | TUNISIA
TR	    | TURKEY
TM	    | TURKMENISTAN
TC	    | TURKS AND CAICOS ISLANDS
TV	    | TUVALU
UG	    | UGANDA
UA	    | UKRAINE
AE	    | UNITED ARAB EMIRATES
GB	    | UNITED KINGDOM
US	    | UNITED STATES
UM	    | UNITED STATES MINOR OUTLYING ISLANDS
UY	    | URUGUAY
UZ	    | UZBEKISTAN
VU	    | VANUATU
VE	    | VENEZUELA, BOLIVARIAN REPUBLIC OF
VN	    | VIET NAM
VG	    | VIRGIN ISLANDS, BRITISH
VI	    | VIRGIN ISLANDS, U.S.
WF	    | WALLIS AND FUTUNA
EH	    | WESTERN SAHARA
YE	    | YEMEN
ZM	    | ZAMBIA
ZW	    | ZIMBABWE

## Reference
* <http://www.cnblogs.com/wuyunan/archive/2009/09/16/1567960.html>
* <http://xiaobingandxiaoer.iteye.com/blog/1218411>
* <http://hi.baidu.com/linux_boy/item/4bf651006dc32e8d3d42e26a>
* <http://www.iso.org/iso/prods-services/iso3166ma/02iso-3166-code-lists/country_names_and_code_elements>
* <http://en.wikipedia.org/wiki/ISO_639>
* [International Codes](/files/android_locales.xls)





