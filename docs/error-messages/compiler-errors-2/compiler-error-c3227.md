---
title: 编译器错误 C3227
ms.date: 11/04/2016
f1_keywords:
- C3227
helpviewer_keywords:
- C3227
ms.assetid: 7939c23a-96c8-43c2-89e9-f217d132d155
ms.openlocfilehash: 460000531dba77e42379199f276c9e2e02f43a9b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743414"
---
# <a name="compiler-error-c3227"></a>编译器错误 C3227

"parameter"：不能使用 "关键字" 来分配泛型类型

为了实例化类型，需要一个适当的构造函数。 但编译器无法确保适当的构造函数可用。

您可以使用模板（而不是泛型）来解决此错误，也可以使用多种方法之一来创建该类型的实例。

## <a name="example"></a>示例

下面的示例生成 C3227。

```cpp
// C3227.cpp
// compile with: /clr /c
generic<class T> interface class ICreate {
   static T Create();
};

generic <class T>
where T : ICreate<T>
ref class C {
   void f() {
      T t = new T;   // C3227

      // OK
      T t2 = ICreate<T>::Create();
      T t3 = safe_cast<T>( System::Activator::CreateInstance(T::typeid) );
   }
};
```
