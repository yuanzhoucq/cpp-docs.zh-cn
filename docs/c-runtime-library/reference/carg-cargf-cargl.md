---
title: "carg，cargf cargl | Microsoft Docs"
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
  - "carg"
  - "cargf"
  - "cargl"
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
  - "carg"
  - "cargf"
  - "cargl"
  - "complex/carg"
  - "complex/cargf"
  - "complex/cargl"
dev_langs: 
  - "C"
  - "C++"
helpviewer_keywords: 
  - "carg 函数"
  - "cargf 函数"
  - "cargl 函数"
ms.assetid: 610d6a93-b929-46ab-a966-b77db0b804be
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# carg，cargf cargl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

与分支剪切负真实轴检索大量复杂的参数。  
  
## 语法  
  
```  
double carg(   
   _Dcomplex z   
);  
float carg(   
   _Fcomplex z   
);  // C++ only  
long double carg(   
   _Lcomplex z   
);  // C++ only  
float cargf(   
   _Fcomplex z   
);  
long double cargl(   
   _Lcomplex z   
);  
```  
  
#### 参数  
 `z`  
 一个复数。  
  
## 返回值  
 参数 （也称为阶段） `z`。 结果是在 \[−π，\+ π\] 的间隔内。  
  
## 备注  
 由于 c \+ \+ 允许重载，你可以调用的重载 `carg` 采用 `_Fcomplex` 或 `_Lcomplex` 值，并返回 `float` 或 `long double` 值。 在 C 程序中， `carg` 始终采用 `_Dcomplex` 值并返回 `double` 值。  
  
## 要求  
  
|例程|C 标头|C\+\+ 标头|  
|--------|----------|--------------|  
|`carg`, `cargf`, `cargl`|\<complex.h\>|\< \> ccomplex|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 请参阅  
 [按字母顺序的函数参考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [norm、 normf norml](../../c-runtime-library/reference/norm-normf-norml1.md)   
 [creal，crealf creall](../../c-runtime-library/reference/creal-crealf-creall.md)   
 [cproj，cprojf cprojl](../../c-runtime-library/reference/cproj-cprojf-cprojl.md)   
 [conj，conjf conjl](../../c-runtime-library/reference/conj-conjf-conjl.md)   
 [cimag，cimagf cimagl](../../c-runtime-library/reference/cimag-cimagf-cimagl.md)   
 [cab 文件，cabsf cabsl](../../c-runtime-library/reference/cabs-cabsf-cabsl.md)