---
title: 如何：用 interior_ptr 关键字声明值类型 (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- _ptr keyword
- value types, declaring
ms.assetid: 49eea66e-eeba-49bd-95b0-ba297be436e3
ms.openlocfilehash: 22c0fe4424e4df81ebb0355dfac2168af725b971
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172277"
---
# <a name="how-to-declare-value-types-with-the-interior_ptr-keyword-ccli"></a>如何：用 interior_ptr 关键字声明值类型 (C++/CLI)

interior_ptr 可以用于值类型。

> [!IMPORTANT]
> `/clr` 编译器选项支持此语言功能，但是 `/ZW` 编译器选项不支持此语言功能。

## <a name="example"></a>示例

### <a name="description"></a>说明

下面的 C++/CLI 示例展示了如何将 interior_ptr 用于值类型。

### <a name="code"></a>代码

```cpp
// interior_ptr_value_types.cpp
// compile with: /clr
value struct V {
   V(int i) : data(i){}
   int data;
};

int main() {
   V v(1);
   System::Console::WriteLine(v.data);

   // pointing to a value type
   interior_ptr<V> pv = &v;
   pv->data = 2;

   System::Console::WriteLine(v.data);
   System::Console::WriteLine(pv->data);

   // pointing into a value type
   interior_ptr<int> pi = &v.data;
   *pi = 3;
   System::Console::WriteLine(*pi);
   System::Console::WriteLine(v.data);
   System::Console::WriteLine(pv->data);
}
```

```Output
1
2
2
3
3
3
```

## <a name="example"></a>示例

### <a name="description"></a>说明

在值类型中，this 指针的计算结果为 interior_ptr。

在值类型 `V` 的非静态成员函数主体中，this 是类型 `interior_ptr<V>` 的表达式，它的值是为其调用函数的对象的地址。

### <a name="code"></a>代码

```cpp
// interior_ptr_value_types_this.cpp
// compile with: /clr /LD
value struct V {
   int data;
   void f() {
      interior_ptr<V> pv1 = this;
      // V* pv2 = this;   error
   }
};
```

## <a name="example"></a>示例

### <a name="description"></a>说明

下面的示例演示了如何将 address-of 运算符与静态成员一起使用。

静态 Visual C++ 类型成员的地址产生本机指针。  静态值类型成员的地址是托管指针，因为值类型成员在运行时堆上分配，并且可由垃圾回收器移动。

### <a name="code"></a>代码

```cpp
// interior_ptr_value_static.cpp
// compile with: /clr
using namespace System;
value struct V { int i; };

ref struct G {
   static V v = {22};
   static int i = 23;
   static String^ pS = "hello";
};

int main() {
   interior_ptr<int> p1 = &G::v.i;
   Console::WriteLine(*p1);

   interior_ptr<int> p2 = &G::i;
   Console::WriteLine(*p2);

   interior_ptr<String^> p3 = &G::pS;
   Console::WriteLine(*p3);
}
```

```Output
22
23
hello
```

## <a name="see-also"></a>另请参阅

[interior_ptr (C++/CLI)](interior-ptr-cpp-cli.md)
