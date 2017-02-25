---
title: "cacosh，cacoshf cacoshl | Microsoft Docs"
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
  - "cacosh"
  - "cacoshf"
  - "cacoshl"
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
  - "cacosh"
  - "cacoshf"
  - "cacoshl"
  - "complex/cacosh"
  - "complex/cacoshf"
  - "complex/cacoshl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cacosh 函数"
  - "cacoshf 函数"
  - "cacoshl 函数"
ms.assetid: 83fd05eb-3587-4741-9be6-589a830a1703
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# cacosh，cacoshf cacoshl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

与分支切割值等于或大于 1 实际轴检索复数的反双曲余弦值。 。  
  
## 语法  
  
```  
_Dcomplex cacosh(   
   _Dcomplex z   
);  
_Fcomplex cacosh(   
   _Fcomplex z   
);  // C++ only  
_Lcomplex cacosh(   
   _Lcomplex z   
);  // C++ only  
_Fcomplex cacoshf(   
   _Fcomplex z   
);  
_Lcomplex cacoshl(   
   _Lcomplex z   
);  
```  
  
#### 参数  
 `z`  
 表示的角度以弧度为单位的复数。  
  
## 返回值  
 反双曲余弦值 `z`, ，以弧度为单位。 结果是不受限制，并且非负的实际轴和虚部轴间隔 \[−iπ，\+ iπ\] 中。  
  
## 备注  
 由于 C\+\+ 允许重载，因此你可以调用采用并返回 `cacosh` 和 `_Fcomplex` 值的 `_Lcomplex` 重载。 在 C 程序中， `cacosh` 始终采用并返回 `_Dcomplex` 值。  
  
## 要求  
  
|例程|C 标头|C\+\+ 标头|  
|--------|----------|--------------|  
|`cacosh`, `cacoshf`, `cacoshl`|\<complex.h\>|\< \> ccomplex|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 请参阅  
 [按字母顺序的函数参考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [catanh，catanhf catanhl](../../c-runtime-library/reference/catanh-catanhf-catanhl.md)   
 [ctanh，ctanhf ctanhl](../../c-runtime-library/reference/ctanh-ctanhf-ctanhl.md)   
 [catan，catanf catanl](../../c-runtime-library/reference/catan-catanf-catanl.md)   
 [csinh，csinhf csinhl](../../c-runtime-library/reference/csinh-csinhf-csinhl.md)   
 [casinh，casinhf casinhl](../../c-runtime-library/reference/casinh-casinhf-casinhl.md)   
 [ccosh，ccoshf ccoshl](../../c-runtime-library/reference/ccosh-ccoshf-ccoshl.md)   
 [cacos，cacosf cacosl](../../c-runtime-library/reference/cacos-cacosf-cacosl.md)   
 [ctan，ctanf ctanl](../../c-runtime-library/reference/ctan-ctanf-ctanl.md)   
 [csin，csinf csinl](../../c-runtime-library/reference/csin-csinf-csinl.md)   
 [casin，casinf casinl](../../c-runtime-library/reference/casin-casinf-casinl.md)   
 [ccos，ccosf ccosl](../../c-runtime-library/reference/ccos-ccosf-ccosl.md)   
 [csqrt，csqrtf csqrtl](../../c-runtime-library/reference/csqrt-csqrtf-csqrtl.md)