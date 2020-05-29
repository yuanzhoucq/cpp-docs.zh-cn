---
title: 错误 C1026
ms.date: 11/04/2016
f1_keywords:
- C1026
helpviewer_keywords:
- C1026
ms.assetid: 89bb9d40-673a-44aa-a9f4-b42c07b49d44
ms.openlocfilehash: a7c7a5da01c8b4a44c307a00f53530acb12a8009
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80204648"
---
# <a name="fatal-error-c1026"></a>错误 C1026

分析器堆栈溢出，程序太复杂

分析程序所需的空间导致了编译器堆栈溢出。

降低表达式的复杂性：

- 减小 `for` 和 `switch` 语句中的嵌套。 将更深层嵌套的语句置于单独的函数中。

- 分解涉及逗号运算符或函数调用的长表达式。
