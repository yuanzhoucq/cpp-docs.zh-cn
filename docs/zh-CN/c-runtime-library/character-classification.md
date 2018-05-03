---
title: 字符分类 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- c.types.character
dev_langs:
- C++
helpviewer_keywords:
- character classification routines
- characters, testing
ms.assetid: 3b6c8f0b-9701-407a-b384-9086698773f5
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 40cc501e89b12b2d2c13f5e64d9e6bf8a6bc4a13
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/20/2018
---
# <a name="character-classification"></a>字符分类

其中的每个例程均针对条件满意度测试指定的单字节字符、宽字符或多字节字符。 （根据定义，0 和 127 之间的 ASCII 字符集是所有多字节字符集的子集。 例如，日语的片假名包括 ASCII 以及非 ASCII 字符。）

 测试条件受区域设置的 LC_CTYPE 类别设置影响；有关详细信息，请参阅 [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)。 这些不带 **_l** 后缀的函数版本使用此区域设置相关的行为的当前区域设置；带有 **_l** 后缀的版本相同，只不过它们使用传递的区域设置参数。

 与你可能编写的测试相比，这些例程的执行速度通常更快，因此应优先考虑。 例如，以下代码执行速度慢于调用 `isalpha(c)`：

```C
if ((c >= 'A') && (c <= 'Z')) || ((c >= 'a') && (c <= 'z'))
    return TRUE;
```

## <a name="character-classification-routines"></a>字符分类例程

