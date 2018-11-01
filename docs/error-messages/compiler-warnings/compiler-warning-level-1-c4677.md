---
title: 编译器警告（等级 1）C4677
ms.date: 11/04/2016
f1_keywords:
- C4677
helpviewer_keywords:
- C4677
ms.assetid: a8d656a1-e2ff-4f8b-9028-201765131026
ms.openlocfilehash: 66b8d42b63bcbf328703523c4eeda7a047f4643c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50533011"
---
# <a name="compiler-warning-level-1-c4677"></a>编译器警告（等级 1）C4677

function： 非私有成员的签名包含程序集私有类型 private_type

具有程序集外部的公共可访问性的类型使用的类型，具有程序集外部的私有访问权限。 引用的公共程序集类型的组件不能使用类型成员或引用程序集私有类型的成员。

## <a name="example"></a>示例

下面的示例生成 C4677。

```
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