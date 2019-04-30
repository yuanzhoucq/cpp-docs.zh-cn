---
title: 编译器警告（等级 4）C4268
ms.date: 11/04/2016
f1_keywords:
- C4268
helpviewer_keywords:
- C4268
ms.assetid: d0511e80-904f-4ee1-b4d7-39b5c0bd8234
ms.openlocfilehash: e3cda7ed70963508d7663c6c12b2b98ac64db204
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400911"
---
# <a name="compiler-warning-level-4-c4268"></a>编译器警告（等级 4）C4268

identifier： 用编译器生成默认构造函数初始化 const 静态/全局数据填充了零对象

一个**const**使用编译器生成的默认构造函数初始化全局或静态的重要类的实例。

## <a name="example"></a>示例

```
// C4268.cpp
// compile with: /c /LD /W4
class X {
public:
   int m_data;
};

const X x1;   // C4268
```

为此类的实例**const**，值`m_data`不能更改。