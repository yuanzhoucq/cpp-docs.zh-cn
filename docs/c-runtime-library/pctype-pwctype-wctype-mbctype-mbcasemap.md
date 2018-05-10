---
title: _pctype、_pwctype、_wctype、_mbctype、_mbcasemap |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- pwctype
- pctype
- mbctype
- mbcasemap
- _mbcasemap
- _mbctype
- _pctype
- _wctype
- _pcwtype
dev_langs:
- C++
helpviewer_keywords:
- _wctype function
- _pwctype function
- _pctype function
- _mbctype function
- wctype function
- pwctype function
- pctype function
- mbcasemap function
- mbctype function
- _mbcasemap function
ms.assetid: 7f5e1107-c43b-4b9b-b387-781e6d2373cb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a98d570d0b43a33395a04b657b4dc2e97f9ba8e1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="pctype-pwctype-wctype-mbctype-mbcasemap"></a>_pctype、_pwctype、_wctype、_mbctype、_mbcasemap
这些全局变量包含字符分类函数使用的信息。 它们仅供内部使用。  
  
## <a name="syntax"></a>语法  
  
```  
extern const unsigned short *_pctype;  
extern const wctype_t *_pwctype;  
extern const unsigned short _wctype[];  
extern unsigned char _mbctype[];  
extern unsigned char _mbcasemap[];  
```  
  
## <a name="remarks"></a>备注  
 `_pctype`、`_pwctype` 和 `_wctype` 中的信息供内部函数 [isupper、_isupper_l、iswupper、_iswupper_l](../c-runtime-library/reference/isupper-isupper-l-iswupper-iswupper-l.md)，[islower、iswlower、_islower_l、_iswlower_l](../c-runtime-library/reference/islower-iswlower-islower-l-iswlower-l.md)、[isdigit、iswdigit、_isdigit_l、_iswdigit_l](../c-runtime-library/reference/isdigit-iswdigit-isdigit-l-iswdigit-l.md)、[isxdigit、iswxdigit、_isxdigit_l、_iswxdigit_l](../c-runtime-library/reference/isxdigit-iswxdigit-isxdigit-l-iswxdigit-l.md)、[isspace、iswspace、_isspace_l、_iswspace_l](../c-runtime-library/reference/isspace-iswspace-isspace-l-iswspace-l.md)、[isalnum、iswalnum、_isalnum_l、_iswalnum_l](../c-runtime-library/reference/isalnum-iswalnum-isalnum-l-iswalnum-l.md)、[ispunct、iswpunct、_ispunct_l、_iswpunct_l](../c-runtime-library/reference/ispunct-iswpunct-ispunct-l-iswpunct-l.md)、[isgraph、iswgraph、_isgraph_l、_iswgraph_l](../c-runtime-library/reference/isgraph-iswgraph-isgraph-l-iswgraph-l.md)，和 [iscntrl、iswcntrl、_iscntrl_l_iswcntrl_l](../c-runtime-library/reference/iscntrl-iswcntrl-iscntrl-l-iswcntrl-l.md)，以及 [toupper、_toupper、towupper、_toupper_l、_towupper_l](../c-runtime-library/reference/toupper-toupper-towupper-toupper-l-towupper-l.md) 和 [tolower、_tolower、towlower、_tolower_l、_towlower_l](../c-runtime-library/reference/tolower-tolower-towlower-tolower-l-towlower-l.md) 函数使用。 应使用这些函数来取代访问全局变量。  
  
 `_mbctype` 和 `_mbcasemap` 中的信息供 [_ismbbkalnum、_ismbbkalnum_l](../c-runtime-library/reference/ismbbkalnum-ismbbkalnum-l.md)、[_ismbbkana、_ismbbkana_l](../c-runtime-library/reference/ismbbkana-ismbbkana-l.md)、[_ismbbkpunct、_ismbbkpunct_l](../c-runtime-library/reference/ismbbkpunct-ismbbkpunct-l.md)，[_ismbbkprint、_ismbbkprint_l](../c-runtime-library/reference/ismbbkprint-ismbbkprint-l.md)、[_ismbbalpha](reference/ismbbalpha-ismbbalpha-l.md)，[_ismbbpunct、_ismbbpunct_l](../c-runtime-library/reference/ismbbpunct-ismbbpunct-l.md)，[_ismbbalnum、_ismbbalnum_l](../c-runtime-library/reference/ismbbalnum-ismbbalnum-l.md)、[_ismbbprint、_ismbbprint_l](../c-runtime-library/reference/ismbbprint-ismbbprint-l.md)、[_ismbbgraph、_ismbbgraph_l](../c-runtime-library/reference/ismbbgraph-ismbbgraph-l.md)、[_ismbblead、_ismbblead_l](../c-runtime-library/reference/ismbblead-ismbblead-l.md)、[_ismbbtrail、_ismbbtrail_l](../c-runtime-library/reference/ismbbtrail-ismbbtrail-l.md)、[_ismbslead、_ismbstrail、_ismbslead_l、_ismbstrail_l](../c-runtime-library/reference/ismbslead-ismbstrail-ismbslead-l-ismbstrail-l.md)，和 [_ismbslead、_ismbstrail、_ismbslead_l、_ismbstrail_l](../c-runtime-library/reference/ismbslead-ismbstrail-ismbslead-l-ismbstrail-l.md) 在内部使用。 应使用这些函数来取代访问全局变量。  
  
## <a name="requirements"></a>惠?  
 不适用于公共使用。  
  
## <a name="see-also"></a>请参阅  
 [is、isw 例程](../c-runtime-library/is-isw-routines.md)   
 [__pctype_func](../c-runtime-library/pctype-func.md)