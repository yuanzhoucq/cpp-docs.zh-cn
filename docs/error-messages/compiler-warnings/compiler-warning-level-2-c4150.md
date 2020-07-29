---
title: 编译器警告（等级2） C4150
ms.date: 11/04/2016
f1_keywords:
- C4150
helpviewer_keywords:
- C4150
ms.assetid: ff1760ec-0d9f-4d45-b797-94261624becf
ms.openlocfilehash: a3993d2b993205c98de968ca893f24f703b3b635
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218138"
---
# <a name="compiler-warning-level-2-c4150"></a>编译器警告（等级2） C4150

删除指向不完整类型 "type" 的指针;未调用析构函数

**`delete`** 调用运算符来删除已声明但未定义的类型，因此编译器无法找到析构函数。

下面的示例生成 C4150：

```cpp
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
