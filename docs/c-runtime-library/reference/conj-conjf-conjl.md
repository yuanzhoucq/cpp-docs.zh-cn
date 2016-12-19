---
title: "conj，conjf conjl | Microsoft Docs"
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
  - "conj"
  - "conjf"
  - "conjl"
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
  - "conj"
  - "conjf"
  - "conjl"
  - "complex/conj"
  - "complex/conjf"
  - "complex/conjl"
dev_langs: 
  - "C"
  - "C++"
helpviewer_keywords: 
  - "conj 函数"
  - "conjf 函数"
  - "conjl 函数"
ms.assetid: 792fccfa-19c6-4890-99f9-a3b89effccd6
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# conj，conjf conjl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

检索一个复杂的数字的复数的共轭。  
  
## 语法  
  
```  
_Dcomplex conj(   
   _Dcomplex z   
);  
_Fcomplex conj(   
   _Fcomplex z   
);  // C++ only  
_Lcomplex conj(   
   _Lcomplex z   
);  // C++ only  
_Fcomplex conjf(   
   _Fcomplex z   
);  
_Lcomplex conjl(   
   _Lcomplex z   
);  
```  
  
#### 参数  
 `z`  
 一个复数。  
  
## 返回值  
 复数的共轭 `z`。  结果具有相同的实部和虚部部件 `z`, ，但符号相反。  
  
## 备注  
 由于 C\+\+ 允许重载，因此你可以调用采用并返回 `conj` 和 `_Fcomplex` 值的 `_Lcomplex` 重载。 在 C 程序中， `conj` 始终采用并返回 `_Dcomplex` 值。  
  
## 要求  
  
|例程|C 标头|C\+\+ 标头|  
|--------|----------|--------------|  
|`conj`, `conjf`, `conjl`|\<complex.h\>|\< \> ccomplex|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 请参阅  
 [按字母顺序的函数参考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [norm、 normf norml](../../c-runtime-library/reference/norm-normf-norml1.md)   
 [creal，crealf creall](../../c-runtime-library/reference/creal-crealf-creall.md)   
 [cproj，cprojf cprojl](../../c-runtime-library/reference/cproj-cprojf-cprojl.md)   
 [cimag，cimagf cimagl](../../c-runtime-library/reference/cimag-cimagf-cimagl.md)   
 [carg，cargf cargl](../../c-runtime-library/reference/carg-cargf-cargl.md)   
 [cab 文件，cabsf cabsl](../../c-runtime-library/reference/cabs-cabsf-cabsl.md)