---
title: 编译器警告（等级1） C4237
ms.date: 11/04/2016
f1_keywords:
- C4237
helpviewer_keywords:
- C4237
ms.assetid: f2e86c4b-80d8-460e-9429-83c5f3f5d7ca
ms.openlocfilehash: e53c4632f8bfc9764f6ab1e124582bda273d945e
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/05/2019
ms.locfileid: "73624904"
---
# <a name="compiler-warning-level-1-c4237"></a>编译器警告（等级1） C4237

"关键字" 关键字目前尚不受支持，但保留以供将来使用

该C++规范中的关键字未在 Microsoft C++编译器中实现，但关键字不可用作用户定义的符号。

下面的示例生成 C4237：

```cpp
// C4237.cpp
// compile with: /W1 /c
int export;   // C4237
```