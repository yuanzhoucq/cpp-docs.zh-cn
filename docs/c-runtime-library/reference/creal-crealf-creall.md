---
title: "creal，crealf creall | Microsoft Docs"
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
  - "creal"
  - "crealf"
  - "creall"
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
  - "creal"
  - "crealf"
  - "creall"
  - "complex/creal"
  - "complex/crealf"
  - "complex/creall"
dev_langs: 
  - "C"
  - "C++"
helpviewer_keywords: 
  - "creal 函数"
  - "crealf 函数"
  - "creall 函数"
ms.assetid: fa3ac62f-7aa3-4238-a71f-d6b00cd0c7c8
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# creal，crealf creall
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

检索一个复数的实部。  
  
## 语法  
  
```  
double creal(   
   _Dcomplex z   
);  
float creal(   
   _Fcomplex z   
);  // C++ only  
long double creal(   
   _Lcomplex z   
);  // C++ only  
float crealf(   
   _Fcomplex z   
);  
long double creall(   
  _Lcomplex z   
);  
```  
  
#### 参数  
 `z`  
 一个复数。  
  
## 返回值  
 实部 `z`。  
  
## 备注  
 由于 c \+ \+ 允许重载，你可以调用的重载 `creal` 采用 `_Fcomplex` 或 `_Lcomplex` 值，并返回 `float` 或 `long double` 值。 在 C 程序中， `creal` 始终采用 `_Dcomplex` 值并返回 `double` 值。  
  
## 要求  
  
|例程|C 标头|C\+\+ 标头|  
|--------|----------|--------------|  
|`creal`, `crealf`, `creall`|\<complex.h\>|\< \> ccomplex|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 请参阅  
 [按字母顺序的函数参考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [norm、 normf norml](../../c-runtime-library/reference/norm-normf-norml1.md)   
 [cproj，cprojf cprojl](../../c-runtime-library/reference/cproj-cprojf-cprojl.md)   
 [conj，conjf conjl](../../c-runtime-library/reference/conj-conjf-conjl.md)   
 [cimag，cimagf cimagl](../../c-runtime-library/reference/cimag-cimagf-cimagl.md)   
 [carg，cargf cargl](../../c-runtime-library/reference/carg-cargf-cargl.md)   
 [cab 文件，cabsf cabsl](../../c-runtime-library/reference/cabs-cabsf-cabsl.md)