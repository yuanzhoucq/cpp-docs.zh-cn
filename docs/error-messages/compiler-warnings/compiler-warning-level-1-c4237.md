---
title: 编译器警告（等级 1）C4237
ms.date: 11/04/2016
f1_keywords:
- C4237
helpviewer_keywords:
- C4237
ms.assetid: f2e86c4b-80d8-460e-9429-83c5f3f5d7ca
ms.openlocfilehash: c68e84daa2ca1aa023123203bb851e92758f9e40
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447682"
---
# <a name="compiler-warning-level-1-c4237"></a>编译器警告（等级 1）C4237

keyword 关键字尚不受支持，但保留供将来使用

中的关键字C++规范未在 Microsoft 中实现C++编译器，但关键字不能作为用户定义的符号。

下面的示例生成 C4237:

```
// C4237.cpp
// compile with: /W1 /c
int export;   // C4237
```