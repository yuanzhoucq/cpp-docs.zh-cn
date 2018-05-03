---
title: 单字节和多字节字符集 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
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
ms.workload:
- cplusplus
ms.openlocfilehash: 1d6c339f1ab2eecfac5f037e711f19d5ee9323fc
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/20/2018
---
# <a name="single-byte-and-multibyte-character-sets"></a>单字节和多字节字符集

ASCII 字符集在 0x00 - 0x7F 范围内定义字符。 还有许多其他字符集（主要是欧洲字符集），它们在 0x00 - 0x7F 范围内定义与 ASCII 字符集相同的字符，还在 0x80 - 0xFF. 范围内定义扩展字符集。 因此，8 位的单字节字符集 (SBCS) 足以表示 ASCII 字符集以及许多欧洲语言的字符集。 但是，一些非欧洲语言的字符集（如日本汉字）包含的字符数多于单字节编码方案可表示的字符数，因此需要多字节字符集 (MBCS) 编码。

> [!NOTE]
> Microsoft 运行库中的许多 SBCS 例程根据需要处理多字节字节、字符和字符串。 许多多字节字符集将 ASCII 字符集定义为子集。 在许多多字节字符集中，0x00 - 0x7F 范围内的每个字符都与 ASCII 字符集中具有相同值的字符相同。 例如，在 ASCII 和 MBCS 字符串中，单字节 NULL 字符（“\0”）的值为 0x00 并指示终止空字符。

多字节字符集可能包括单字节和双字节字符。 因此，多字节字符串可以包含单字节和双字节字符的组合。 两字节多字节字符具有一个前导字节和一个尾字节。 在特定的多字节字符集中，前导字节位于某个范围内，尾字节也是如此。 当这两种范围重叠时，可能需要计算特定上下文以确定某个给定的字节是用作前导字节还是尾字节。

## <a name="see-also"></a>请参阅

[国际化](../c-runtime-library/internationalization.md)<br/>
[按类别分的通用 C 运行时例程](../c-runtime-library/run-time-routines-by-category.md)<br/>
