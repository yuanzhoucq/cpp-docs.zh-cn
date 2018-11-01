---
title: 编译器警告 （等级 1） C4074
ms.date: 11/04/2016
f1_keywords:
- C4074
helpviewer_keywords:
- C4074
ms.assetid: cd510e66-c338-4a86-a4d7-bfa1df9b16c3
ms.openlocfilehash: d9b0259e95198396d8c34ca43781045248e22ad9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50665556"
---
# <a name="compiler-warning-level-1-c4074"></a>编译器警告 （等级 1） C4074

初始值设定项放置在编译器保留的初始化区域

编译器初始化区域中，通过指定[#pragma init_seg](../../preprocessor/init-seg.md)，Microsoft 保留。 可能的 C 运行时库初始化之前执行此区域中的代码。

下面的示例生成 C4074:

```
// C4074.cpp
// compile with: /W1
#pragma init_seg( compiler )   // C4074

// try this line to resolve the warning
// #pragma init_seg(user)

int main() {
}
```