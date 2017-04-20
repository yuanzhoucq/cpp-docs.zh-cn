---
title: "单字节和多字节字符集 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- c.character.multibyte
dev_langs:
- C++
helpviewer_keywords:
- SBCS (single byte character set)
- MBCS [C++], about MBCS
- character sets [C++], multibyte
- character sets [C++], single byte
ms.assetid: 2cbc78ea-33c0-4cfb-b0df-7ce2458431ce
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: c7d9a62c2b6dc69f9fcd86c8f498e42ce31cae84
ms.lasthandoff: 04/01/2017

---
# <a name="single-byte-and-multibyte-character-sets"></a>单字节和多字节字符集
ASCII 字符集在 0x00 - 0x7F 范围内定义字符。 还有许多其他字符集（主要是欧洲字符集），它们在 0x00 - 0x7F 范围内定义与 ASCII 字符集相同的字符，还在 0x80 - 0xFF. 范围内定义扩展字符集。 因此，8 位的单字节字符集 (`SBCS`) 足以表示 ASCII 字符集以及许多欧洲语言的字符集。 但是，一些非欧洲语言的字符集（如日本汉字）包含的字符数多于单字节编码方案可表示的字符数，因此需要多字节字符集 (`MBCS`) 编码。  
  
> [!NOTE]
>  Microsoft 运行库中的许多 `SBCS` 例程根据需要处理多字节字节、字符和字符串。 许多多字节字符集将 ASCII 字符集定义为子集。 在许多多字节字符集中，0x00 - 0x7F 范围内的每个字符都与 ASCII 字符集中具有相同值的字符相同。 例如，在 `ASCII` 和 `MBCS` 字符串中，单字节 `NULL` 字符（“\0”）的值为 0x00 并指示终止 null 字符。  
  
 多字节字符集可能包括单字节和双字节字符。 因此，多字节字符串可以包含单字节和双字节字符的组合。 两字节多字节字符具有一个前导字节和一个尾字节。 在特定的多字节字符集中，前导字节位于某个范围内，尾字节也是如此。 当这两种范围重叠时，可能需要计算特定上下文以确定某个给定的字节是用作前导字节还是尾字节。  
  
## <a name="see-also"></a>另请参阅  
 [国际化](../c-runtime-library/internationalization.md)   
 [按类别分的运行时例程](../c-runtime-library/run-time-routines-by-category.md)
