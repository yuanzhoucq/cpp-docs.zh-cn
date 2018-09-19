---
title: 浮点值的截断 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- floating-point numbers, truncation
ms.assetid: 051a6e22-c636-4af8-9ac4-40160f4affca
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b30700b52e7cbbbc295d6050b03283b4b45a0b08
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46103810"
---
# <a name="truncation-of-floating-point-values"></a>浮点值的截断

**ANSI 3.2.1.4** 在某个浮点数转换为较小的浮点数时截断或舍入的方向

当出现下溢时，浮点变量的值将向下舍入为 0。 溢出可能导致运行时错误，也可能生成不可预知的值，具体取决于指定的优化。

## <a name="see-also"></a>请参阅

[浮点数学](../c-language/floating-point-math.md)