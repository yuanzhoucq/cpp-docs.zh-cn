---
title: 编译器警告（等级 1）C4677
ms.date: 11/04/2016
f1_keywords:
- C4677
helpviewer_keywords:
- C4677
ms.assetid: a8d656a1-e2ff-4f8b-9028-201765131026
ms.openlocfilehash: 5b31fd22c917b2c0f505ca189425f8160f62f748
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175540"
---
# <a name="compiler-warning-level-1-c4677"></a>编译器警告（等级 1）C4677

"function"：非私有成员的签名包含程序集私有类型 "private_type"

在程序集外具有公共可访问性的类型使用在程序集外部具有私有访问权限的类型。 引用公共程序集类型的组件将无法使用引用该程序集私有类型的类型成员。

## <a name="example"></a>示例

下面的示例生成 C4677。

```cpp
// C4677.cpp
// compile with: /clr /c /W1
delegate void TestDel();
public delegate void TestDel2();

public ref class MyClass {
public:
   static event TestDel^ MyClass_Event;   // C4677
   static event TestDel2^ MyClass_Event2;   // OK
};
```
