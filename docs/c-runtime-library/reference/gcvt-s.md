---
title: "_gcvt_s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_gcvt_s"
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
  - "_gcvt_s"
  - "gcvt_s"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_CVTBUFSIZE"
  - "_gcvt_s 函数"
  - "转换, 浮点到字符串"
  - "CVTBUFSIZE"
  - "浮点函数, 将数字转换为字符串"
  - "gcvt_s 函数"
  - "数字, 转换为字符串"
  - "字符串 [C++], 从浮点转换"
ms.assetid: 0a8d8a26-5940-4ae3-835e-0aa6ec1b0744
caps.latest.revision: 30
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 30
---
# _gcvt_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

转换浮点值到字符串。  [\_gcvt](../../c-runtime-library/reference/gcvt.md) 的一些版本提供安全增强功能（如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)所述）。  
  
## 语法  
  
```  
errno_t _gcvt_s(   
   char *buffer,  
   size_t sizeInBytes,  
   double value,  
   int digits   
);  
template <size_t cchStr>  
errno_t _gcvt_s(   
   char (&buffer)[cchStr],  
   double value,  
   int digits   
); // C++ only  
```  
  
#### 参数  
 \[out\] `buffer`  
 存储转换结果的缓冲区。  
  
 \[in\] `sizeInBytes`  
 缓冲区的大小。  
  
 \[in\] `value`  
 要转换的值。  
  
 \[in\] `digits`  
 存储的有效位数。  
  
## 返回值  
 如果成功,是0。  如果发生失败由于无效的参数为无效值 \(请参见下表\)，则参数的处理程序调用。[参数验证](../../c-runtime-library/parameter-validation.md)所述。  如果允许代码继续执行，则返回错误代码。  错误代码在Errno.h中被定义。  有关这些错误的列表，请参阅[errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
### 错误情况  
  
|`buffer`|`sizeInBytes`|`value`|`digits`|返回|`buffer`中的值|  
|--------------|-------------------|-------------|--------------|--------|-----------------|  
|`NULL`|any|any|any|`EINVAL`|未被修改|  
|不是 `NULL` \(指向有效的内存\)|零|any|any|`EINVAL`|未被修改|  
|不是 `NULL` \(指向有效的内存\)|any|any|\>\= `sizeInBytes`|`EINVAL`|未被修改|  
  
 **安全问题**  
  
 如果 `buffer` 不指向有效的内存和不是 `NULL`，`_gcvt_s` 可能会发生访问冲突。  
  
## 备注  
 `_gcvt_s` 函数将浮点 `value`转换为字符字符串（ 包含小数点和一种符号字节\)，并存储在`buffer`中。  `buffer` 应该足够大以容纳转换的值和自动追加的终止 null 字符。  长度为 `_CVTBUFSIZE` 的缓冲区足够存储任意浮点值。  如果 1 \+ 使用缓冲区大小，`digits` 函数不会覆盖缓冲区末尾的，因此，为确保提供此操作的一个满足的缓冲区。  `_gcvt_s` 尝试产生十进制格式的`digits`数值。  如果不能，它产生指数格式`digits`的数值。  在转换中尾随零转换可能被抑制。  
  
 在 C\+\+ 中，使用这些函数是由重载模板简化；该重载可以自动推断缓冲区长度，而无需指定范围参数。  有关更多信息，请参见[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。  
  
 这些函数的调试版本首先用 0xFD 填充缓冲区。  若要禁用此行为，请使用 [\_CrtSetDebugFillThreshold](../../c-runtime-library/reference/crtsetdebugfillthreshold.md)。  
  
## 要求  
  
|例程|必需的标头|可选标头|  
|--------|-----------|----------|  
|`_gcvt_s`|\<stdlib.h\>|\<error.h\>|  
  
 有关更多兼容性信息，请参见简介中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_gcvt_s.c  
#include <stdio.h>  
#include <stdlib.h>  
#include <errno.h>  
  
int main()  
{  
  char buf[_CVTBUFSIZE];  
  int decimal;  
  int sign;  
  int err;  
  
  err = _gcvt_s(buf, _CVTBUFSIZE, 1.2, 5);  
  
  if (err != 0)  
  {  
     printf("_gcvt_s failed with error code %d\n", err);  
     exit(1);  
  }  
  
  printf("Converted value: %s\n", buf);    
  
}  
```  
  
  **已转换的值: 1.2**   
## .NET Framework 等效项  
 <xref:System.Convert.ToString%2A>  
  
## 请参阅  
 [数据转换](../../c-runtime-library/data-conversion.md)   
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [atof、\_atof\_l、\_wtof、\_wtof\_l](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)   
 [\_ecvt\_s](../../c-runtime-library/reference/ecvt-s.md)   
 [\_fcvt\_s](../../c-runtime-library/reference/fcvt-s.md)   
 [\_gcvt](../../c-runtime-library/reference/gcvt.md)