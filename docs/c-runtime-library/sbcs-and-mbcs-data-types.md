---
title: "SBCS 和 MBCS 数据类型 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MBCS
- SBCS
dev_langs:
- C++
helpviewer_keywords:
- SBCS and MBCS data types
- data types [C], MBCS and SBCS
ms.assetid: 4c3ef9da-e397-48d4-800e-49dba36db171
caps.latest.revision: 10
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
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: ac4c3f7273adf9e373484f24fbb7a56ebea5903a
ms.contentlocale: zh-cn
ms.lasthandoff: 05/18/2017

---
# <a name="sbcs-and-mbcs-data-types"></a>SBCS 和 MBCS 数据类型
仅处理一个多字节字符或多字节字符的一个字节的任何 Microsoft `MBCS` 运行库例程需要一个 `unsigned int` 参数（其中 0x00 <= 字符值 <= 0xFFFF，0x00 <= 字节值 <= 0xFF）。 处理字符串上下文中的多字节的字节或字符的 `MBCS` 例程需要一个用 `unsigned char` 指针表示的多字节字符串。  
  
> [!CAUTION]
>  多字节字符的每个字节可用一个 8 位 `char` 表示。 然而，带有大于 0x7F 的值的 `SBCS` 类型的 `MBCS` 或 `char` 单字节字符是负的。 将此类字符直接转换为 `int` 或 `long` 时，结果将由编译器进行符号扩展，因此可能产生意外的结果。  
  
 因此，最好将多字节字符的一个字节表示为一个 8 位 `unsigned char`。 或者，为避免产生负数结果，可在将 `char` 类型的单字节字符转换为 `unsigned char` 或 `int` 之前将其转换为 `long`。  
  
 由于某些 `SBCS` 字符串处理函数采用（带符号的）`char*` 参数，因此定义 `_MBCS` 时，编译器会发出类型不匹配的警告。 可通过三种方法来避免此警告（按效率高低的顺序列出）：  
  
1.  使用 TCHAR.H 中的“类型安全的”内联函数。 这是默认行为。  
  
2.  通过在命令行上定义 `_MB_MAP_DIRECT`，使用 TCHAR.H 中的“直接的”宏。 如果执行此操作，必须手动匹配类型。 这是最快的方法，但不是类型安全的方法。  
  
3.  使用 TCHAR.H 中“类型安全的”静态链接的库函数。 为此，在命令行上定义常量 `_NO_INLINING`。 这是最慢的方法，但是最能确保类型安全。  
  
## <a name="see-also"></a>另请参阅  
 [国际化](../c-runtime-library/internationalization.md)   
 [按类别分的运行时例程](../c-runtime-library/run-time-routines-by-category.md)
