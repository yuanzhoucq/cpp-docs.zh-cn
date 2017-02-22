---
title: "cproj，cprojf cprojl | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "cpp"
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "cproj"
  - "cprojf"
  - "cprojl"
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
  - "cproj"
  - "cprojf"
  - "cprojl"
  - "complex/cproj"
  - "complex/cprojf"
  - "complex/cprojl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cproj 函数"
  - "cprojf 函数"
  - "cprojl 函数"
ms.assetid: 32b49623-13bf-4cae-802e-7912d75030fe
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# cproj，cprojf cprojl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

检索 Reimann 球体上一个复杂的数字的投影。  
  
## 语法  
  
```  
_Dcomplex cproj(   
   _Dcomplex z   
);  
_Fcomplex cproj(   
   _Fcomplex z   
);  // C++ only  
_Lcomplex cproj(   
   _Lcomplex z   
);  // C++ only  
_Fcomplex cprojf(   
   _Fcomplex z   
);  
_Lcomplex cprojl(   
   _Lcomplex z   
);  
```  
  
#### 参数  
 `z`  
 一个复数。  
  
## 返回值  
 投影 `z` Reimann 球体上。  
  
## 备注  
 由于 C\+\+ 允许重载，因此你可以调用采用并返回 `cproj` 和 `_Fcomplex` 值的 `_Lcomplex` 重载。 在 C 程序中， `cproj` 始终采用并返回 `_Dcomplex` 值。  
  
## 要求  
  
|例程|C 标头|C\+\+ 标头|  
|--------|----------|--------------|  
|`cproj`, `cprojf`, `cprojl`|\<complex.h\>|\< \> ccomplex|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 请参阅  
 [按字母顺序的函数参考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [norm、 normf norml](../../c-runtime-library/reference/norm-normf-norml1.md)   
 [creal，crealf creall](../../c-runtime-library/reference/creal-crealf-creall.md)   
 [conj，conjf conjl](../../c-runtime-library/reference/conj-conjf-conjl.md)   
 [cimag，cimagf cimagl](../../c-runtime-library/reference/cimag-cimagf-cimagl.md)   
 [carg，cargf cargl](../../c-runtime-library/reference/carg-cargf-cargl.md)   
 [cab 文件，cabsf cabsl](../../c-runtime-library/reference/cabs-cabsf-cabsl.md)