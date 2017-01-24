---
title: "cab 文件，cabsf cabsl | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "cpp"
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "cabs"
  - "cabsf"
  - "cabsl"
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
  - "cabs"
  - "cabsf"
  - "cabsl"
  - "complex/cabs"
  - "complex/cabsf"
  - "complex/cabsl"
dev_langs: 
  - "C"
  - "C++"
helpviewer_keywords: 
  - "cabs 函数"
  - "cabsf 函数"
  - "cabsl 函数"
ms.assetid: 6b8eb453-cc8f-4972-bebf-351cbdfdfc15
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# cab 文件，cabsf cabsl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

检索一个复杂的数字的绝对值的数值。  
  
## 语法  
  
```  
double cabs(   
   _Dcomplex z   
);  
float cabs(   
   _Fcomplex z   
);  // C++ only  
long double cabs(   
   _Lcomplex z   
);  // C++ only  
float cabsf(   
   _Fcomplex z   
);  
long double cabsl(   
   _Lcomplex z   
);  
```  
  
#### 参数  
 `z`  
 一个复数。  
  
## 返回值  
 数值的绝对值 `z`。  
  
## 备注  
 由于 c \+ \+ 允许重载，你可以调用的重载 `cabs` 采用 `_Fcomplex` 或 `_Lcomplex` 值，并返回 `float` 或 `long double` 值。 在 C 程序中， `cabs` 始终采用 `_Dcomplex` 值并返回 `double` 值。  
  
## 要求  
  
|例程|C 标头|C\+\+ 标头|  
|--------|----------|--------------|  
|`cabs`, `cabsf`, `cabsl`|\<complex.h\>|\< \> ccomplex|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 请参阅  
 [按字母顺序的函数参考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [norm、 normf norml](../../c-runtime-library/reference/norm-normf-norml1.md)   
 [creal，crealf creall](../../c-runtime-library/reference/creal-crealf-creall.md)   
 [cproj，cprojf cprojl](../../c-runtime-library/reference/cproj-cprojf-cprojl.md)   
 [conj，conjf conjl](../../c-runtime-library/reference/conj-conjf-conjl.md)   
 [cimag，cimagf cimagl](../../c-runtime-library/reference/cimag-cimagf-cimagl.md)   
 [carg，cargf cargl](../../c-runtime-library/reference/carg-cargf-cargl.md)