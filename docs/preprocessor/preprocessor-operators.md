---
title: 预处理器运算符
ms.date: 08/29/2019
helpviewer_keywords:
- preprocessor operators
- operators [C++], preprocessor
ms.assetid: 884126d1-0ce2-48b6-9e06-8a2d7c4a9656
ms.openlocfilehash: 5dd252fb495a05efe6eef45674f9ecd601a298a7
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857939"
---
# <a name="preprocessor-operators"></a>预处理器运算符

在 `#define` 指令的上下文中使用四个预处理器特定运算符。 请参阅下表了解每个。 接下来的三个部分讨论了字符串化、charizing 和标记粘贴运算符。 有关 `defined` 运算符的信息，请参阅[#if、#elif、#else 和 #endif 指令](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)。

|运算符|操作|
|--------------|------------|
|[字符串化运算符（#）](../preprocessor/stringizing-operator-hash.md)|导致将相应的实参括在双引号中|
|[Charizing 运算符（# @）](../preprocessor/charizing-operator-hash-at.md)|使相应的参数括在单引号中，并被视为一个字符（Microsoft 特定）|
|[标记粘贴运算符（# #）](../preprocessor/token-pasting-operator-hash-hash.md)|允许用于连接到其他标记的实参的标记|
|[定义的运算符](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|简化某些宏指令中的复合表达式的编写|

## <a name="see-also"></a>另请参阅

[预处理器指令](../preprocessor/preprocessor-directives.md)\
[预定义的宏](../preprocessor/predefined-macros.md)\
[c/c + + 预处理器参考](../preprocessor/c-cpp-preprocessor-reference.md)
