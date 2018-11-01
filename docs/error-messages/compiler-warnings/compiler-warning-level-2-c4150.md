---
title: 编译器警告 （等级 2） C4150
ms.date: 11/04/2016
f1_keywords:
- C4150
helpviewer_keywords:
- C4150
ms.assetid: ff1760ec-0d9f-4d45-b797-94261624becf
ms.openlocfilehash: 4c5c10ee0ea3242e52e6db5391694c9ddf941a78
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50527668"
---
# <a name="compiler-warning-level-2-c4150"></a>编译器警告 （等级 2） C4150

删除的指针，指向不完整类型 type;没有调用析构函数

**删除**调用运算符来删除的类型已声明但未定义，这样编译器找不到析构函数。

下面的示例生成 C4150:

```
// C4150.cpp
// compile with: /W2
class  IncClass;

void NoDestruct( IncClass* pIncClass )
{
   delete pIncClass;
} // C4150, define class to resolve

int main()
{
}
```