---
title: "_fcvt_s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_fcvt_s"
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
  - "fcvt_s"
  - "_fcvt_s"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_fcvt_s 函数"
  - "转换浮点, 为字符串"
  - "fcvt_s 函数"
  - "浮点函数, 将数字转换为字符串"
ms.assetid: 48671197-1d29-4c2b-a5d8-d2368f5f68a1
caps.latest.revision: 27
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 27
---
# _fcvt_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将浮点数转换为字符串。  [\_fcvt](../../c-runtime-library/reference/fcvt.md) 的一些版本提供安全增强功能（如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)所述）。  
  
## 语法  
  
```  
errno_t _fcvt_s(   
   char* buffer,  
   size_t sizeInBytes,  
   double value,  
   int count,  
   int *dec,  
   int *sign   
);  
template <size_t size>  
errno_t _fcvt_s(   
   char (&buffer)[size],  
   double value,  
   int count,  
   int *dec,  
   int *sign   
); // C++ only  
```  
  
#### 参数  
 \[out\] `buffer`  
 提供的缓冲区将保持转换的结果。  
  
 \[in\] `sizeInBytes`  
 缓冲区的字节大小。  
  
 \[in\] `value`  
 数字可被转换.  
  
 \[in\] `count`  
 小数点后数字的位数。  
  
 \[out\] `dec`  
 指向存储的小数点位置的指针。  
  
 \[out\] `sign`  
 指向存储的符号指示器的指针。  
  
## 返回值  
 如果成功,是0。  如果失败，返回值是错误代码。  错误代码在Errno.h中被定义。  有关这些错误的列表，请参阅[errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 对于无效的参数中，如下表中所列，此函数调用的参数无效处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md)所述。  如果允许执行继续，则该函数设置 `errno` 为 `EINVAL` 并返回 `EINVAL`。  
  
### 错误情况  
  
|`buffer`|`sizeInBytes`|值|count|dec|sign|返回|`buffer`中的值|  
|--------------|-------------------|-------|-----------|---------|----------|--------|-----------------|  
|`NULL`|any|any|any|any|any|`EINVAL`|未被修改|  
|不是 `NULL` \(指向有效的内存\)|\<\=0|any|any|any|any|`EINVAL`|未被修改|  
|any|any|any|any|`NULL`|any|`EINVAL`|未被修改|  
|any|any|any|any|any|`NULL`|`EINVAL`|未被修改|  
  
 **安全问题**  
  
 如果 `buffer` 不指向有效的内存和不是 `NULL`，`_fcvt_s` 可能会发生访问冲突。  
  
## 备注  
 `_fcvt_s` 函数将浮点数转换为空终止字符字符串。  `value` 参数是转换浮点数。  `_fcvt_s` 存储 `value` 值作为字符串并添加空字符 \(“\\ 0 "\)。  `count` 参数指定小数点后要存储的位数。  多余的数字被四舍五入到 `count` 位置。  如果小于精度的 `count` 位数，用零填充字符串。  
  
 只有数字被存储在字符串中。  小数点的位置和`value` 的符号可以在调用之后从 `dec` 和 `sign` 获取。   `dec` 参数指向一个整数值；此整数值指定相对于字符串的开头小数点的位置。  零或负整数值指示小数点位于第一个数的左侧。  参数 `value` 指向一个整数表示 `sign` 标记。  如果 `value` 是正，则整数设置为 0，如果 `value` 为负，则设置为一个非零值。  
  
 长度为 `_CVTBUFSIZE` 的缓冲区足够存储任意浮点值。  
  
 `_ecvt_s` 和 `_fcvt_s` 的差异在于对 `count` 参数的解释不同。  `_ecvt_s` 将 `count` 解释为输出字符串的总位数，而 `_fcvt_s` 将 c`ount` 解释为在小数点后的位数。  
  
 在 C\+\+ 中，使用这些函数是由重载模板简化；该重载可以自动推断缓冲区长度，而无需指定范围参数。  有关更多信息，请参见[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。  
  
 这些函数的调试版本首先用 0xFD 填充缓冲区。  若要禁用此行为，请使用 [\_CrtSetDebugFillThreshold](../../c-runtime-library/reference/crtsetdebugfillthreshold.md)。  
  
## 要求  
  
|功能|必需的标头|可选标头|  
|--------|-----------|----------|  
|`_fcvt_s`|\<stdlib.h\>|\<errno.h\>|  
  
 有关更多兼容性信息，请参见简介中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
 **Libraries:** 的所有版本 [CRT 库功能](../../c-runtime-library/crt-library-features.md).  
  
## 示例  
  
```  
// fcvt_s.c  
#include <stdio.h>  
#include <stdlib.h>  
#include <errno.h>  
  
int main()  
{  
  char * buf = 0;  
  int decimal;  
  int sign;  
  int err;  
  
  buf = (char*) malloc(_CVTBUFSIZE);  
  err = _fcvt_s(buf, _CVTBUFSIZE, 1.2, 5, &decimal, &sign);  
  
  if (err != 0)  
  {  
     printf("_fcvt_s failed with error code %d\n", err);  
     exit(1);  
  }  
  
  printf("Converted value: %s\n", buf);    
  
}  
```  
  
  **已转换的值: 120000**   
## .NET Framework 等效项  
 <xref:System.Convert.ToString%2A>  
  
## 请参阅  
 [数据转换](../../c-runtime-library/data-conversion.md)   
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [atof、\_atof\_l、\_wtof、\_wtof\_l](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)   
 [\_ecvt\_s](../../c-runtime-library/reference/ecvt-s.md)   
 [\_gcvt\_s](../../c-runtime-library/reference/gcvt-s.md)   
 [\_fcvt](../../c-runtime-library/reference/fcvt.md)