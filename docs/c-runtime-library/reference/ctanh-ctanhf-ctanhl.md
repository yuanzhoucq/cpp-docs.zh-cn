---
title: "ctanh，ctanhf ctanhl | Microsoft Docs"
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
  - "ctanh"
  - "ctahf"
  - "ctahl"
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
  - "ctanh"
  - "ctanhf"
  - "ctanhl"
  - "complex/ctanh"
  - "complex/ctanhf"
  - "complex/ctanhl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ctanh 函数"
  - "ctanhl 函数"
  - "ctanhf 函数"
ms.assetid: 807f2cd1-8740-4988-afff-5911c346385b
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# ctanh，ctanhf ctanhl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

计算复数的复杂双曲正切值。  
  
## 语法  
  
```  
_Dcomplex ctanh(   
   _Dcomplex z   
);  
_Fcomplex ctanh(   
   _Fcomplex z   
);  // C++ only  
_Lcomplex ctanh(   
   _Lcomplex z   
);  // C++ only  
_Fcomplex ctanhf(   
   _Fcomplex z   
);  
_Lcomplex ctanhl(   
   _Lcomplex z   
);  
```  
  
#### 参数  
 `z`  
 表示的角度以弧度为单位的复数。  
  
## 返回值  
 复杂双曲正切值 `z`。  
  
|输入|SEH 异常|`_matherr` 异常|  
|--------|------------|-------------------|  
|± ∞、QNAN、IND|无|\_DOMAIN|  
|± ∞ （tan、 tanf）|无效|\_DOMAIN|  
  
## 备注  
 由于 C\+\+ 允许重载，因此你可以调用采用并返回 `ctanh` 和 `_Fcomplex` 值的 `_Lcomplex` 重载。 在 C 程序中， `ctanh` 始终采用并返回 `_Dcomplex` 值。  
  
## 要求  
  
|例程|C 标头|C\+\+ 标头|  
|--------|----------|--------------|  
|`ctanh`, `ctanhf`, `ctanhl`|\<complex.h\>|\< \> ccomplex|  
  
 有关兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 请参阅  
 [按字母顺序的函数参考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [catanh，catanhf catanhl](../../c-runtime-library/reference/catanh-catanhf-catanhl.md)   
 [catan，catanf catanl](../../c-runtime-library/reference/catan-catanf-catanl.md)   
 [csinh，csinhf csinhl](../../c-runtime-library/reference/csinh-csinhf-csinhl.md)   
 [casinh，casinhf casinhl](../../c-runtime-library/reference/casinh-casinhf-casinhl.md)   
 [ccosh，ccoshf ccoshl](../../c-runtime-library/reference/ccosh-ccoshf-ccoshl.md)   
 [cacosh，cacoshf cacoshl](../../c-runtime-library/reference/cacosh-cacoshf-cacoshl.md)   
 [cacos，cacosf cacosl](../../c-runtime-library/reference/cacos-cacosf-cacosl.md)   
 [ctan，ctanf ctanl](../../c-runtime-library/reference/ctan-ctanf-ctanl.md)   
 [csin，csinf csinl](../../c-runtime-library/reference/csin-csinf-csinl.md)   
 [casin，casinf casinl](../../c-runtime-library/reference/casin-casinf-casinl.md)   
 [ccos，ccosf ccosl](../../c-runtime-library/reference/ccos-ccosf-ccosl.md)   
 [csqrt，csqrtf csqrtl](../../c-runtime-library/reference/csqrt-csqrtf-csqrtl.md)