|例程所返回的值|字符测试条件|
|-------------|------------------------------|
|[isalnum、iswalnum、_isalnum_l、_iswalnum_l](../c-runtime-library/reference/isalnum-iswalnum-isalnum-l-iswalnum-l.md)、[isalnum、iswalnum、_isalnum_l、_iswalnum_l](../c-runtime-library/reference/ismbcalnum-functions.md)|字母数字|
|[_ismbcalnum、_ismbcalnum_l、_ismbcalpha、_ismbcalpha_l、_ismbcdigit、_ismbcdigit_l](../c-runtime-library/reference/ismbcalnum-functions.md)|字母数字|
|[isalpha、iswalpha、_isalpha_l、_iswalpha_l](../c-runtime-library/reference/isalpha-iswalpha-isalpha-l-iswalpha-l.md)、[isalnum、iswalnum、_isalnum_l、_iswalnum_l](../c-runtime-library/reference/ismbcalnum-functions.md)|Alphabetic|
|[isascii、__isascii、iswascii](../c-runtime-library/reference/isascii-isascii-iswascii.md)|ASCII|
|[isblank、iswblank、_isblank_l、_iswblank_l](../c-runtime-library/reference/isblank-iswblank-isblank-l-iswblank-l.md)、[_ismbcsblank、_ismbcsblank_l](../c-runtime-library/reference/ismbcgraph-functions.md)|空白（空格或水平制表符）|
|[iscntrl、iswcntrl、_iscntrl_l、_iswcntrl_l](../c-runtime-library/reference/iscntrl-iswcntrl-iscntrl-l-iswcntrl-l.md)|控件|
|[iscsym、iscsymf、__iscsym、\___iswcsym、\___iscsymf、\___iswcsymf、_iscsym_l、_iswcsym_l、_iscsymf_l、_iswcsymf_l](../c-runtime-library/reference/iscsym-functions.md)|字母、下划线或数字|
|[iscsym、iscsymf、__iscsym、\___iswcsym、\___iscsymf、\___iswcsymf、_iscsym_l、_iswcsym_l、_iscsymf_l、_iswcsymf_l](../c-runtime-library/reference/iscsym-functions.md)|字母或下划线|
|[isdigit、iswdigit、_isdigit_l、_iswdigit_l](../c-runtime-library/reference/isdigit-iswdigit-isdigit-l-iswdigit-l.md)、[isalnum、iswalnum、_isalnum_l、_iswalnum_l](../c-runtime-library/reference/ismbcalnum-functions.md)|十进制数字|
|[isgraph、iswgraph、_isgraph_l、_iswgraph_l](../c-runtime-library/reference/isgraph-iswgraph-isgraph-l-iswgraph-l.md)、[_ismbcgraph、_ismbcgraph_l、_ismbcprint、_ismbcprint_l、_ismbcpunct、_ismbcpunct_l、_ismbcblank、_ismbcblank_l、_ismbcspace、_ismbcspace_l](../c-runtime-library/reference/ismbcgraph-functions.md)|可打印（空格除外）|
|[islower、iswlower、_islower_l、_iswlower_l](../c-runtime-library/reference/islower-iswlower-islower-l-iswlower-l.md)、[_ismbclower、_ismbclower_l、_ismbcupper、_ismbcupper_l](../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|小写|
|[_ismbchira、_ismbchira_l、_ismbckata、_ismbckata_l](../c-runtime-library/reference/ismbchira-ismbchira-l-ismbckata-ismbckata-l.md)|平假名|
|[_ismbchira、_ismbchira_l、_ismbckata、_ismbckata_l](../c-runtime-library/reference/ismbchira-ismbchira-l-ismbckata-ismbckata-l.md)|片假名|
|[_ismbclegal、_ismbclegal_l、_ismbcsymbol、_ismbcsymbol_l](../c-runtime-library/reference/ismbclegal-ismbclegal-l-ismbcsymbol-ismbcsymbol-l.md)|有效的多字节字符|
|[_ismbcl0、_ismbcl0_l、_ismbcl1、_ismbcl1_l、_ismbcl2、_ismbcl2_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|日本 0 级多字节字符|
|[_ismbcl0、_ismbcl0_l、_ismbcl1、_ismbcl1_l、_ismbcl2、_ismbcl2_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|日本 1 级多字节字符|
|[_ismbcl0、_ismbcl0_l、_ismbcl1、_ismbcl1_l、_ismbcl2、_ismbcl2_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|日本 2 级多字节字符|
|[_ismbclegal、_ismbclegal_l、_ismbcsymbol、_ismbcsymbol_l](../c-runtime-library/reference/ismbclegal-ismbclegal-l-ismbcsymbol-ismbcsymbol-l.md)|非字母数字的多字节字符|
|[isprint、iswprint、_isprint_l、_iswprint_l](../c-runtime-library/reference/isprint-iswprint-isprint-l-iswprint-l.md)、[_ismbcgraph、_ismbcgraph_l、_ismbcprint、_ismbcprint_l、_ismbcpunct、_ismbcpunct_l、_ismbcblank、_ismbcblank_l、_ismbcspace、_ismbcspace_l](../c-runtime-library/reference/ismbcgraph-functions.md)|可打印|
|[ispunct、iswpunct、_ispunct_l、_iswpunct_l](../c-runtime-library/reference/ispunct-iswpunct-ispunct-l-iswpunct-l.md)、[_ismbcgraph、_ismbcgraph_l、_ismbcprint、_ismbcprint_l、_ismbcpunct、_ismbcpunct_l、_ismbcblank、_ismbcblank_l、_ismbcspace、_ismbcspace_l](../c-runtime-library/reference/ismbcgraph-functions.md)|标点|[System::Char::IsPunctuation](https://msdn.microsoft.com/en-us/library/system.char.ispunctuation.aspx)|
|[isspace、iswspace、_isspace_l、_iswspace_l](../c-runtime-library/reference/isspace-iswspace-isspace-l-iswspace-l.md)、[_ismbcgraph、_ismbcgraph_l、_ismbcprint、_ismbcprint_l、_ismbcpunct、_ismbcpunct_l、_ismbcblank、_ismbcblank_l、_ismbcspace、_ismbcspace_l](../c-runtime-library/reference/ismbcgraph-functions.md)|空格|[System::Char::IsWhiteSpace](https://msdn.microsoft.com/en-us/library/system.char.iswhitespace.aspx)|
|[Isupper、iswupper](../c-runtime-library/reference/isupper-isupper-l-iswupper-iswupper-l.md), [_ismbclower、_ismbclower_l、_ismbcupper、_ismbcupper_l](../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|大写|
|[_isctype、iswctype、_isctype_l、_iswctype_l](../c-runtime-library/reference/isctype-iswctype-isctype-l-iswctype-l.md)|desc 参数指定的属性|
|[isxdigit、iswxdigit、_isxdigit_l、_iswxdigit_l](../c-runtime-library/reference/isxdigit-iswxdigit-isxdigit-l-iswxdigit-l.md)|十六进制数|
|[_mbclen、mblen、_mblen_l](../c-runtime-library/reference/mbclen-mblen-mblen-l.md)|返回有效的多字节字符的长度；结果取决于当前区域设置的 LC_CTYPE 类别设置|

## <a name="see-also"></a>请参阅

[按类别分的通用 C 运行时例程](../c-runtime-library/run-time-routines-by-category.md)<br/>