---
title: 错误 C1026
ms.date: 11/04/2016
f1_keywords:
- C1026
helpviewer_keywords:
- C1026
ms.assetid: 89bb9d40-673a-44aa-a9f4-b42c07b49d44
ms.openlocfilehash: b1a659967a9a62cb79e1084f7d1fa1729bae14da
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50666168"
---
# <a name="fatal-error-c1026"></a>错误 C1026

分析器堆栈溢出，程序太复杂

分析程序所需的空间导致编译器堆栈溢出。

降低所表达式的复杂程度：

- 减少中的嵌套`for`和`switch`语句。 将更深的嵌套语句放在单独的函数。

- 分解长涉及逗号运算符或函数调用的表达式。