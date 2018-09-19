---
title: 编译器警告 （等级 1） C4216 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4216
dev_langs:
- C++
helpviewer_keywords:
- C4216
ms.assetid: 211079dc-59d0-42a7-801c-2ddab21d7232
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d6f9e53115b7b162fa4c36ad9a3fa227de777bf8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46042983"
---
# <a name="compiler-warning-level-1-c4216"></a>编译器警告（等级 1）C4216

使用了非标准扩展： 长浮点

默认 Microsoft 扩展 (/Ze) 将视为**长浮点**作为**double**。 ANSI 兼容性 ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) 却没有。 使用**double**以保持兼容性。 下面的示例生成 C4216:

```
// C4216.cpp
// compile with: /W1
float long a;   // C4216

// use the line below to resolve the warning
// double a;

int main() {
}
```