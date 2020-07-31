---
title: new（vtable 中的新槽）（C++/CLI 和 C++/CX）
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- new keyword [C++]
ms.assetid: 1a9a5704-f02f-46ae-ad65-f0f2b6dbabc3
ms.openlocfilehash: 29e43fe4c462fa6ac6523f8627abf923f02247a8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214238"
---
# <a name="new-new-slot-in-vtable--ccli-and-ccx"></a>new（vtable 中的新槽）（C++/CLI 和 C++/CX）

**`new`** 关键字指示虚拟成员将获取 vtable 中的新槽。

## <a name="all-runtimes"></a>所有运行时

（此语言功能没有适用于所有运行时的备注。）

## <a name="windows-runtime"></a>Windows 运行时

Windows 运行时不支持此功能。

## <a name="common-language-runtime"></a>公共语言运行时

### <a name="remarks"></a>备注

在 `/clr` 编译中， **`new`** 指示虚拟成员将获取 vtable 中的新槽; 该函数不会重写基类方法。

**`new`** 使 newslot 修饰符添加到函数的 IL。  若要详细了解 newslot，请参阅：

- <xref:System.Reflection.MethodInfo.GetBaseDefinition?displayProperty=nameWithType>

- <xref:System.Reflection.MethodAttributes?displayProperty=nameWithType>

### <a name="requirements"></a>要求

编译器选项：`/clr`

### <a name="examples"></a>示例

下面的示例演示了的效果 **`new`** 。

```cpp
// newslot.cpp
// compile with: /clr
ref class C {
public:
   virtual void f() {
      System::Console::WriteLine("C::f() called");
   }

   virtual void g() {
      System::Console::WriteLine("C::g() called");
   }
};

ref class D : public C {
public:
   virtual void f() new {
      System::Console::WriteLine("D::f() called");
   }

   virtual void g() override {
      System::Console::WriteLine("D::g() called");
   }
};

ref class E : public D {
public:
   virtual void f() override {
      System::Console::WriteLine("E::f() called");
   }
};

int main() {
   D^ d = gcnew D;
   C^ c = gcnew D;

   c->f();   // calls C::f
   d->f();   // calls D::f

   c->g();   // calls D::g
   d->g();   // calls D::g

   D ^ e = gcnew E;
   e->f();   // calls E::f
}
```

```Output
C::f() called

D::f() called

D::g() called

D::g() called

E::f() called
```

## <a name="see-also"></a>另请参阅

[适用于 .NET 和 UWP 的组件扩展](component-extensions-for-runtime-platforms.md)<br/>
[重写说明符](override-specifiers-cpp-component-extensions.md)
