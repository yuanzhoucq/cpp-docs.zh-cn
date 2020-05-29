---
title: 编译器警告（等级 3）C4102
ms.date: 11/04/2016
f1_keywords:
- C4102
helpviewer_keywords:
- C4102
ms.assetid: 349f308a-daf3-48c6-bd53-6c38b73f8880
ms.openlocfilehash: 53a68c476e307143d30f3bdbec88c0edb7d1bbd7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199072"
---
# <a name="compiler-warning-level-3-c4102"></a>编译器警告（等级 3）C4102

“label”: 未引用的标签

定义了标签，但从未引用过。 编译器忽略该标签。

下面的示例生成 C4102：

```cpp
// C4102.cpp
// compile with: /W3
int main() {
   int a;

   test:   // C4102, remove the unreferenced label to resolve

   a = 1;
}
```
