---
title: 区域设置和代码页 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- locales [C++], about locales
- locale IDs [C++]
- locales [C++]
- code pages [C++]
- code pages [C++], dynamically changing
- character sets [C++], code pages
- multibyte code pages [C++]
- character sets [C++], locales
- localization [C++], code pages
- localization [C++], locales
- code pages [C++], locales
- conventions [C++], international character support
ms.assetid: bd937361-b6d3-4c98-af95-beb7c903187b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9952f0bf27202c468e38ff3fb6aa701a0d6f9163
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42594834"
---
# <a name="locales-and-code-pages"></a>区域设置和代码页
区域设置 ID 反映了本地约定和特定地理区域的语言。 可能有一个以上的国家/地区说某种特定的语言，例如，巴西和葡萄牙都说葡萄牙语。 反之，一个国家/地区可能有一种以上的官方语言。 例如，加拿大有两种语言： 英语和法语。 因此，加拿大有两种不同的区域设置： 加拿大英语和加拿大法语。 一些与区域设置相关的类别包括日期的格式设置和货币值的显示格式。  
  
 语言确定文本和数据的格式约定，而国家/地区则确定本地约定。 每种语言具有唯一的映射，由代码页，其中包括在字母表中 （例如标点符号和数字） 字符。 代码页是一个字符集和与语言相关。 在这种情况下，[区域设置](../c-runtime-library/locale.md)是唯一的语言、 国家/地区和代码页。 通过调用，可在运行时更改区域设置和代码页设置[setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)函数。  
  
 不同的语言可能使用不同的代码页。 例如，适用于英语和大多数欧洲语言中，使用 ANSI 代码页 1252年和适用于日本汉字使用 ANSI 代码页 932。 几乎所有代码页都共享 ASCII 字符集的最小 128 个字符 (0x00 到 0x7F)。  
  
 可以在表 （带 256 条目） 中表示任何单字节代码页，为到字符 （包括数字和标点符号） 或标志符号的字节值的映射。 也可以作为双字节值与字符的非常大 （有 64k 项） 表表示任何多字节代码页。 在实践中，但是，它通常表示作为表的前 256 个 （单字节） 字符和双字节值的范围。  
  
 有关代码页的详细信息，请参见 [Code Pages](../c-runtime-library/code-pages.md)。  
  
 C 运行时库有两种类型的内部代码页： 区域设置和多字节。 可以在程序执行期间更改当前代码页 (请参阅的文档[setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)并[_setmbcp](../c-runtime-library/reference/setmbcp.md)函数)。 此外，运行时库可能会获取和使用的操作系统代码页上，该程序的执行持续时间是常量值。  
  
 区域设置代码页发生更改时，函数更改为由所选的代码页的区域设置相关集的行为。 默认情况下，所有依赖于区域设置的函数开始执行使用唯一的"C"区域设置的区域设置代码页。 可以通过调用更改内部的区域设置代码页 （以及其他特定于区域设置的属性）`setlocale`函数。 调用`setlocale`(LC_ALL，"") 将区域设置设置为指示的操作系统用户区域设置。  
  
 同样，多字节代码页发生更改时，为由所选的代码页的多字节函数更改的行为。 默认情况下，多字节的所有函数都开始执行过程与为操作系统的默认代码页对应的多字节代码页。 可以通过调用更改内部的多字节代码页`_setmbcp`函数。  
  
 C 运行时函数`setlocale`设置、 更改或查询部分或全部当前程序区域设置信息。 [_Wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)例程是宽字符版本`setlocale`; 的参数和返回值`_wsetlocale`都是宽字符字符串。  
  
## <a name="see-also"></a>请参阅  
 [Unicode 和 MBCS](../text/unicode-and-mbcs.md)   
 [字符集可迁移性的好处](../text/benefits-of-character-set-portability.md)