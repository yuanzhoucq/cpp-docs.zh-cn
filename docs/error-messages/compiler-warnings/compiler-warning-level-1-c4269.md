---
title: 编译器警告（等级 1）C4269
ms.date: 11/04/2016
f1_keywords:
- C4269
helpviewer_keywords:
- C4269
ms.assetid: 96c97bbc-068a-4b65-8cd8-4ed5dca04c15
ms.openlocfilehash: 1b63d1af49a53b7b15cdbae912d79a1b4f0cf787
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230709"
---
# <a name="compiler-warning-level-1-c4269"></a>编译器警告（等级 1）C4269

"identifier"：用编译器生成的默认构造函数初始化的 "const" 自动数据产生不可靠的结果

**`const`** 使用编译器生成的默认构造函数初始化非普通类的自动实例。

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

由于类的此实例是在堆栈上生成的，因此的初始值 `m_data` 可以是任何值。 另外，由于它是一个 **`const`** 实例，因此 `m_data` 永远不能更改的值。
