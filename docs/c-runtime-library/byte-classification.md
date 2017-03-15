---
title: "字节分类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.types.bytes"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "字节分类例程"
  - "字节, 测试"
  - "代码页 932"
ms.assetid: 1cb52d71-fb0c-46ca-aad7-6472c1103370
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# 字节分类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

这些例程每个测试的多字节字符的指定字节条件的满意度。  把指向其他地方的除外，输出值受区域设置的 `LC_CTYPE` 类设置影响；有关更多信息，请参见 [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)。  这些不带 `_l` 后缀的函数的版本使用为该区域设置相关的行为的当前区域设置；带有 `_l` 后缀的版本相同，只不过它们使用传递的区域设置参数。  
  
> [!NOTE]
>  按照定义，在0到127之间的ASCII字符是所有多字节字符集的子集。  例如，日文片假名包含 ASCII 字符集以及非 ASCII 字符。  
  
 下表中的预定义常数在CTYPE.H中被定义。  
  
### 多字节 字节类目程序  
  
|例程|字节测试条件|.NET Framework 等效项|  
|--------|------------|------------------------|  
|[isleadbyte、\_isleadbyte\_l](../c-runtime-library/reference/isleadbyte-isleadbyte-l.md)|前导字节；测试结果取决于 `LC_CTYPE` 当前区域设置设置类别|不适用，就请参见[System::Globalization::CultureInfo](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo.aspx)。|  
|[\_ismbbalnum、\_ismbbalnum\_l](../c-runtime-library/reference/ismbbalnum-ismbbalnum-l.md)|`isalnum &#124;&#124; _ismbbkalnum`|不适用，就请参见[System::Globalization::CultureInfo](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo.aspx)。|  
|[\_ismbbalpha、\_ismbbalpha\_l](../c-runtime-library/reference/ismbbalpha-ismbbalpha-l.md)|`isalpha &#124;&#124; _ismbbkalnum`|不适用，就请参见[System::Globalization::CultureInfo](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo.aspx)。|  
|[\_ismbbgraph、\_ismbbgraph\_l](../c-runtime-library/reference/ismbbgraph-ismbbgraph-l.md)|和`_ismbbprint`相同，但是，`_ismbbgraph` 不包含空格 \(0x20\)。|不适用，就请参见[System::Globalization::CultureInfo](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo.aspx)。|  
|[\_ismbbkalnum、\_ismbbkalnum\_l](../c-runtime-library/reference/ismbbkalnum-ismbbkalnum-l.md)|非 ASCII 的文本符号\(除了标点外\)。  例如，仅在代码页 932 ，`_ismbbkalnum` 测试片假名的字母数字。|不适用，就请参见[System::Globalization::CultureInfo](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo.aspx)。|  
|[\_ismbbkana、\_ismbbkana\_l](../c-runtime-library/reference/ismbbkana-ismbbkana-l.md)|片假名 \(0xA1 – 0xDF\), ，仅在代码页932|不适用，就请参见[System::Globalization::CultureInfo](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo.aspx)。|  
|[\_ismbbkprint、\_ismbbkprint\_l](../c-runtime-library/reference/ismbbkprint-ismbbkprint-l.md)|非 ASCII 文本或非 ASCII 标点符号。  例如，仅在代码页 932 ，`_ismbbkprint` 测试片假名字母数字或片假名标点 \(范围：0xA1 – 0xDF\)。|不适用，就请参见[System::Globalization::CultureInfo](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo.aspx)。|  
|[\_ismbbkpunct、\_ismbbkpunct\_l](../c-runtime-library/reference/ismbbkpunct-ismbbkpunct-l.md)|非 ASCII 标点。  例如，仅在代码页 932 ，`_ismbbkpunct` 测试的标点片假名。|不适用，就请参见[System::Globalization::CultureInfo](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo.aspx)。|  
|[\_ismbblead、\_ismbblead\_l](../c-runtime-library/reference/ismbblead-ismbblead-l.md)|多字节字符的第一个字节。  例如，仅在代码页 932 ，有效范围是 0x81 – 0x9F，0xE0 – 0xFC。|不适用，就请参见[System::Globalization::CultureInfo](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo.aspx)。|  
|[\_ismbbprint、\_ismbbprint\_l](../c-runtime-library/reference/ismbbprint-ismbbprint-l.md)|`isprint &#124;&#124; _ismbbkprint. ismbbprint` \(0x20\) 包含空白字符|不适用，就请参见[System::Globalization::CultureInfo](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo.aspx)。|  
|[\_ismbbpunct、\_ismbbpunct\_l](../c-runtime-library/reference/ismbbpunct-ismbbpunct-l.md)|`ispunct &#124;&#124; _ismbbkpunct`|不适用，就请参见[System::Globalization::CultureInfo](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo.aspx)。|  
|[\_ismbbtrail、\_ismbbtrail\_l](../c-runtime-library/reference/ismbbtrail-ismbbtrail-l.md)|多字节字符的第二个字节。  例如，仅在代码页 932 ，有效范围是 0x40 – 0x7E，0x80 – 0xEC。|不适用，就请参见[System::Globalization::CultureInfo](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo.aspx)。|  
|[\_ismbslead，\_ismbslead\_l](../c-runtime-library/reference/ismbslead-ismbstrail-ismbslead-l-ismbstrail-l.md)|前导字节 \(在字符串上下文\)|不适用，就请参见[System::Globalization::CultureInfo](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo.aspx)。|  
|[ismbstrail，\_ismbstrail\_l](../c-runtime-library/reference/ismbslead-ismbstrail-ismbslead-l-ismbstrail-l.md)|尾字节 \(在字符串上下文\)|不适用，就请参见[System::Globalization::CultureInfo](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo.aspx)。|  
|[\_mbbtype、\_mbbtype\_l](../c-runtime-library/reference/mbbtype-mbbtype-l.md)|根据以前字节字节的返回类型|不适用，就请参见[System::Globalization::CultureInfo](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo.aspx)。|  
|[\_mbsbtype、\_mbsbtype\_l](../c-runtime-library/reference/mbsbtype-mbsbtype-l.md)|字节的返回类型在字符串中|不适用，就请参见[System::Globalization::CultureInfo](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo.aspx)。|  
|[mbsinit](../c-runtime-library/reference/mbsinit.md)|跟踪多字节字符转换的状态。|不适用，就请参见[System::Globalization::CultureInfo](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo.aspx)。|  
  
 `MB_LEN_MAX` 宏，所以定义在 LIMITS.H，则所有多字节字符可以包含的字节扩充到最大长度。  `MB_CUR_MAX`，在 STDLIB.H 定义，以字节为扩充到最大长度所有多字节字符在当前区域设置。  
  
## 请参阅  
 [按类别分的运行时例程](../c-runtime-library/run-time-routines-by-category.md)