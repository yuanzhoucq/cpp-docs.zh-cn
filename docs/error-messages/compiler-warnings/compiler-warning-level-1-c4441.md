---
title: 编译器警告（等级 1）C4441
ms.date: 11/04/2016
f1_keywords:
- C4441
helpviewer_keywords:
- C4441
ms.assetid: 7fc540a5-e41f-47cf-aa37-b2b699c2685e
ms.openlocfilehash: 45d7a6af09677c1e63dab5ffcc55c35d8203b40b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50539689"
---
# <a name="compiler-warning-level-1-c4441"></a>编译器警告（等级 1）C4441

cc1 被忽略; 的调用约定cc2 改为使用

必须使用托管的用户定义类型和全局函数泛型中的成员函数[__clrcall](../../cpp/clrcall.md)调用约定。  使用编译器`__clrcall`。

## <a name="example"></a>示例

下面的示例生成 C4441。

```
// C4441.cpp
// compile with: /clr /W1 /c
generic <class ItemType>
void __cdecl Test(ItemType item) {}   // C4441
// try the following line instead
// void Test(ItemType item) {}

ref struct MyStruct {
   void __cdecl Test(){}   // C4441
   void Test2(){}   // OK
};
```