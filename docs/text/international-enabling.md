---
title: "国际支持 |Microsoft 文档"
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
- strings [C++], international enabling
- localization [C++], character sets
- MBCS [C++], enabling
- Unicode [C++], enabling
ms.assetid: b077f4ca-5865-40ef-a46e-d9e4d686ef21
caps.latest.revision: "7"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ce0210546dafd354d0d62225c97df8b36a8d84e0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="international-enabling"></a>国际支持
大多数传统的 C 和 c + + 代码作出假设字符和字符串操作适用于国际应用程序不起作用。 MFC 和运行时库支持 Unicode 或 MBCS，而是仍为您进行的工作。 以指导你，本部分介绍 Visual c + + 中的"国际支持"的含义：  
  
-   Unicode 和 MBCS 通过 MFC 函数参数列表中的可移植数据类型，可以启用和返回类型。 在合适的方法，具体取决于你的生成是否定义符号中有条件地定义这些类型**_UNICODE**或符号**_MBCS** （这意味着 DBCS）。 应用程序后，具体取决于这两个符号你的生成定义自动链接 MFC 库的不同变体。  
  
-   类库代码使用可移植运行时函数和其他方法来确保正确的 Unicode 或 MBCS 行为。  
  
-   仍必须在你的代码中处理某些种类的国际化任务：  
  
    -   使用相同的可移植运行时函数，使 MFC 在这两种环境下可移植。  
  
    -   使文本字符串和字符在任一环境，可移植使用**_T**宏。 有关详细信息，请参阅[Tchar.h 中的一般文本映射](../text/generic-text-mappings-in-tchar-h.md)。  
  
    -   分析字符串在 MBCS 下的时，请采取预防措施。 在 Unicode 下不需要这些预防措施。 有关详细信息，请参阅[MBCS 编程提示](../text/mbcs-programming-tips.md)。  
  
    -   注意如果混合应用程序中使用 ANSI （8 位） 和 Unicode （16 位） 字符。 可以使用你的程序的某些部分中的 ANSI 字符和 Unicode 字符，其他情况下，但不是能在相同的字符串中混合使用。  
  
    -   请不要在你的应用程序的硬编码字符串。 相反，使它们 STRINGTABLE 资源通过将其添加到应用程序的.rc 文件。 然后可以而无需源代码更改或重新编译本地化你的应用程序。 STRINGTABLE 资源有关的详细信息，请参阅[字符串编辑器](../windows/string-editor.md)。  
  
> [!NOTE]
>  欧洲和 MBCS 字符集具有一些字符，如重音字母，大于 0x80 字符代码。 由于大多数代码使用有符号的字符，这些字符大于 0x80 是带符号扩展时转换为`int`。 这是对数组索引问题，因为登录扩展的字符为负，则索引将超出数组。 使用 MBCS，如日语语言也是唯一的。 因为字符可能包含 1 或 2 个字节，应始终在同一时间处理两个字节。  
  
## <a name="see-also"></a>请参阅  
 [Unicode 和 MBCS](../text/unicode-and-mbcs.md)   
 [国际化策略](../text/internationalization-strategies.md)