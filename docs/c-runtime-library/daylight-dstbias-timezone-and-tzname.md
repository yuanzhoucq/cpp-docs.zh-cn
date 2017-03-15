---
title: "_daylight、_dstbias、_timezone 和 _tzname | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "tzname"
  - "_timezone"
  - "timezone"
  - "_daylight"
  - "_tzname"
  - "daylight"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "时区"
  - "时间调整"
  - "时区变量"
  - "_tzname 函数"
  - "_daylight 函数"
  - "_timezone 函数"
  - "daylight 函数"
  - "本地时间调整"
  - "timezone 函数"
  - "tzname 函数"
  - "时区变量"
ms.assetid: d06c7292-6b99-4aba-b284-16a96570c856
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# _daylight、_dstbias、_timezone 和 _tzname
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`_daylight`、`_dstbias`、`_timezone`和 `_tzname` 在某些时间和日期例程使本地时间调整。  这些全局变量因有更安全函数版本而被废弃，这被使用来替代全局变量。  
  
|全局变量|等效功能|  
|----------|----------|  
|`_daylight`|[\_get\_daylight](../c-runtime-library/reference/get-daylight.md)|  
|`_dstbias`|[\_get\_dstbias](../c-runtime-library/reference/get-dstbias.md)|  
|`_timezone`|[\_get\_timezone](../c-runtime-library/reference/get-timezone.md)|  
|`_tzname`|[\_get\_tzname](../c-runtime-library/reference/get-tzname.md)|  
  
 在 Time.h 按如下方式声明。  
  
## 语法  
  
```  
extern int _daylight;   
extern int _dstbias;   
extern long _timezone;   
extern char *_tzname[2];  
```  
  
## 备注  
 在对 `_ftime`的调用，`localtime`或 `_tzset`值，`_daylight`、`_dstbias`、`_timezone`和 `_tzname` 环境变量 `TZ` 的值确定。  如果不显式设置 `TZ`值，`_tzname[0]` 和 `_tzname[1]` 分别包含 PST“”和“”PDT 默认设置。时间操作函数 \(和\)、[\_tzset](../c-runtime-library/reference/tzset.md)[\_ftime](../c-runtime-library/reference/ftime-ftime32-ftime64.md)[localtime](../c-runtime-library/reference/localtime-localtime32-localtime64.md)尝试通过查询的操作系统默认值设置 `_daylight`、`_dstbias` 和 `_timezone` 的值每个变量。  时区全局变量的值如下表所示。  
  
|变量|值|  
|--------|-------|  
|`_daylight`|如果非零，夏时制 \(DST\) 区域 `TZ` 中指定或从操作系统中确定；否则为0。  默认值为 1。|  
|`_dstbias`|夏时制偏移量|  
|`_timezone`|协调差异。在中的泛时间以及本地时间之间的秒的格式。  默认值为 28,800。|  
|`_tzname[0]`|从 `TZ` 派生该环境变量的名称。  默认值为“PST”。|  
|`_tzname[1]`|从 `TZ` 环境变量派生的DST区域名称。  默认值为“PDT”\(太平洋夏时制时间\)。|  
  
## 请参阅  
 [全局变量](../c-runtime-library/global-variables.md)   
 [\_get\_daylight](../c-runtime-library/reference/get-daylight.md)   
 [\_get\_dstbias](../c-runtime-library/reference/get-dstbias.md)   
 [\_get\_timezone](../c-runtime-library/reference/get-timezone.md)   
 [\_get\_tzname](../c-runtime-library/reference/get-tzname.md)