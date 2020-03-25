---
title: 编译器警告（等级 1）C4441
ms.date: 11/04/2016
f1_keywords:
- C4441
helpviewer_keywords:
- C4441
ms.assetid: 7fc540a5-e41f-47cf-aa37-b2b699c2685e
ms.openlocfilehash: 4de80a9b7ad5601d9f8760d7c55a64a8631307a8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162369"
---
# <a name="compiler-warning-level-1-c4441"></a>编译器警告（等级 1）C4441

已忽略 "cc1" 的调用约定;改为使用 "cc2"

托管用户定义类型中的成员函数和全局函数泛型必须使用[__clrcall](../../cpp/clrcall.md)调用约定。  编译器使用 `__clrcall`。

## <a name="example"></a>示例

下面的示例生成 C4441。

```cpp
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
