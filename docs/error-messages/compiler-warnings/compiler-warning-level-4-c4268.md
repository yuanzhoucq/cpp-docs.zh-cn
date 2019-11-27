---
title: 编译器警告（等级 4）C4268
ms.date: 11/04/2016
f1_keywords:
- C4268
helpviewer_keywords:
- C4268
ms.assetid: d0511e80-904f-4ee1-b4d7-39b5c0bd8234
ms.openlocfilehash: 1d0531b79ef29d2aa9528cc29046fa9e9514c379
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541985"
---
# <a name="compiler-warning-level-4-c4268"></a>编译器警告（等级 4）C4268

"identifier"：用编译器生成的默认构造函数初始化的 "const" 静态/全局数据用零填充对象

不常用类的**const**全局或静态实例使用编译器生成的默认构造函数进行初始化。

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

由于此类实例是**const**，因此不能更改 `m_data` 的值。