---
title: delegate（C++/CLI 和 C++/CX）
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- delegate_cpp
- delegate
helpviewer_keywords:
- delegate keyword [C++]
ms.assetid: 03caf23d-7873-4a23-9b34-becf42aaf429
ms.openlocfilehash: 77cd17eb8c164a08af9ec783f8aba422785609b6
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219724"
---
# <a name="delegate--ccli-and-ccx"></a>delegate（C++/CLI 和 C++/CX）

声明表示函数指针的类型。

## <a name="all-runtimes"></a>所有运行时

Windows 运行时和公共语言运行时都支持委托。

### <a name="remarks"></a>备注

delegate**** 是上下文相关关键字。 有关详细信息，请参阅[上下文相关关键字](context-sensitive-keywords-cpp-component-extensions.md)。

若要在编译时检测类型是否是委托，请使用 `__is_delegate()` 类型特征。 有关详细信息，请参阅[编译器对类型特征的支持](compiler-support-for-type-traits-cpp-component-extensions.md)。

## <a name="windows-runtime"></a>Windows 运行时

C++/CX 支持使用以下语法的委托。

### <a name="syntax"></a>语法

```cpp
access
delegate
return-type
delegate-type-identifier
(
[ parameters ]
)
```

### <a name="parameters"></a>参数

*access*<br/>
可有可无委托的可访问性，可以是 **`public`** （默认值）或 **`private`** 。 函数原型还可以用 **`const`** 或 **`volatile`** 关键字限定。

*返回类型*<br/>
函数原型的返回类型。

delegate-type-identifier**<br/>
声明的委托类型的名称。

*parameters*<br/>
（可选）函数原型的类型和标识符。

### <a name="remarks"></a>备注

delegate-type-identifier** 可用于声明与委托具有相同原型的事件。 有关详细信息，请参阅 [delegate (C++/CX)](../cppcx/delegates-c-cx.md)。

### <a name="requirements"></a>要求

编译器选项：`/ZW`

## <a name="common-language-runtime"></a>公共语言运行时

公共语言运行时支持使用以下语法的委托。

### <a name="syntax"></a>语法

```cpp
access
delegate
function_declaration
```

### <a name="parameters"></a>参数

*access*<br/>
（可选）程序集外部委托的可访问性可以是 public 或 private。  默认值为 private。  在类中，委托可具有任意可访问性。

function_declaration**<br/>
可以绑定到委托的函数的签名。 委托的返回类型可以是任意托管类型。 出于互操作性方面的考虑，建议使用 CLS 类型作为委托的返回类型。

若要定义未绑定的委托， *function_declaration*中的第一个参数应为 **`this`** 该对象的指针类型。

### <a name="remarks"></a>备注

委托是多播的。也就是说，“函数指针”可以绑定到托管类中的一个或多个方法。 delegate**** 关键字定义了含特定方法签名的多播委托类型。

委托还可以绑定到 value class 的方法（如静态方法）。

委托有以下特征：

- 它继承自 `System::MulticastDelegate`。

- 它有一个构造函数，需要使用以下两个参数：指向托管类或 NULL（在绑定到静态方法时）的指针，以及采用指定类型的完全限定方法。

- 它具有一个称为 `Invoke` 的方法，其签名与委托的声明签名匹配。

在委托获得调用后，它的一个或多个函数按附加顺序进行调用。

委托的返回值是它最后一个附加成员函数的返回值。

无法重载委托。

可以绑定委托，也可以不绑定委托。

实例化绑定委托时，第一个参数应为对象引用。 委托实例化的第二个参数要么应为托管类对象的方法的地址，要么应为指向采用值类型的方法的指针。 委托实例化的第二个参数必须使用完整的类范围语法来命名方法，并应用取址器运算符。

实例化未绑定委托时，第一个参数要么应为托管类对象的方法的地址，要么应为指向采用值类型的方法的指针。 此参数必须使用完整的类范围语法来命名方法，并应用取址器运算符。

创建静态函数或全局函数的委托时，只需要一个参数，即函数（也可以视需要使用函数地址）。

若要详细了解委托，请参阅

- [如何：定义和使用委托 (C++/CLI)](../dotnet/how-to-define-and-use-delegates-cpp-cli.md)

- [泛型委托 (C++/CLI)](generic-delegates-visual-cpp.md)

### <a name="requirements"></a>要求

编译器选项：`/clr`

### <a name="examples"></a>示例

下面的示例展示了如何声明、初始化和调用委托。

```cpp
// mcppv2_delegate.cpp
// compile with: /clr
using namespace System;

// declare a delegate
public delegate void MyDel(int i);

ref class A {
public:
   void func1(int i) {
      Console::WriteLine("in func1 {0}", i);
   }

   void func2(int i) {
      Console::WriteLine("in func2 {0}", i);
   }

   static void func3(int i) {
      Console::WriteLine("in static func3 {0}", i);
   }
};

int main () {
   A ^ a = gcnew A;

   // declare a delegate instance
   MyDel^ DelInst;

   // test if delegate is initialized
   if (DelInst)
      DelInst(7);

   // assigning to delegate
   DelInst = gcnew MyDel(a, &A::func1);

   // invoke delegate
   if (DelInst)
      DelInst(8);

   // add a function
   DelInst += gcnew MyDel(a, &A::func2);

   DelInst(9);

   // remove a function
   DelInst -= gcnew MyDel(a, &A::func1);

   // invoke delegate with Invoke
   DelInst->Invoke(10);

   // make delegate to static function
   MyDel ^ StaticDelInst = gcnew MyDel(&A::func3);
   StaticDelInst(11);
}
```

```Output
in func1 8

in func1 9

in func2 9

in func2 10

in static func3 11
```

## <a name="see-also"></a>另请参阅

[适用于 .NET 和 UWP 的组件扩展](component-extensions-for-runtime-platforms.md)
