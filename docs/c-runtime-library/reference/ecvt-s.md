---
title: "_ecvt_s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_ecvt_s"
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
  - "api-ms-win-crt-convert-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "ecvt_s"
  - "_ecvt_s"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_ecvt_s 函数"
  - "转换双精度数字"
  - "ecvt_s 函数"
  - "数字, 转换"
ms.assetid: d52fb0a6-cb91-423f-80b3-952a8955d914
caps.latest.revision: 25
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 25
---
# _ecvt_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将 `double` 数字转换成字符串。  [\_ecvt](../../c-runtime-library/reference/ecvt.md) 的一些版本提供安全增强功能（如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)所述）。  
  
## 语法  
  
```  
errno_t _ecvt_s(   
   char * _Buffer,  
   size_t _SizeInBytes,  
   double _Value,  
   int _Count,  
   int *_Dec,  
   int *_Sign  
);  
template <size_t size>  
errno_t _ecvt_s(   
   char (&_Buffer)[size],  
   double _Value,  
   int _Count,  
   int *_Dec,  
   int *_Sign  
); // C++ only  
```  
  
#### 参数  
 \[out\] `_Buffer`  
 用指针为数值字符串，转换的结果。  
  
 \[in\] `_SizeInBytes`  
 缓冲区的大小（以字节为单位）。  
  
 \[in\] `_Value`  
 数字可被转换.  
  
 \[in\] `_Count`  
 存储数字的数字。  
  
 \[out\] `_Dec`  
 存储小数点的位置。  
  
 \[out\] `_Sign`  
 转换后的数的符号  
  
## 返回值  
 如果成功,是0。  如果失败，返回值是错误代码。  错误代码在Errno.h中被定义。  有关更多信息，请参见 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 对于无效的参数中，如下表中所列，此函数调用的参数无效处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md)所述。  如果允许执行继续，则该函数设置 `errno` 为 `EINVAL` 并返回 `EINVAL`。  
  
### 错误情况  
  
|`_Buffer`|`_SizeInBytes`|\_Value|\_Count|\_Dec|\_Sign|返回值|`buffer`中的值|  
|---------------|--------------------|-------------|-------------|-----------|------------|---------|-----------------|  
|`NULL`|any|any|any|any|any|`EINVAL`|未被修改|  
|不是 `NULL` \(指向有效的内存\)|\<\=0|any|any|any|any|`EINVAL`|未被修改|  
|any|any|any|any|`NULL`|any|`EINVAL`|未被修改|  
|any|any|any|any|any|`NULL`|`EINVAL`|未被修改|  
  
 **安全问题**  
  
 如果 `buffer` 不指向有效的内存和不是 `NULL`，`_ecvt_s` 可能会发生访问冲突。  
  
## 备注  
 `_ecvt_s` 函数将浮点数转换为字符字符串。  `_Value` 参数是转换浮点数。  此函数以存储到 `count` `_Value` 数字为字符串并在 null 字符 \(“\\ 0 "\)。  如果数字的数目`_Value` 的溢出 `_Count`，低位数舍入。  如果小于精度的 `count` 位数，用零填充字符串。  
  
 只有数字被存储在字符串中。  小数点的位置和`_Value` 的符号可以在调用之后从 `_Dec` 和 `_Sign` 获取。   `_Dec` 参数指向一个整数值；此整数值指定相对于字符串的开头小数点的位置。  零或负整数值指示小数点位于第一个数的左侧。  到指示所转换的数字符号的整数的 `_Sign` 参数的位置。  如果整数值为 0，在数字为正数的。  否则，数字为负。  
  
 长度 `_CVTBUFSIZE` 缓冲区。所有浮点值是不够的。  
  
 `_ecvt_s` 和 `_fcvt_s` 的差异在于对 `_Count` 参数的解释不同。  `_ecvt_s` 将 `_Count` 解释为输出字符串的总位数，而 `_fcvt_s` 将 `_Count` 解释为在小数点后的位数。  
  
 在 C\+\+ 中，使用这些函数是由重载模板简化；该重载可以自动推断缓冲区长度，而无需指定范围参数。  有关更多信息，请参见[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。  
  
 这些函数的调试版本首先用 0xFD 填充缓冲区。  若要禁用此行为，请使用 [\_CrtSetDebugFillThreshold](../../c-runtime-library/reference/crtsetdebugfillthreshold.md)。  
  
## 要求  
  
|功能|必需的标头|可选标头|  
|--------|-----------|----------|  
|`_ecvt_s`|\<stdlib.h\>|\<errno.h\>|  
  
 有关更多兼容性信息，请参见简介中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// ecvt_s.c  
#include <stdio.h>  
#include <stdlib.h>  
#include <errno.h>  
  
int main( )  
{  
  char * buf = 0;  
  int decimal;  
  int sign;  
  int err;  
  
  buf = (char*) malloc(_CVTBUFSIZE);  
  err = _ecvt_s(buf, _CVTBUFSIZE, 1.2, 5, &decimal, &sign);  
  
  if (err != 0)  
  {  
     printf("_ecvt_s failed with error code %d\n", err);  
     exit(1);  
  }  
  
  printf("Converted value: %s\n", buf);    
  
}  
```  
  
  **已转换的值：12000**   
## .NET Framework 等效项  
 <xref:System.Convert.ToString%2A>  
  
## 请参阅  
 [数据转换](../../c-runtime-library/data-conversion.md)   
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [atof、\_atof\_l、\_wtof、\_wtof\_l](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)   
 [\_ecvt](../../c-runtime-library/reference/ecvt.md)   
 [\_fcvt\_s](../../c-runtime-library/reference/fcvt-s.md)   
 [\_gcvt\_s](../../c-runtime-library/reference/gcvt-s.md)