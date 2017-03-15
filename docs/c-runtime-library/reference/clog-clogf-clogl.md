---
title: "clog、 clogf、 clogl | Microsoft Docs"
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
  - "clog"
  - "clogf"
  - "clogl"
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
  - "clog"
  - "clogf"
  - "clogl"
  - "complex/clog"
  - "complex/clogf"
  - "complex/clogl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "clog 函数"
  - "clogf 函数"
  - "clogl 函数"
ms.assetid: 870b9b0b-6618-46f3-bfcf-da595cbd5e18
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# clog、 clogf、 clogl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

与分支剪切负真实轴检索一个复数的自然对数。  
  
## 语法  
  
```  
_Dcomplex clog(   
   _Dcomplex z   
);  
_Fcomplex clog(   
   _Fcomplex z   
);  // C++ only  
_Lcomplex clog(   
   _Lcomplex z   
);  // C++ only  
_Fcomplex clogf(   
   _Fcomplex z   
);  
_Lcomplex clogl(   
   _Lcomplex z   
);  
```  
  
#### 参数  
 `z`  
 对数的底。  
  
## 返回值  
 自然对数 `z`。 结果是真正轴和虚数轴间隔 \[−iπ，\+ iπ\] 中不受限制。  
  
 可能的返回值是︰  
  
|z 参数|返回值|  
|----------|---------|  
|正|以 10 为底的 z 对数|  
|零|\- ∞|  
|负数|NaN|  
|NaN|NaN|  
|\+ ∞|\+ ∞|  
  
## 备注  
 由于 C\+\+ 允许重载，因此你可以调用采用并返回 `clog` 和 `_Fcomplex` 值的 `_Lcomplex` 重载。 在 C 程序中， `clog` 始终采用并返回 `_Dcomplex` 值。  
  
## 要求  
  
|例程|C 标头|C\+\+ 标头|  
|--------|----------|--------------|  
|`clog`, `clogf`, `clogl`|\<complex.h\>|\< \> ccomplex|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 请参阅  
 [按字母顺序的函数参考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [cexp、cexpf、cexpl](../../c-runtime-library/reference/cexp-cexpf-cexpl.md)   
 [cpow，cpowf cpowl](../../c-runtime-library/reference/cpow-cpowf-cpowl.md)   
 [clog10，clog10f clog10l](../../c-runtime-library/reference/clog10-clog10f-clog10l.md)