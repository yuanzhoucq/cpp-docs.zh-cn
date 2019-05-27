---
title: 泛型函数 (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- functions [C++], generic
- generic methods
- generics [C++], functions
- methods [C++], generic
- generic functions
ms.assetid: 8e409364-58f9-4360-b486-e7d555e0c218
ms.openlocfilehash: a4a1702c8b9902f5265a8a5f92316d7c82751609
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "65516372"
---
# <a name="generic-functions-ccli"></a>泛型函数 (C++/CLI)

泛型函数是指使用类型参数声明的函数。 在函数调用后，使用的是实际类型，而不是类型参数。

## <a name="all-platforms"></a>所有平台

### <a name="remarks"></a>备注

此功能不适用于所有平台。

## <a name="windows-runtime"></a>Windows 运行时

### <a name="remarks"></a>备注

Windows 运行时不支持此功能。

### <a name="requirements"></a>要求

编译器选项：`/ZW`

## <a name="common-language-runtime"></a>公共语言运行时

泛型函数是指使用类型参数声明的函数。 在函数调用后，使用的是实际类型，而不是类型参数。

### <a name="syntax"></a>语法

```cpp
[attributes] [modifiers]
return-type identifier<type-parameter identifier(s)>
[type-parameter-constraints clauses]

([formal-parameters])
{function-body}
```

### <a name="parameters"></a>参数

*特性*<br/>
（可选）其他声明性信息。 若要详细了解特性和特性类，请参阅“attribute”。

modifiers<br/>
（可选）函数修饰符（如 static）。  禁止使用 virtual，因为虚方法可能不是泛型。

return-type<br/>
由方法返回的类型。 如果返回类型为 void，则不需要返回值。

*identifier*<br/>
函数名称。

type-parameter identifier(s)<br/>
标识符的逗号分隔列表。

formal-parameters<br/>
（可选）参数列表。

type-parameter-constraints-clauses<br/>
这指定了对可以用作类型参数的类型施加的限制，并采用[泛型类型参数的约束 (C++/CLI)](constraints-on-generic-type-parameters-cpp-cli.md) 中指定的形式。

function-body<br/>
方法主体，可能会引用类型参数标识符。

### <a name="remarks"></a>备注

泛型函数是指使用泛型类型参数声明的函数。 它们可以是类或结构中的方法，也可以是独立函数。 一个泛型声明隐式声明一系列函数，这些函数的唯一区别是，使用不同的实际类型来替换泛型类型参数。

类或结构构造函数无法使用泛型类型参数进行声明。

在函数调用后，实际类型替换泛型类型参数。 可以使用类似于模板函数调用的语法，在尖括号中显式指定实际类型。 如果在调用函数时没有类型参数，编译器会尝试根据函数调用中提供的参数推导实际类型。 如果无法根据所用参数推导预期类型参数，编译器会报告错误。

### <a name="requirements"></a>要求

编译器选项：`/clr`

### <a name="examples"></a>示例

下面的代码示例展示了泛型函数。

```cpp
// generics_generic_function_1.cpp
// compile with: /clr
generic <typename ItemType>
void G(int i) {}

ref struct A {
   generic <typename ItemType>
   void G(ItemType) {}

   generic <typename ItemType>
   static void H(int i) {}
};

int main() {
   A myObject;

   // generic function call
   myObject.G<int>(10);

   // generic function call with type parameters deduced
   myObject.G(10);

   // static generic function call
   A::H<int>(10);

   // global generic function call
   G<int>(10);
}
```

泛型函数可以根据签名或参数数量（函数中类型参数的数量）进行重载。 此外，泛型函数还可以重载有同名的非泛型函数，只要这些函数的一些类型参数不同即可。 例如，可以重载下面的函数：

```cpp
// generics_generic_function_2.cpp
// compile with: /clr /c
ref struct MyClass {
   void MyMythod(int i) {}

   generic <class T>
   void MyMythod(int i) {}

   generic <class T, class V>
   void MyMythod(int i) {}
};
```

下面的示例使用泛型函数来查找数组中的第一个元素。 它声明继承自基类 `MyBaseClass` 的 `MyClass`。 `MyClass` 包含泛型函数 `MyFunction`，此函数调用基类中的另一个泛型函数 `MyBaseClassFunction`。 在 `main` 中，泛型函数 `MyFunction` 是通过使用不同的类型参数进行调用。

```cpp
// generics_generic_function_3.cpp
// compile with: /clr
using namespace System;

ref class MyBaseClass {
protected:
   generic <class ItemType>
   ItemType MyBaseClassFunction(ItemType item) {
      return item;
   }
};

ref class MyClass: public MyBaseClass {
public:
   generic <class ItemType>
   ItemType MyFunction(ItemType item) {
      return MyBaseClass::MyBaseClassFunction<ItemType>(item);
   }
};

int main() {
   MyClass^ myObj = gcnew MyClass();

   // Call MyFunction using an int.
   Console::WriteLine("My function returned an int: {0}",
                           myObj->MyFunction<int>(2003));

   // Call MyFunction using a string.
   Console::WriteLine("My function returned a string: {0}",
   myObj->MyFunction<String^>("Hello generic functions!"));
}
```

```Output
My function returned an int: 2003
My function returned a string: Hello generic functions!
```

## <a name="see-also"></a>请参阅

[ .NET 和 UWP 的组件扩展](component-extensions-for-runtime-platforms.md)<br/>
[泛型](generics-cpp-component-extensions.md)
