---
title: ANSI 一致性 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- ANSI [C++]
- ANSI [C++], C standard
ms.assetid: c3a188c8-42bc-41fb-a78d-637f3175ade0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cca68ad9865ab6382114c3ebe64d5921539f7ce0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46106867"
---
# <a name="ansi-conformance"></a>ANSI 一致性

Microsoft C 遵循在 ANSI C 标准的 9899:1990 版本中规定的 C 语言的标准。

本书的文本和语法中以及联机引用中介绍了 Microsoft ANSI C 标准扩展。 由于此扩展不是 ANSI C 标准的一部分，因此对它们的使用可能会限制系统间程序的可移植性。 默认情况下，将启用 Microsoft 扩展。 若要禁用此扩展，请指定 /Za 编译器选项。 使用 /Za，所有非 ANSI 代码将生成错误或警告。

## <a name="see-also"></a>请参阅

[《C 语言参考》的组织](../c-language/organization-of-the-c-language-reference.md)