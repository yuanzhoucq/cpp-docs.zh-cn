---
title: "clog10，clog10f clog10l | Microsoft Docs"
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
  - "clog10"
  - "clog10f"
  - "clog10l"
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
  - "clog10"
  - "clog10f"
  - "clog10l"
  - "complex/clog10"
  - "complex/clog10f"
  - "complex/clog10l"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "clog10 函数"
  - "clog10f 函数"
  - "clog10l 函数"
ms.assetid: 2ddae00d-ef93-4441-add3-f4d58358401b
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# clog10，clog10f clog10l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

检索一个复杂的数字的对数。  
  
## 语法  
  
```  
_Dcomplex clog10(   
   _Dcomplex z   
);  
_Fcomplex clog10(   
  _Fcomplex z   
);  // C++ only  
_Lcomplex clog10(   
   _Lcomplex z   
);  // C++ only  
_Fcomplex clog10f(   
   _Fcomplex z   
);  
_Lcomplex clog10l(   
   _Lcomplex z   
);  
```  
  
#### 参数  
 `z`  
 对数的底。  
  
## 返回值  
 可能的返回值是︰  
  
|z 参数|返回值|  
|----------|---------|  
|正|以 10 为底的 z 对数|  
|零|\- ∞|  
|负数|NaN|  
|NaN|NaN|  
|\+ ∞|\+ ∞|  
  
## 备注  
 由于 C\+\+ 允许重载，因此你可以调用采用并返回 `clog10` 和 `_Fcomplex` 值的 `_Lcomplex` 重载。 在 C 程序中， `clog10` 始终采用并返回 `_Dcomplex` 值。  
  
## 要求  
  
|例程|C 标头|C\+\+ 标头|  
|--------|----------|--------------|  
|`clog10`, `clog10f`, `clogl`|\<complex.h\>|\< \> ccomplex|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 请参阅  
 [按字母顺序的函数参考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [cexp、cexpf、cexpl](../../c-runtime-library/reference/cexp-cexpf-cexpl.md)   
 [cpow，cpowf cpowl](../../c-runtime-library/reference/cpow-cpowf-cpowl.md)   
 [clog、 clogf、 clogl](../../c-runtime-library/reference/clog-clogf-clogl.md)