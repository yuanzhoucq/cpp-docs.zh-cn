---
title: MBCS 编程提示 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- _mbcs
dev_langs:
- C++
helpviewer_keywords:
- programming [C++], MBCS
- character sets [C++], multibyte
- MBCS [C++], programming
- multibyte characters [C++]
ms.assetid: d8ad36b8-917f-474e-8adb-69462adecd17
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ac4ed378640942dbe33490d618cec7289125b0c8
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46418783"
---
# <a name="mbcs-programming-tips"></a>MBCS 编程提示

在新开发中，您应该为最终用户可能看到的所有字符串使用 Unicode 字符编码。 MBCS 是已经被 Unicode 取代的旧技术。 本节为必须维护使用 MBCS 的现有程序的开发人员提供了一些提示，以及有关不适合转换为 Unicode 的情况的提示。 建议适用于 MFC 应用程序和如果不使用 MFC 编写的应用程序。 包括以下主题：

- [常规 MBCS 编程建议](../text/general-mbcs-programming-advice.md)

- [递增和递减指针](../text/incrementing-and-decrementing-pointers.md)

- [字节索引](../text/byte-indices.md)

- [字符串中的最后一个字符](../text/last-character-in-a-string.md)

- [字符赋值](../text/character-assignment.md)

- [字符比较](../text/character-comparison.md)

- [缓冲区溢出](../text/buffer-overflow.md)

## <a name="see-also"></a>请参阅

[支持多字节字符集 (MBCS)](../text/support-for-multibyte-character-sets-mbcss.md)