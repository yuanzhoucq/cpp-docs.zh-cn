---
title: 编译器错误 C3227
ms.date: 11/04/2016
f1_keywords:
- C3227
helpviewer_keywords:
- C3227
ms.assetid: 7939c23a-96c8-43c2-89e9-f217d132d155
ms.openlocfilehash: b175b14af55a9a462e040f064cc6e38d13fffb94
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50632487"
---
# <a name="compiler-error-c3227"></a>编译器错误 C3227

parameter： 无法使用 keyword 来分配泛型类型

若要实例化一个类型，相应的构造函数是必需的。 但是，编译器不能确保适当的构造函数可用。

可以使用模板而不是泛型若要解决此错误，或者可以使用几种方法之一来创建类型的实例。

## <a name="example"></a>示例

下面的示例生成 C3227。

```
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