---
title: "_ismbb 例程 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apilocation:
- msvcr110.dll
- msvcrt.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr90.dll
- msvcr100.dll
apitype: DLLExport
f1_keywords:
- _ismbb
- ismbb
dev_langs:
- C++
helpviewer_keywords:
- ismbb routines
- _ismbb routines
ms.assetid: d63c232e-3fe4-4844-aafd-2133846ece4b
caps.latest.revision: 14
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: 2ac04f1efef14b0a86a24eed2ebef8b92bffaf01
ms.lasthandoff: 04/01/2017

---
# <a name="ismbb-routines"></a>_ismbb 例程
使用当前区域设置或指定 LC_CTYPE 转换状态类别，针对特定条件测试给定整数值 `c` 。  
  
|||  
|-|-|  
|[_ismbbalnum、_ismbbalnum_l](../c-runtime-library/reference/ismbbalnum-ismbbalnum-l.md)|[_ismbbkprint、_ismbbkprint_l](../c-runtime-library/reference/ismbbkprint-ismbbkprint-l.md)|  
|[_ismbbalpha、_ismbbalpha_l](http://msdn.microsoft.com/en-us/8e54cb92-fc2b-41f5-8ab4-b22ac8aa9ad0)|[_ismbbkpunct、_ismbbkpunct_l](../c-runtime-library/reference/ismbbkpunct-ismbbkpunct-l.md)|  
|[_ismbbblank、_ismbbblank_l](../c-runtime-library/reference/ismbbblank-ismbbblank-l.md)|[_ismbblead、_ismbblead_l](../c-runtime-library/reference/ismbblead-ismbblead-l.md)|  
|[_ismbbgraph、_ismbbgraph_l](../c-runtime-library/reference/ismbbgraph-ismbbgraph-l.md)|[_ismbbprint、_ismbbprint_l](../c-runtime-library/reference/ismbbprint-ismbbprint-l.md)|  
|[_ismbbkalnum、_ismbbkalnum_l](../c-runtime-library/reference/ismbbkalnum-ismbbkalnum-l.md)|[_ismbbpunct、_ismbbpunct_l](../c-runtime-library/reference/ismbbpunct-ismbbpunct-l.md)|  
|[_ismbbkana、_ismbbkana_l](../c-runtime-library/reference/ismbbkana-ismbbkana-l.md)|[_ismbbtrail、_ismbbtrail_l](../c-runtime-library/reference/ismbbtrail-ismbbtrail-l.md)|  
  
## <a name="remarks"></a>备注  
 `_ismbb` 系列中的每个例程会针对特定条件测试给定整数值 `c` 。 测试结果取决于有效的多字节代码页。 默认情况下，多字节代码页设置为在程序启动时从操作系统获取的 ANSI 代码页。 可使用 [_getmbcp](../c-runtime-library/reference/getmbcp.md) 查询所使用的多字节代码页，或使用 [_setmbcp](../c-runtime-library/reference/setmbcp.md) 更改它。  
  
 输出值受区域设置的 `LC_CTYPE` 类别设置的影响；有关详细信息，请参阅 [setlocale、_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)。 这些不带 **_l** 后缀的函数的版本将当前区域设置用于此依赖于区域设置的行为；带有 **_l** 后缀的版本与之相同，只不过它们改用传入的区域设置参数。  
  
 `_ismbb` 系列中的例程按如下所示测试给定整数 `c` 。  
  
|例程|字节测试条件|  
|-------------|-------------------------|  
|[_ismbbalnum](../c-runtime-library/reference/ismbbalnum-ismbbalnum-l.md)|`isalnum` &#124;&#124; `_ismbbkalnum`.|  
|[_ismbbalpha](http://msdn.microsoft.com/en-us/8e54cb92-fc2b-41f5-8ab4-b22ac8aa9ad0)|`isalpha` &#124;&#124; `_ismbbkalnum`.|  
|[_ismbbblank](../c-runtime-library/reference/ismbbblank-ismbbblank-l.md)|`isblank`|  
|[_ismbbgraph](../c-runtime-library/reference/ismbbgraph-ismbbgraph-l.md)|与 `_ismbbprint`相同，但是 `_ismbbgraph` 不包含空格字符 (0x20)。|  
|[_ismbbkalnum](../c-runtime-library/reference/ismbbkalnum-ismbbkalnum-l.md)|标点以外的非 ASCII 文本符号。 例如，仅在代码页 932 中， `_ismbbkalnum` 测试片假名字母数字。|  
|[_ismbbkana](../c-runtime-library/reference/ismbbkana-ismbbkana-l.md)|片假名 (0xA1 - 0xDF)。 特定于代码页 932。|  
|[_ismbbkprint](../c-runtime-library/reference/ismbbkprint-ismbbkprint-l.md)|非 ASCII 文本或非 ASCII 标点符号。 例如，仅在代码页 932 中，`_ismbbkprint` 测试片假名字母数字或片假名标点（范围：0xA1 - 0xDF）。|  
|[_ismbbkpunct](../c-runtime-library/reference/ismbbkpunct-ismbbkpunct-l.md)|非 ASCII 标点。 例如，仅在代码页 932 中，`_ismbbkpunct` 测试片假名标点。|  
|[_ismbblead](../c-runtime-library/reference/ismbblead-ismbblead-l.md)|多字节字符的第一个字节。 例如，仅在代码页 932 中，有效范围为 0x81 - 0x9F 以及 0xE0 - 0xFC。|  
|[_ismbbprint](../c-runtime-library/reference/ismbbprint-ismbbprint-l.md)|`isprint` &#124;&#124; `_ismbbkprint`. **ismbbprint** 包含空白字符 (0x20)。|  
|[_ismbbpunct](../c-runtime-library/reference/ismbbpunct-ismbbpunct-l.md)|`ispunct` &#124;&#124; `_ismbbkpunct`.|  
|[_ismbbtrail](../c-runtime-library/reference/ismbbtrail-ismbbtrail-l.md)|多字节字符的第二个字节。 例如，仅在代码页 932 中，有效范围为 0x40 - 0x7E 以及 0x80 - 0xEC。|  
  
 下表显示组成这些例程测试条件的经过“或”运算的值。 清单常量 `_BLANK`、 `_DIGIT`、 `_LOWER`、 `_PUNCT`和 `_UPPER` 在 Ctype.h 中进行定义。  
  
|例程|_BLANK|_DIGIT|LOWER|_PUNCT|UPPER|Non-<br /><br /> ASCII<br /><br /> 文本|Non-<br /><br /> ASCII<br /><br /> punct|  
|-------------|-------------|-------------|-----------|-------------|-----------|------------------------------|-------------------------------|  
|`_ismbbalnum`|—|x|x|—|x|x|—|  
|`_ismbbalpha`|—|—|x|—|x|x|—|  
|`_ismbbblank`|x|—|—|—|—|—|—|  
|`_ismbbgraph`|—|x|x|x|x|x|x|  
|`_ismbbkalnum`|—|—|—|—|—|x|—|  
|`_ismbbkprint`|—|—|—|—|—|x|x|  
|`_ismbbkpunct`|—|—|—|—|—|—|x|  
|`_ismbbprint`|x|x|x|x|x|x|x|  
|`_ismbbpunct`|—|—|—|x|—|—|x|  
  
 `_ismbb` 例程同时以函数和宏的形式来实现。 若要深入了解如何选择任一实现，请参阅[关于选择函数和宏的建议](../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md)。  
  
## <a name="see-also"></a>另请参阅  
 [字节分类](../c-runtime-library/byte-classification.md)   
 [is、isw 例程](../c-runtime-library/is-isw-routines.md)   
 [_mbbtombc、_mbbtombc_l](../c-runtime-library/reference/mbbtombc-mbbtombc-l.md)   
 [_mbctombb、_mbctombb_l](../c-runtime-library/reference/mbctombb-mbctombb-l.md)
