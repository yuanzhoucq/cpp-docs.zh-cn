---
title: 文本和字符串在 Visual c + + |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- globalization [C++], character sets
- programming [C++], international
- multiple language support [C++]
- Unicode [C++]
- international applications [C++], about international applications
- portability [C++]
- translation [C++], character sets
- non-European characters [C++]
- character sets [C++]
- globalization [C++]
- Japanese characters [C++]
- Kanji character support [C++]
- local character sets [C++]
- ASCII characters [C++]
- character sets [C++], about character sets
- localization [C++], character sets
- translating code [C++]
- localization [C++]
- character sets [C++], non-European
- portability [C++], character sets
- MBCS [C++], international programming
ms.assetid: a1bb27ac-abe5-4c6b-867d-f761d4b93205
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cf9133965a9009421c28f64c1f4157b4a6a6d6b3
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43223290"
---
# <a name="text-and-strings-in-visual-c"></a>Visual C++ 中的文本和字符串
开发适用于国际市场的应用程序的一个重要方面是足够有代表性的本地字符集。 ASCII 字符集在 0x00 到 0x7F 范围内定义字符。 有其他字符集，主要是欧洲的相同定义 0x00 到 0x7F 范围内的字符到 ASCII 字符集，还可定义一个设置为从 0x80 到 0xFF 的扩展的字符。 因此，一个 8 位的单字节字符的集 (SBCS) 足以表示 ASCII 字符集以及许多欧洲语言的字符集。 但是，一些非欧洲语言的字符集，如日本汉字包括很多更多的字符不是单字节编码方案可表示，，因此需要使用多字节字符集 (MBCS) 编码。  
  
## <a name="in-this-section"></a>本节内容  
 [Unicode 和 MBCS](../text/unicode-and-mbcs.md)  
 讨论对 Unicode 和 MBCS 编程的 Visual c + + 支持。  
  
 [支持 Unicode](../text/support-for-unicode.md)  
 介绍 Unicode，支持所有字符集，包括字符不能表示单字节的规范。  
  
 [对多字节字符集 (MBCS) 的支持](../text/support-for-multibyte-character-sets-mbcss.md)  
 讨论 MBCS 到 Unicode 支持的字符集，如日语和中文，不能以单个字节表示的替代方法。  
  
 [Tchar.h 中的一般文本映射](../text/generic-text-mappings-in-tchar-h.md)  
 为多种数据类型、 例程和其他对象提供特定于 Microsoft 的一般文本映射。  
  
 [如何：在各种字符串类型之间进行转换](../text/how-to-convert-between-various-string-types.md)  
 演示如何将各种 Visual c + + 字符串类型转换为其他字符串。  
  
## <a name="related-sections"></a>相关章节  
 [国际化](../c-runtime-library/internationalization.md)  
 讨论 C 运行时库中的国际支持。  
  
 [国际示例](https://msdn.microsoft.com/aa8d390c-cf4c-4dd8-9dea-74d81f93f2f8)  
 提供指向演示 Visual c + + 中的国际化示例。  
  
 [语言和国家/地区字符串](../c-runtime-library/locale-names-languages-and-country-region-strings.md)  
 提供了 C 运行时库中的语言和国家/地区字符串。