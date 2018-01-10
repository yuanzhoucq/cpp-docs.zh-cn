---
title: "文本和字符串在 Visual c + + |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "12"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a911b3a4547be409047004969043943b54bb2480
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="text-and-strings-in-visual-c"></a>Visual C++ 中的文本和字符串
开发国际市场的应用程序的一个重要方面是适当地表示的本地字符集。 ASCII 字符集在 0x00 到 0x7F 范围内定义字符。 有其他字符集，主要是欧洲字符集，于 ASCII 字符集相同定义中的范围 0x00 到 0x7F 的字符和还定义为扩展的字符设置为从 0x80 到 0xFF。 因此，一个 8 位、 单字节字符的集 (SBCS) 足以表示 ASCII 字符集，以及许多欧洲语言的字符集。 但是，一些非欧洲字符集，如日本汉字包括许多更多的字符不是单字节编码方案可以表示，并因此需要多字节字符集 (MBCS) 编码。  
  
## <a name="in-this-section"></a>本节内容  
 [Unicode 和 MBCS](../text/unicode-and-mbcs.md)  
 讨论为 Unicode 和 MBCS 编程的 Visual c + + 支持。  
  
 [支持 Unicode](../text/support-for-unicode.md)  
 描述 Unicode，它支持所有字符集，包括字符不能表示单字节的规范。  
  
 [多字节字符集 (MBCS) 的支持](../text/support-for-multibyte-character-sets-mbcss.md)  
 讨论 MBCS，以支持字符集，如日语和中文，不能表示单字节 Unicode 的替代方法。  
  
 [Tchar.h 中的一般文本映射](../text/generic-text-mappings-in-tchar-h.md)  
 提供多种数据类型、 例程和其他对象的特定于 Microsoft 的一般文本映射。  
  
 [如何：在各种字符串类型之间进行转换](../text/how-to-convert-between-various-string-types.md)  
 演示如何将各种 Visual c + + 字符串类型转换为其他字符串。  
  
## <a name="related-sections"></a>相关章节  
 [国际化](../c-runtime-library/internationalization.md)  
 讨论 C 运行时库中的国际支持。  
  
 [国际示例](http://msdn.microsoft.com/en-us/aa8d390c-cf4c-4dd8-9dea-74d81f93f2f8)  
 提供指向演示 Visual c + + 中的国际化的示例。  
  
 [语言和国家/地区字符串](../c-runtime-library/locale-names-languages-and-country-region-strings.md)  
 提供的 C 运行时库中的语言和国家/地区字符串。