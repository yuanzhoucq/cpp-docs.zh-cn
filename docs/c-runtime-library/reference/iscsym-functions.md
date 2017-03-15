---
title: "iscsym、 iscsymf、 __iscsym、 __iswcsym、 __iscsymf、 __iswcsymf、 _iscsym_l、 _iswcsym_l、 _iscsymf_l、 _iswcsymf_l | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_iswcsym_l"
  - "__iswcsym"
  - "__iscsym"
  - "_iswcsymf_l"
  - "_iscsym_l"
  - "__iswcsymf"
  - "__iscsymf"
  - "_iscsymf_l"
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
  - "api-ms-win-crt-string-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_iswcsym_l"
  - "_iswcsymf_l"
  - "iscsymf"
  - "iswcsymf"
  - "__iswcsym"
  - "__iswcsymf"
  - "iscsym"
  - "iswcsym"
  - "__iscsym"
  - "_iscsym_l"
  - "_iscsymf_l"
  - "__iscsymf"
  - "ctype/iscsym"
  - "ctype/iscsymf"
  - "ctype/__iscsym"
  - "ctype/__iscsymf"
  - "ctype/__iscsym_l"
  - "ctype/__iscsymf_l"
  - "ctype/__iswcsym"
  - "ctype/__iswcsymf"
  - "ctype/__iswcsym_l"
  - "ctype/__iswcsymf_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "iscsymf_l 函数"
  - "iswsym_l 函数"
  - "_iswcsym_l 函数"
  - "iscsym_l 函数"
  - "_iscsymf_l 函数"
  - "_iswcsymf_l 函数"
  - "_iscsym_l 函数"
  - "__iscsym 函数"
  - "__iswcsymf 函数"
  - "iswsymf_l 函数"
  - "__iscsymf 函数"
  - "__iswcsym 函数"
  - "iscsym 函数"
  - "iscsymf 函数"
ms.assetid: 944dfb99-f2b8-498c-9f55-dbcf370d0a2c
caps.latest.revision: 21
caps.handback.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# iscsym、 iscsymf、 __iscsym、 __iswcsym、 __iscsymf、 __iswcsymf、 _iscsym_l、 _iswcsym_l、 _iscsymf_l、 _iswcsymf_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

确定整数是否表示可在标识符中使用的字符。  
  
## 语法  
  
```  
int __iscsym(   
   int c   
);  
int __iswcsym(   
   wint_t c   
);  
int __iscsymf(   
   int c   
);  
int __iswcsymf(   
   wint_t c   
);  
int _iscsym_l(   
   int c,  
   _locale_t locale  
);  
int _iswcsym_l(   
   wint_t c,  
   _locale_t locale  
);  
int _iscsymf_l(   
   int c,  
   _locale_t locale  
);  
int _iswcsymf_l(   
   wint_t c,  
   _locale_t locale  
);  
#define iscsym __iscsym  
#define iscsymf __iscsymf  
```  
  
#### 参数  
 `c`  
 要测试的整数。`c` 应位于函数的窄字符版本的 0\-255 范围内。  
  
 `locale`  
 要使用的区域设置。  
  
## 返回值  
 这两 `__iscsym` 和 `__iswcsym` 返回非零值，如果 `c` 是字母、 下划线或数字。 同时 `__iscsymf` 和 `__iswcsymf` 返回非零值，如果 `c` 是字母或下划线。 如果 `c` 不满足测试条件，则这些例程都返回 0。 这些带有 `_l` 后缀的函数的版本相同，只不过它们使用传递区域设置而不是其与区域设置相关的行为的当前区域设置。 有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
## 备注  
 除非定义预处理器宏 \_CTYPE\_DISABLE\_MACROS，这些例程都定义为宏。 当使用这些例程的宏版本时，可以多次计算参数。 使用具有参数列表中的副作用的表达式时要小心。  
  
 为了向后兼容， `iscsym` 和 `iscsymf` 定义为宏时，才 [\_\_STDC\_\_](../../preprocessor/predefined-macros.md) 未定义或定义为 0; 否则是不确定。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`iscsym`, `iscsymf`, `__iscsym`, `__iswcsym`, `__iscsymf`, `__iswcsymf`, `_iscsym_l`, `_iswcsym_l`, `_iscsymf_l`, `_iswcsymf_l`|C: \< ctype.h \><br /><br /> C \+ \+: \< cctype \> 或 \< ctype.h \>|  
  
 `iscsym`, ，`iscsymf`, ，`__iscsym`, ，`__iswcsym`, ，`__iscsymf`, ，`__iswcsymf`, ，`_iscsym_l`, ，`_iswcsym_l`, ，`_iscsymf_l`, ，和 `_iswcsymf_l` 例程是 Microsoft 专用。 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 请参阅  
 [字符分类](../../c-runtime-library/character-classification.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [is、isw 例程](../../c-runtime-library/is-isw-routines.md)