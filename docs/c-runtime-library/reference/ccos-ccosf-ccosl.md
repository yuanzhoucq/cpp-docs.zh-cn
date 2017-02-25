---
title: "ccos，ccosf ccosl | Microsoft Docs"
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
  - "ccos"
  - "ccosf"
  - "ccosl"
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
  - "ccos"
  - "ccosf"
  - "ccosl"
  - "complex/ccos"
  - "complex/ccosf"
  - "complex/ccosl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ccos 函数"
  - "ccosf 函数"
  - "ccosl 函数"
ms.assetid: 4ab936ac-ff85-49ac-9418-2b69cf5d4696
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# ccos，ccosf ccosl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

检索一个复杂的数字的余弦值。  
  
## 语法  
  
```  
_Dcomplex ccos(   
   _Dcomplex z   
);  
_Fcomplex ccos(   
   _Fcomplex z   
);  // C++ only  
_Lcomplex ccos(   
   _Lcomplex z   
);  // C++ only  
_Fcomplex ccosf(   
   _Fcomplex z   
);  
_Lcomplex ccosl(   
   _Lcomplex z   
);  
```  
  
#### 参数  
 `z`  
 表示的角度以弧度为单位的复数。  
  
## 返回值  
 余弦值 `z`, ，以弧度为单位。  
  
## 备注  
 由于 C\+\+ 允许重载，因此你可以调用采用并返回 `ccos` 和 `_Fcomplex` 值的 `_Lcomplex` 重载。 在 C 程序中， `ccos` 始终采用并返回 `_Dcomplex` 值。  
  
## 要求  
  
|例程|C 标头|C\+\+ 标头|  
|--------|----------|--------------|  
|`ccos`, `ccosf`, `ccosl`|\<complex.h\>|\< \> ccomplex|  
  
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
 [cacos，cacosf cacosl](../../c-runtime-library/reference/cacos-cacosf-cacosl.md)   
 [ctan，ctanf ctanl](../../c-runtime-library/reference/ctan-ctanf-ctanl.md)   
 [csin，csinf csinl](../../c-runtime-library/reference/csin-csinf-csinl.md)   
 [casin，casinf casinl](../../c-runtime-library/reference/casin-casinf-casinl.md)   
 [csqrt，csqrtf csqrtl](../../c-runtime-library/reference/csqrt-csqrtf-csqrtl.md)