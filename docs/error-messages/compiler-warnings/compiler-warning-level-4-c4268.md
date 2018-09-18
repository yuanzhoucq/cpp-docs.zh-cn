---
title: 编译器警告 （等级 C4268 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4268
dev_langs:
- C++
helpviewer_keywords:
- C4268
ms.assetid: d0511e80-904f-4ee1-b4d7-39b5c0bd8234
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f91a8152ef690b9ded63b91b2b6e6f1da6dc2524
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46063705"
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