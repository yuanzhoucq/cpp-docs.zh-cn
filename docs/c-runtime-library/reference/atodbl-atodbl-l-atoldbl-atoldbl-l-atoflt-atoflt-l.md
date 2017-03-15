---
title: "_atodbl, _atodbl_l, _atoldbl, _atoldbl_l, _atoflt, _atoflt_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_atoldbl"
  - "_atoldbl_l"
  - "_atodbl"
  - "_atoflt"
  - "_atoflt_l"
  - "_atodbl_l"
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
  - "_atoflt"
  - "_atoflt_l"
  - "atodbl_l"
  - "atoflt_l"
  - "_atoldbl"
  - "_atoldbl_l"
  - "atodbl"
  - "_atodbl_l"
  - "atoldbl"
  - "atoflt"
  - "atoldbl_l"
  - "_atodbl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_atodbl 函数"
  - "_atoldbl_l 函数"
  - "atoflt 函数"
  - "atoflt_l 函数"
  - "atoldbl 函数"
  - "_atoldbl 函数"
  - "atodbl_l 函数"
  - "_atoflt_l 函数"
  - "atoldbl_l 函数"
  - "atodbl 函数"
  - "字符串转换, 为浮点值"
  - "_atoflt 函数"
  - "_atodbl_l 函数"
ms.assetid: 2d2530f4-4bd4-42e3-8083-f2d2fbc8432a
caps.latest.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 22
---
# _atodbl, _atodbl_l, _atoldbl, _atoldbl_l, _atoflt, _atoflt_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将字符串转换为双精度 \(`_atodbl`\)，长双精度 \(`_atoldbl`\)，或浮点数 \(`_atoflt`\)。  
  
## 语法  
  
```  
int _atodbl(  
   _CRT_DOUBLE * value,  
   char * str  
);  
int _atodbl_l (  
   _CRT_DOUBLE * value,  
   char * str,  
   locale_t locale  
);  
int _atoldbl(  
   _LDOUBLE * value,  
   char * str  
);  
int _atoldbl_l (  
   _LDOUBLE * value,  
   char * str,  
   locale_t locale  
);  
int _atoflt(  
   _CRT_FLOAT * value,  
   const char * str  
);  
int _atoflt_l(  
   _CRT_FLOAT * value,  
   const char * str,  
   locale_t locale  
);  
```  
  
#### 参数  
 `value`  
 双精度、长双精度或浮点数值在转换字符串为浮点值的过程中产生。  这些值包装在结构体中。  
  
 `str`  
 要分析的字符串转换为浮点值。  
  
 `locale`  
 要使用的区域设置。  
  
## 返回值  
 如果成功，则返回0 。  可能的错误代码是 `_UNDERFLOW` 或 `_OVERFLOW`，在标头文件 Math.h 定义。  
  
## 备注  
 这些函数将字符串转换为浮点值。  在这些函数和 函数族`atof` 的区别在于这些函数不生成浮点代码，并不会导致硬件异常。  相反，错误代码报告错误状态。  
  
 如果字符串不能有效的解释为浮点值，`value` 设置为零，并返回值为零。  
  
 这些带有 `_l` 后缀的函数版本与那些不带此后缀的函数版本相同，只不过它们使用传递的区域设置参数而不是当前线程区域设置。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_atodbl`, `_atoldbl`, `_atoflt`<br /><br /> `_atodbl_l`, `_atoldbl_l`, `_atoflt_l`|\<stdlib.h\>|  
  
## 示例  
  
```  
// crt_atodbl.c  
// Uses _atodbl to convert a string to a double precision  
// floating point value.  
  
#include <stdlib.h>  
#include <stdio.h>  
  
int main()  
{  
   char str1[256] = "3.141592654";  
   char abc[256] = "abc";  
   char oflow[256] = "1.0E+5000";  
   _CRT_DOUBLE dblval;  
   _CRT_FLOAT fltval;  
   int retval;  
  
   retval = _atodbl(&dblval, str1);  
  
   printf("Double value: %lf\n", dblval.x);  
   printf("Return value: %d\n\n", retval);  
  
   retval = _atoflt(&fltval, str1);  
   printf("Float value: %f\n", fltval.f);  
   printf("Return value: %d\n\n", retval);  
  
   // A non-floating point value: returns 0.  
   retval = _atoflt(&fltval, abc);  
   printf("Float value: %f\n", fltval.f);  
   printf("Return value: %d\n\n", retval);  
  
   // Overflow.  
   retval = _atoflt(&fltval, oflow);  
   printf("Float value: %f\n", fltval.f);  
   printf("Return value: %d\n\n", retval);  
  
   return 0;  
}  
```  
  
  **双精度值: 3.141593**  
**返回值：0**  
**浮点值：3.141593**  
**返回值：0**  
**浮点值：0.000000**  
**返回值：0**  
**浮点值：1.\#INF00**  
**返回值：3**   
## 请参阅  
 [数据转换](../../c-runtime-library/data-conversion.md)   
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [atof、\_atof\_l、\_wtof、\_wtof\_l](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)