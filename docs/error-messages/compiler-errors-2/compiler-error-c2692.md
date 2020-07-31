---
title: 编译器错误 C2692
ms.date: 11/04/2016
f1_keywords:
- C2692
helpviewer_keywords:
- C2692
ms.assetid: 02ade3b4-b757-448b-b065-d7d71bc3f441
ms.openlocfilehash: a82ee0bead9e4e7a92c16df89eee86288f562de9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216097"
---
# <a name="compiler-error-c2692"></a>编译器错误 C2692

"function_name"： C 编译器中具有 "/clr" 选项所需的完全原型的函数

在编译 .NET 托管代码时，C 编译器需要 ANSI 函数声明。 此外，如果函数不采用任何参数，它必须显式声明 **`void`** 为参数类型。
