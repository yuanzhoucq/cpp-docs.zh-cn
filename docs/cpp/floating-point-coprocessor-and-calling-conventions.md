---
title: 浮点协处理器和调用约定
ms.date: 11/04/2016
helpviewer_keywords:
- floating-point numbers [C++]
- floating-point coprocessor
ms.assetid: 3cc6615a-b308-4cf7-9570-83e192a832b3
ms.openlocfilehash: 09358ee36da7e5a86c214789fa7fd0687e9b8825
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231190"
---
# <a name="floating-point-coprocessor-and-calling-conventions"></a>浮点协处理器和调用约定

如果要为浮点协处理器编写程序集例程，则必须保留浮点控制字并清理协处理器堆栈，除非返回 **`float`** 或 **`double`** 值（函数应在 ST （0）中返回）。

## <a name="see-also"></a>请参阅

[调用约定](../cpp/calling-conventions.md)
