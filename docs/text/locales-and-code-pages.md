---
title: 区域设置和代码页 |Microsoft 文档
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
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b1c7dd3c5356df7b80f21605e325158e87cc5a71
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33858141"
---
# <a name="locales-and-code-pages"></a>区域设置和代码页
将区域设置 ID 反映本地的约定和语言特定的地理区域。 可能有一个以上的国家/地区说某种特定的语言，例如，巴西和葡萄牙都说葡萄牙语。 反之，一个国家/地区可能有一种以上的官方语言。 例如，加拿大有两种语言： 英语和法语。 因此，加拿大有两个不同的区域设置： 加拿大英语和加拿大法语。 一些与区域设置相关的类别包括日期的格式设置和货币值的显示格式。  
  
 语言确定文本和数据的格式约定，而国家/地区则确定本地约定。 每种语言具有的唯一映射，表示由代码页，其中包括之外 （如标点符号和数字） 字母表中的字符。 一个代码页是一个字符集，并且与语言相关。 在这种情况下，[区域设置](../c-runtime-library/locale.md)就成为语言、 国家/地区和代码页的唯一组合。 通过调用，可在运行时更改区域设置和代码页设置[setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)函数。  
  
 不同语言可能使用不同的代码页。 例如，ANSI 代码页 1252年适用于英语和大多数欧洲语言，并且 ANSI 代码页 932 适用于日本汉字。 几乎所有的代码页共享 ASCII 字符集为最低 128 个字符 (0x00 到 0x7F)。  
  
 任何单字节代码页可以用来表示 （具有 256 项） 的表到字符 （包括数字和标点符号） 或标志符号的字节值的映射。 任何多字节代码页，也可以表示为一个非常大表 （64k) 的双字节字符的值。 在实践中，但是，它通常表示作为表以获取前 256 个 （单字节） 字符和双字节值的范围。  
  
 有关代码页的详细信息，请参见 [Code Pages](../c-runtime-library/code-pages.md)。  
  
 C 运行时库有两种类型的内部代码页： 区域设置和多字节。 你可以在程序执行期间更改的当前代码页 (请参阅的文档[setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)和[_setmbcp](../c-runtime-library/reference/setmbcp.md)函数)。 此外，运行时库可能获取并使用操作系统代码页，可为程序的执行持续时间内的常数的值。  
  
 区域设置代码页更改时，区域设置相关的更改集的函数为由选定的代码页的行为。 默认情况下，所有依赖于区域设置函数开始执行与唯一的"C"区域设置的区域设置代码页。 你可以更改内部的区域设置代码页 （以及其他区域设置特定的属性） 通过调用`setlocale`函数。 调用`setlocale`(LC_ALL，"") 区域设置设定为，指示由操作系统用户区域设置。  
  
 同样，更改多字节代码页时，多字节函数更改为由选定的代码页的行为。 默认情况下，所有的多字节函数使用对应于操作系统的默认代码页多字节代码页开始执行。 你可以通过调用来更改内部的多字节代码页`_setmbcp`函数。  
  
 C 运行时函数`setlocale`设置、 更改或查询部分或全部当前程序区域设置信息。 [_Wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)例程是宽字符版本的`setlocale`; 的自变量和返回值`_wsetlocale`是宽字符字符串。  
  
## <a name="see-also"></a>请参阅  
 [Unicode 和 MBCS](../text/unicode-and-mbcs.md)   
 [字符集可迁移性的好处](../text/benefits-of-character-set-portability.md)