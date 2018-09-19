---
title: 编译器警告 （等级 C4629 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4629
dev_langs:
- C++
helpviewer_keywords:
- C4629
ms.assetid: 158cde12-bae5-4d43-b575-b52b35aaa0b9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e5f728d60a654a672002610d41aa4e387b4479e0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46081309"
---
# <a name="compiler-warning-level-4-c4629"></a>编译器警告（等级 4）C4629

使用了有向图，字符序列“digraph”解释为标记“char”（如果这不是你想要的，请在这两个字符之间插入一个空格）

在 [/Za](../../build/reference/za-ze-disable-language-extensions.md)下，当编译器检测到有向图时会发出警告。

以下示例生成 C4629：

```
// C4629.cpp
// compile with: /Za /W4
int main()
<%   // C4629 <% digraph for {
}
```