---
title: "cpow，cpowf cpowl | Microsoft Docs"
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
  - "cpow"
  - "cpowf"
  - "cpowl"
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
  - "cpow"
  - "cpowf"
  - "cpowl"
  - "complex/cpow"
  - "complex/cpowf"
  - "complex/copwl"
dev_langs: 
  - "C"
  - "C++"
helpviewer_keywords: 
  - "cpow 函数"
  - "cpowf 函数"
  - "复杂/cpowl 函数"
ms.assetid: 83fe2187-22b7-4295-ab16-4d77abdbb80b
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# cpow，cpowf cpowl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

检索其中的基本和指数为复数的指定幂的数字值。 此函数具有负的实际轴指数剪切一个分支。  
  
## 语法  
  
```  
_Dcomplex cpow(   
   _Dcomplex x, _Dcomplex y   
);  
_Fcomplex cpow(   
   _Fcomplex x, _Fcomplex y   
);  // C++ only  
_Lcomplex cpow(   
   _Lcomplex x, _Lcomplex y   
);  // C++ only  
_Fcomplex cpowf(   
   _Fcomplex x, _Fcomplex y   
);  
_Lcomplex cpowl(   
   _Lcomplex x, _Lcomplex y   
);  
```  
  
#### 参数  
 `x`  
 基。  
  
 `y`  
 指数。  
  
## 返回值  
 值 `x` 的次幂 `y` 与分支的剪切 `x` 负真实轴。  
  
## 备注  
 由于 C\+\+ 允许重载，因此你可以调用采用并返回 `cpow` 和 `_Fcomplex` 值的 `_Lcomplex` 重载。 在 C 程序中， `cpow` 始终采用并返回 `_Dcomplex` 值。  
  
## 要求  
  
|例程|C 标头|C\+\+ 标头|  
|--------|----------|--------------|  
|`cpow`, `cpowf`, `cpowl`|\<complex.h\>|\< \> ccomplex|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 请参阅  
 [按字母顺序的函数参考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [cexp、cexpf、cexpl](../../c-runtime-library/reference/cexp-cexpf-cexpl.md)   
 [clog10，clog10f clog10l](../../c-runtime-library/reference/clog10-clog10f-clog10l.md)   
 [clog、 clogf、 clogl](../../c-runtime-library/reference/clog-clogf-clogl.md)