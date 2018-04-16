---
title: "Unicode：宽字符集 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- c.international
dev_langs:
- C++
helpviewer_keywords:
- Unicode [C++], wide character set
- wide characters [C++], Unicode
ms.assetid: b6a05a21-59a5-4d30-8c85-2dbe185f7a74
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 46702f9ea91c9cbba7f7ddbaadc23de88d80fe9c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="unicode-the-wide-character-set"></a>Unicode：宽字符集
宽字符是双字节多语言字符代码。 在现代全球计算业内使用的任意字符（包括技术符号和特殊的发布字符），都可以根据 Unicode 规范表示为宽字符形式。 由包括 Microsoft 在内的大财团开发和维护的 Unicode 标准现在被广泛接受。  
  
 宽字符的类型为 `wchar_t`。 宽字符串表示为一个 `wchar_t[]` 数组，由 `wchar_t*` 指针指向它。 您可以通过在字符前放置字母 `L` 作为前缀来将任何 ASCII 字符表示为宽字符形式。 例如，L'\0' 是终止宽（16 位）`NULL` 字符。 同样，您可以通过在 ASCII 文本前放置字母 L 作为前缀 (L"Hello") 来将任何 ASCII 字符串文本表示为宽字符串文本形式。  
  
 通常，宽字符在内存中占用的空间比多字节字符多，但处理速度更快。 另外，在多字节编码中一次只能表示一个区域设置，而世界上的所有字符集可以同时以 Unicode 表示形式表示。  
  
## <a name="see-also"></a>请参阅  
 [国际化](../c-runtime-library/internationalization.md)   
 [按类别分的运行时例程](../c-runtime-library/run-time-routines-by-category.md)