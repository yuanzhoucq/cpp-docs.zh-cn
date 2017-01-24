---
title: "区域设置类别 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "LC_MAX"
  - "LC_MIN"
  - "LC_MONETARY"
  - "LC_TIME"
  - "LC_NUMERIC"
  - "LC_COLLATE"
  - "LC_CTYPE"
  - "LC_ALL"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "LC_ALL 常量"
  - "LC_COLLATE 常量"
  - "LC_CTYPE 常量"
  - "LC_MAX 常量"
  - "LC_MIN 常量"
  - "LC_MONETARY 常量"
  - "LC_NUMERIC 常量"
  - "LC_TIME 常量"
  - "区域设置常量"
ms.assetid: 868f1493-fe5d-4722-acab-bfcd374a063a
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 区域设置类别
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 语法  
  
```  
  
#include <locale.h>  
  
```  
  
## 备注  
 区域设置类别是本地化程序使用额的清单常量指，用于指定哪部分的程序的区域设置信息将被使用  区域设置是指位置（或国家\/地区）程序的某些方面可以自定义。  一些与区域设置相关的类别包括日期的格式或者货币值的显示格式。  
  
|区域设置类别|部分程序受到影响|  
|------------|--------------|  
|`LC_ALL`|所有区域设置特定的行为 \(所有类别\)|  
|`LC_COLLATE`|`strcoll` 和 `strxfrm` 函数的行为|  
|`LC_CTYPE`|字符处理函数 \( 除了**判断字符是否为数字**、`isxdigit`、`mbstowcs`和 `mbtowc`，不受影响\) 的行为。|  
|`LC_MAX`|与 `LC_TIME` 相同。|  
|`LC_MIN`|和 `LC_ALL` 相同。|  
|`LC_MONETARY`|由`localeconv`函数返回的货币格式信息。|  
|`LC_NUMERIC`|用于格式化输出程序\(例如 `printf`\)，数据转换程序的十进制点字符，和由函数 `localeconv`返回的非货币的格式化信息。|  
|`LC_TIME`|函数`strftime` 的行为|  
  
 有关示例，请参见 [setlocale、\_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)。  
  
## 请参阅  
 [localeconv](../c-runtime-library/reference/localeconv.md)   
 [setlocale、\_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [strcoll 函数](../c-runtime-library/strcoll-functions.md)   
 [strftime、wcsftime、\_strftime\_l、\_wcsftime\_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)   
 [strxfrm、wcsxfrm、\_strxfrm\_l、\_wcsxfrm\_l](../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)   
 [全局常量](../c-runtime-library/global-constants.md)