---
title: 编译器警告 （等级 1） C4677 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4677
dev_langs:
- C++
helpviewer_keywords:
- C4677
ms.assetid: a8d656a1-e2ff-4f8b-9028-201765131026
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b6a3f57ba0e3d4c15c83711a86bb8482fa8b0596
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46049379"
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