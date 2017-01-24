---
title: "norm、 normf norml | Microsoft Docs"
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
  - "norm"
  - "normf"
  - "norml"
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
  - "norm"
  - "normf"
  - "norml"
  - "complex/norm"
  - "complex/normf"
  - "complex/norml"
dev_langs: 
  - "C"
  - "C++"
helpviewer_keywords: 
  - "norm 函数"
  - "normf 函数"
  - "norml 函数"
ms.assetid: 9786ecfe-0019-4553-b378-0af6c691e15c
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# norm、 normf norml
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

检索一个复杂的数字的平方的量。  
  
## 语法  
  
```  
double norm(   
   _Dcomplex z   
);  
float norm(   
   _Fcomplex z   
);  // C++ only  
long double norm(   
  _Lcomplex z   
);  // C++ only  
float normf(   
   _Fcomplex z   
);  
long double norml(   
   _Lcomplex z   
);  
```  
  
#### 参数  
 `z`  
 一个复数。  
  
## 返回值  
 平方的程度 `z`。  
  
## 备注  
 由于 c \+ \+ 允许重载，你可以调用的重载 `norm` 采用 `_Fcomplex` 或 `_Lcomplex` 值，并返回 `float` 或 `long double` 值。 在 C 程序中， `norm` 始终采用 `_Dcomplex` 值并返回 `double` 值。  
  
## 要求  
  
|例程|C 标头|C\+\+ 标头|  
|--------|----------|--------------|  
|`norm`, `normf`, `norml`|\<complex.h\>|\< \> ccomplex|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 请参阅  
 [按字母顺序的函数参考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [creal，crealf creall](../../c-runtime-library/reference/creal-crealf-creall.md)   
 [cproj，cprojf cprojl](../../c-runtime-library/reference/cproj-cprojf-cprojl.md)   
 [conj，conjf conjl](../../c-runtime-library/reference/conj-conjf-conjl.md)   
 [cimag，cimagf cimagl](../../c-runtime-library/reference/cimag-cimagf-cimagl.md)   
 [carg，cargf cargl](../../c-runtime-library/reference/carg-cargf-cargl.md)   
 [cab 文件，cabsf cabsl](../../c-runtime-library/reference/cabs-cabsf-cabsl.md)