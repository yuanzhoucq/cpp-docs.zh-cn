---
title: 编译器警告（等级 1）C4269
ms.date: 11/04/2016
f1_keywords:
- C4269
helpviewer_keywords:
- C4269
ms.assetid: 96c97bbc-068a-4b65-8cd8-4ed5dca04c15
ms.openlocfilehash: 9a7f42b2dd65644d3f2abec58236a0b93cc6f635
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62207228"
---
# <a name="compiler-warning-level-1-c4269"></a>编译器警告（等级 1）C4269

identifier： 用编译器生成默认构造函数初始化 const 自动数据产生不可靠的结果

一个**const**使用编译器生成的默认构造函数初始化的一个重要的类的自动实例。

## <a name="example"></a>示例

```
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

由于此类的实例在堆栈中的初始值，生成`m_data`可以是任何内容。 此外，由于它是**const**实例的值`m_data`永远不会更改。