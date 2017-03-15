---
title: "cacos，cacosf cacosl | Microsoft Docs"
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
  - "cacos"
  - "cacosf"
  - "cacosl"
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
  - "cacos"
  - "cacosf"
  - "cacosl"
  - "complex/cacos"
  - "complex/cacosf"
  - "complex/cacosl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cacos 函数"
  - "cacosf 函数"
  - "cacosl 函数"
ms.assetid: 78118c00-0a07-49c1-8a13-4bf19ce3aea8
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# cacos，cacosf cacosl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

检索实际轴间隔 \[− 1，\+ 1\] 之外的分支剪切为复数的反余弦值。  
  
## 语法  
  
```  
_Dcomplex cacos(   
  _Dcomplex z   
);  
_Fcomplex cacos(   
   _Fcomplex z   
);  // C++ only  
_Lcomplex cacos(   
   _Lcomplex z   
);  // C++ only  
_Fcomplex cacosf(   
   _Fcomplex z   
);  
_Lcomplex cacosl(   
   _Lcomplex z   
);  
```  
  
#### 参数  
 `z`  
 表示的角度以弧度为单位的复数。  
  
## 返回值  
 反余弦值 `z`, ，以弧度为单位。 结果是不受限制的假想轴和实际轴间隔 \[0，π\] 中。 如果将发生域错误 `z` 之外 \[\-1，\+ 1\]。  
  
## 备注  
 由于 C\+\+ 允许重载，因此你可以调用采用并返回 `cacos` 和 `_Fcomplex` 值的 `_Lcomplex` 重载。 在 C 程序中， `cacos` 始终采用并返回 `_Dcomplex` 值。  
  
## 要求  
  
|例程|C 标头|C\+\+ 标头|  
|--------|----------|--------------|  
|`cacos`, `cacosf`, `cacosl`|\<complex.h\>|\< \> ccomplex|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 请参阅  
 [按字母顺序的函数参考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [catanh，catanhf catanhl](../../c-runtime-library/reference/catanh-catanhf-catanhl.md)   
 [ctanh，ctanhf ctanhl](../../c-runtime-library/reference/ctanh-ctanhf-ctanhl.md)   
 [catan，catanf catanl](../../c-runtime-library/reference/catan-catanf-catanl.md)   
 [csinh，csinhf csinhl](../../c-runtime-library/reference/csinh-csinhf-csinhl.md)   
 [casinh，casinhf casinhl](../../c-runtime-library/reference/casinh-casinhf-casinhl.md)   
 [ccosh，ccoshf ccoshl](../../c-runtime-library/reference/ccosh-ccoshf-ccoshl.md)   
 [cacosh，cacoshf cacoshl](../../c-runtime-library/reference/cacosh-cacoshf-cacoshl.md)   
 [ctan，ctanf ctanl](../../c-runtime-library/reference/ctan-ctanf-ctanl.md)   
 [csin，csinf csinl](../../c-runtime-library/reference/csin-csinf-csinl.md)   
 [casin，casinf casinl](../../c-runtime-library/reference/casin-casinf-casinl.md)   
 [ccos，ccosf ccosl](../../c-runtime-library/reference/ccos-ccosf-ccosl.md)   
 [csqrt，csqrtf csqrtl](../../c-runtime-library/reference/csqrt-csqrtf-csqrtl.md)