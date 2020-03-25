---
title: 编译器警告（等级1） C4074
ms.date: 11/04/2016
f1_keywords:
- C4074
helpviewer_keywords:
- C4074
ms.assetid: cd510e66-c338-4a86-a4d7-bfa1df9b16c3
ms.openlocfilehash: 7a11112962872788df855bfc63b869193188fab9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164074"
---
# <a name="compiler-warning-level-1-c4074"></a>编译器警告（等级1） C4074

初始值设定项放置在编译器保留的初始化区域中

由 Microsoft 保留[#pragma init_seg](../../preprocessor/init-seg.md)指定的编译器初始化区域。 此区域中的代码可在 C 运行库的初始化之前执行。

下面的示例生成 C4074：

```cpp
// C4074.cpp
// compile with: /W1
#pragma init_seg( compiler )   // C4074

// try this line to resolve the warning
// #pragma init_seg(user)

int main() {
}
```
