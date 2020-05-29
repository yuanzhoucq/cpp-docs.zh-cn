---
title: 编译器警告（等级 1）C4269
ms.date: 11/04/2016
f1_keywords:
- C4269
helpviewer_keywords:
- C4269
ms.assetid: 96c97bbc-068a-4b65-8cd8-4ed5dca04c15
ms.openlocfilehash: e2e1781bf4c1b9ac0ee29d0b5900daa6cfe94b45
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199766"
---
# <a name="compiler-warning-level-1-c4269"></a>编译器警告（等级 1）C4269

"identifier"：用编译器生成的默认构造函数初始化的 "const" 自动数据产生不可靠的结果

使用编译器生成的默认构造函数初始化不常用类的**const**自动实例。

## <a name="example"></a>示例

```cpp
// C4269.cpp
// compile with: /c /LD /W1
class X {
public:
   int m_data;
};

void g() {
   const X x1;   // C4269
};
```

由于类的此实例是在堆栈上生成的，因此 `m_data` 的初始值可以是任何值。 另外，由于它是**const**实例，因此永远不能更改 `m_data` 的值。
