---
title: "_pctype、_pwctype、_wctype、_mbctype、_mbcasemap | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "pwctype"
  - "pctype"
  - "mbctype"
  - "mbcasemap"
  - "_mbcasemap"
  - "_mbctype"
  - "_pctype"
  - "_wctype"
  - "_pcwtype"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_wctype 函数"
  - "_pwctype 函数"
  - "_pctype 函数"
  - "_mbctype 函数"
  - "wctype 函数"
  - "pwctype 函数"
  - "pctype 函数"
  - "mbcasemap 函数"
  - "mbctype 函数"
  - "_mbcasemap 函数"
ms.assetid: 7f5e1107-c43b-4b9b-b387-781e6d2373cb
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _pctype、_pwctype、_wctype、_mbctype、_mbcasemap
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

这些全局变量包含使用字符分类函数的信息。  仅供内部使用。  
  
## 语法  
  
```  
extern const unsigned short *_pctype;  
extern const wctype_t *_pwctype;  
extern const unsigned short _wctype[];  
extern unsigned char _mbctype[];  
extern unsigned char _mbcasemap[];  
```  
  
## 备注  
 在 `_pctype`, `_pwctype` 和 `_wctype` 的信息通过函数 [isupper、\_isupper\_l、iswupper、\_iswupper\_l](../c-runtime-library/reference/isupper-isupper-l-iswupper-iswupper-l.md), [islower、iswlower、\_islower\_l、\_iswlower\_l](../c-runtime-library/reference/islower-iswlower-islower-l-iswlower-l.md), [isdigit、iswdigit、\_isdigit\_l、\_iswdigit\_l](../c-runtime-library/reference/isdigit-iswdigit-isdigit-l-iswdigit-l.md), [isxdigit、iswxdigit、\_isxdigit\_l、\_iswxdigit\_l](../c-runtime-library/reference/isxdigit-iswxdigit-isxdigit-l-iswxdigit-l.md), [isspace、iswspace、\_isspace\_l、\_iswspace\_l](../c-runtime-library/reference/isspace-iswspace-isspace-l-iswspace-l.md), [isalnum、iswalnum、\_isalnum\_l、\_iswalnum\_l](../c-runtime-library/reference/isalnum-iswalnum-isalnum-l-iswalnum-l.md), [ispunct、iswpunct、\_ispunct\_l、\_iswpunct\_l](../c-runtime-library/reference/ispunct-iswpunct-ispunct-l-iswpunct-l.md), [isgraph、iswgraph、\_isgraph\_l、\_iswgraph\_l](../c-runtime-library/reference/isgraph-iswgraph-isgraph-l-iswgraph-l.md) 和 [iscntrl、iswcntrl、\_iscntrl\_l、\_iswcntrl\_l](../c-runtime-library/reference/iscntrl-iswcntrl-iscntrl-l-iswcntrl-l.md) 在内部使用, 同样地对于 [toupper、\_toupper、towupper、\_toupper\_l、\_towupper\_l](../c-runtime-library/reference/toupper-toupper-towupper-toupper-l-towupper-l.md) 和 [tolower、\_tolower、towlower、\_tolower\_l、\_towlower\_l](../c-runtime-library/reference/tolower-tolower-towlower-tolower-l-towlower-l.md) 函数。  使用这些函数而不是访问这些全局变量。  
  
 在 `_mbctype` 和 `_mbcasemap` 的信息通过 [\_ismbbkalnum、\_ismbbkalnum\_l](../c-runtime-library/reference/ismbbkalnum-ismbbkalnum-l.md), [\_ismbbkana、\_ismbbkana\_l](../c-runtime-library/reference/ismbbkana-ismbbkana-l.md), [\_ismbbkpunct、\_ismbbkpunct\_l](../c-runtime-library/reference/ismbbkpunct-ismbbkpunct-l.md), [\_ismbbkprint、\_ismbbkprint\_l](../c-runtime-library/reference/ismbbkprint-ismbbkprint-l.md), [\_ismbbalpha](http://msdn.microsoft.com/zh-cn/8e54cb92-fc2b-41f5-8ab4-b22ac8aa9ad0), [\_ismbbpunct、\_ismbbpunct\_l](../c-runtime-library/reference/ismbbpunct-ismbbpunct-l.md), [\_ismbbalnum、\_ismbbalnum\_l](../c-runtime-library/reference/ismbbalnum-ismbbalnum-l.md), [\_ismbbprint、\_ismbbprint\_l](../c-runtime-library/reference/ismbbprint-ismbbprint-l.md), [\_ismbbgraph、\_ismbbgraph\_l](../c-runtime-library/reference/ismbbgraph-ismbbgraph-l.md), [\_ismbblead、\_ismbblead\_l](../c-runtime-library/reference/ismbblead-ismbblead-l.md), [\_ismbbtrail、\_ismbbtrail\_l](../c-runtime-library/reference/ismbbtrail-ismbbtrail-l.md), [\_ismbslead、\_ismbstrail、\_ismbslead\_l、\_ismbstrail\_l](../c-runtime-library/reference/ismbslead-ismbstrail-ismbslead-l-ismbstrail-l.md) 和 [\_ismbslead、\_ismbstrail、\_ismbslead\_l、\_ismbstrail\_l](../c-runtime-library/reference/ismbslead-ismbstrail-ismbslead-l-ismbstrail-l.md) 在内部使用。  使用这些函数而不是访问全局变量。  
  
## 要求  
 不适用于公共使用。  
  
## 请参阅  
 [is、isw 例程](../c-runtime-library/is-isw-routines.md)   
 [\_\_pctype\_func](../c-runtime-library/pctype-func.md)