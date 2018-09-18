---
title: 错误 C1026 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1026
dev_langs:
- C++
helpviewer_keywords:
- C1026
ms.assetid: 89bb9d40-673a-44aa-a9f4-b42c07b49d44
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: db9167383df48dad274ef8941defaa53f51d3bfa
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46068983"
---
# <a name="fatal-error-c1026"></a>错误 C1026

分析器堆栈溢出，程序太复杂

分析程序所需的空间导致编译器堆栈溢出。

降低所表达式的复杂程度：

- 减少中的嵌套`for`和`switch`语句。 将更深的嵌套语句放在单独的函数。

- 分解长涉及逗号运算符或函数调用的表达式。