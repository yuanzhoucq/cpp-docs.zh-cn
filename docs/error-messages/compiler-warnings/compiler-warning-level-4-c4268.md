---
title: 编译器警告（等级 4）C4268
ms.date: 11/04/2016
f1_keywords:
- C4268
helpviewer_keywords:
- C4268
ms.assetid: d0511e80-904f-4ee1-b4d7-39b5c0bd8234
ms.openlocfilehash: 1db8f67591560c130bc25c40c63232f54b3b7884
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219906"
---
# <a name="compiler-warning-level-4-c4268"></a>编译器警告（等级 4）C4268

"identifier"：用编译器生成的默认构造函数初始化的 "const" 静态/全局数据用零填充对象

**`const`** 使用编译器生成的默认构造函数对非普通类的全局或静态实例进行初始化。

## <a name="example"></a>示例

```cpp
// C4268.cpp
// compile with: /c /LD /W4
class X {
public:
   int m_data;
};

const X x1;   // C4268
```

由于此类的实例为 **`const`** ， `m_data` 因此不能更改的值。
