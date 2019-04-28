---
title: 编译器警告（等级 1）C4237
ms.date: 11/04/2016
f1_keywords:
- C4237
helpviewer_keywords:
- C4237
ms.assetid: f2e86c4b-80d8-460e-9429-83c5f3f5d7ca
ms.openlocfilehash: 04fcb99e1dd1e348716e25affb22b54079d53aa9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62207378"
---
# <a name="compiler-warning-level-1-c4237"></a>编译器警告（等级 1）C4237

keyword 关键字尚不受支持，但保留供将来使用

中的关键字C++规范未在视觉对象中实现C++编译器，但关键字不能作为用户定义的符号。

下面的示例生成 C4237:

```
// C4237.cpp
// compile with: /W1 /c
int export;   // C4237
```