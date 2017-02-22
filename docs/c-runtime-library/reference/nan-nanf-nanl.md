---
title: "nan、nanf、nanl | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "nanf"
  - "nan"
  - "nanl"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-math-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "nan"
  - "nanl"
  - "nanf"
dev_langs: 
  - "C++"
ms.assetid: 790e9158-80ab-43e0-8f5a-096198553fd9
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# nan、nanf、nanl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

返回 quiet NaN 值。  
  
## 语法  
  
```  
double nan(    const char* input  ); float nanf(    const char* input  ); long double nanl(    const char* input  );  
```  
  
#### 参数  
 `input`  
 字符串值。  
  
## 返回值  
 `nan` 函数将返回 quiet NaN 值。  
  
## 备注  
 `nan` 函数将返回与 quiet（非 signalling）NaN 相应的浮点值。  将忽略 `input` 值。  有关如何表示用于输出的 NaN 的信息，请参阅 [printf、\_printf\_l、wprintf、\_wprintf\_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)。  
  
## 要求  
  
|函数|C 标头|C\+\+ 标头|  
|--------|----------|--------------|  
|`nan`, `nanf`, `nanl`|\<math.h\>|\<cmath\>|  
  
## .NET Framework 等效项  
 [System::Double::NaN](https://msdn.microsoft.com/en-us/library/system.double.nan.aspx)  
  
## 请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [\_finite \_finitef](../../c-runtime-library/reference/finite-finitef.md)   
 [\_fpclass \_fpclassf](../../c-runtime-library/reference/fpclass-fpclassf.md)   
 [isnan，\_isnan \_isnanf](../../c-runtime-library/reference/isnan-isnan-isnanf.md)