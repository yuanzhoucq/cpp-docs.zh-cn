---
title: interior_ptr (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- stdcli::language::interior_ptr
- interior_ptr_cpp
- interior_ptr
helpviewer_keywords:
- interior_ptr keyword [C++]
ms.assetid: 25160f74-569e-492d-9e3c-67ece7486baa
ms.openlocfilehash: 264ac0a56996b0dcbeeb64246623eca1a3fc73ff
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172147"
---
# <a name="interior_ptr-ccli"></a>interior_ptr (C++/CLI)

内部指针声明指向引用类型内部，但不指向对象本身的指针。 内部指针可以指向引用句柄、值类型、装箱类型句柄、托管类型的成员或托管数组的元素。

## <a name="all-runtimes"></a>所有运行时

（此语言功能没有适用于所有运行时的备注。）

## <a name="windows-runtime"></a>Windows 运行时

(此语言功能没有只适用于 Windows 运行时的备注。）

### <a name="requirements"></a>要求

编译器选项：`/ZW`

## <a name="common-language-runtime"></a>公共语言运行时

以下语法示例演示内部指针。

### <a name="syntax"></a>语法

```cpp
cli::interior_ptr<cv_qualifier type> var = &initializer;
```

### <a name="parameters"></a>parameters

cv_qualifier<br/>
const 或 volatile 限定符。

type<br/>
初始值设定项的类型。

*var*<br/>
interior_ptr 变量的名称。

*initializer*<br/>
可以分配给本机指针的引用类型、托管数组的元素或者任何其他对象的成员。

### <a name="remarks"></a>备注

本机指针无法跟踪项，因为其位置在托管堆上不断变化，这是由垃圾回收器移动对象实例引起的。 为了使指针正确指向实例，运行时需要将指针更新到新定位的对象。

interior_ptr 表示本机指针的功能超集。  因此，可以分配给本机指针的所有内容也可以分配给 interior_ptr。  内部指针允许执行与本机指针相同的操作，其中包括比较和指针算法。

内部指针只能在堆栈上声明。  内部指针无法声明为类的成员。

由于内部指针仅存在于堆栈，使用内部指针的地址会产生非托管指针。

interior_ptr 支持隐式转换为 bool，所以可用于条件语句。

若要了解如何声明指向无法在垃圾回收堆上移动的对象的内部指针，请参阅 [pin_ptr](pin-ptr-cpp-cli.md)。

interior_ptr 位于 cli 命名空间中。  有关详细信息，请参阅[平台默认 cli 命名空间](platform-default-and-cli-namespaces-cpp-component-extensions.md)。

有关内部指针的详细信息，请参阅

- [如何：声明和使用内部指针及托管数组 (C++/CLI)](how-to-declare-and-use-interior-pointers-and-managed-arrays-cpp-cli.md)

- [如何：用 interior_ptr 关键字声明值类型 (C++/CLI)](how-to-declare-value-types-with-the-interior-ptr-keyword-cpp-cli.md)

- [如何：用内部指针和本机指针重载函数 (C++/CLI)](how-to-overload-functions-with-interior-pointers-and-native-pointers-cpp-cli.md)

- [如何：用 const 关键字声明内部指针 (C++/CLI)](how-to-declare-interior-pointers-with-the-const-keyword-cpp-cli.md)

### <a name="requirements"></a>要求

编译器选项：`/clr`

### <a name="examples"></a>示例

以下示例演示如何声明和使用指向引用类型的内部指针。

```cpp
// interior_ptr.cpp
// compile with: /clr
using namespace System;

ref class MyClass {
public:
   int data;
};

int main() {
   MyClass ^ h_MyClass = gcnew MyClass;
   h_MyClass->data = 1;
   Console::WriteLine(h_MyClass->data);

   interior_ptr<int> p = &(h_MyClass->data);
   *p = 2;
   Console::WriteLine(h_MyClass->data);

   // alternatively
   interior_ptr<MyClass ^> p2 = &h_MyClass;
   (*p2)->data = 3;
   Console::WriteLine((*p2)->data);
}
```

```Output
1
2
3
```

## <a name="see-also"></a>另请参阅

[ .NET 和 UWP 的组件扩展](component-extensions-for-runtime-platforms.md)
