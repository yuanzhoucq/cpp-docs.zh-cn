---
title: typeid（C++/CLI 和 C++/CX）
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- typeid keyword [C++]
ms.assetid: e9706cae-e7c4-4d6d-b474-646d73df3e70
ms.openlocfilehash: 8b22481fecb4b7de5106921fec1c3a43fab81a48
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181741"
---
# <a name="typeid--ccli-and-ccx"></a>typeid（C++/CLI 和 C++/CX）

获取指明对象类型的值。

> [!NOTE]
> 本主题引用 typeid 的 C++ 组件扩展版本。 有关此关键字的 ISO C++ 版本，请参阅 [typeid 运算符](../cpp/typeid-operator.md)。

## <a name="all-runtimes"></a>所有运行时

### <a name="syntax"></a>语法

```cpp
T::typeid
```

### <a name="parameters"></a>parameters

*T*<br/>
类型名称。

## <a name="windows-runtime"></a>Windows 运行时

### <a name="syntax"></a>语法

```cpp
Platform::Type^ type = T::typeid;
```

### <a name="parameters"></a>parameters

*T*<br/>
类型名称。

### <a name="remarks"></a>备注

在 C++/CX 中，typeid 返回根据运行时类型信息构造的 [Platform::Type](../cppcx/platform-type-class.md)。

### <a name="requirements"></a>要求

编译器选项：`/ZW`

## <a name="common-language-runtime"></a>公共语言运行时

### <a name="syntax"></a>语法

```
type::typeid
```

### <a name="parameters"></a>parameters

type<br/>
要为其获取 `System::Type` 对象的类型（抽象声明符）的名称。

### <a name="remarks"></a>备注

`typeid` 用于在编译时为类型获取 <xref:System.Type>。

`typeid` 类似于在运行时使用 <xref:System.Type.GetType%2A> 或 <xref:System.Object.GetType%2A> 为类型获取 System::Type。 然而，typeid 只接受类型名称作为参数。  若要使用类型实例来获取它的 System:: Type 名称，请使用 GetType。

`typeid` 必须可以在编译时计算类型名称（类型），而 GetType 则计算要在运行时返回的类型。

`typeid` 可以使用本机类型名称，也可以使用本机类型名称的公共语言运行时别名；有关详细信息，请参阅[相当于 C++ 本机类型的 .NET Framework 类型 (C++/CLI)](../dotnet/dotnet-framework-equivalents-to-cpp-native-types-cpp-cli.md)。

`typeid` 还适用于本机类型，不过它仍返回 System::Type。  若要获取 type_info 结构，请使用 [typeid 运算符](../cpp/typeid-operator.md)。

### <a name="requirements"></a>要求

编译器选项：`/clr`

### <a name="examples"></a>示例

下面的示例比较 typeid 关键字与 `GetType()` 成员。

```cpp
// keyword__typeid.cpp
// compile with: /clr
using namespace System;

ref struct G {
   int i;
};

int main() {
   G ^ pG = gcnew G;
   Type ^ pType = pG->GetType();
   Type ^ pType2 = G::typeid;

   if (pType == pType2)
      Console::WriteLine("typeid and GetType returned the same System::Type");
   Console::WriteLine(G::typeid);

   typedef float* FloatPtr;
   Console::WriteLine(FloatPtr::typeid);
}
```

```Output
typeid and GetType returned the same System::Type
G

System.Single*
```

下面的示例展示了类型变量 System::Type 可用于获取类型的特性。  它还展示了，必须对一些类型创建 typedef，才能使用 `typeid`。

```cpp
// keyword__typeid_2.cpp
// compile with: /clr
using namespace System;
using namespace System::Security;
using namespace System::Security::Permissions;

typedef int ^ handle_to_int;
typedef int * pointer_to_int;

public ref class MyClass {};

class MyClass2 {};

[attribute(AttributeTargets::All)]
ref class AtClass {
public:
   AtClass(Type ^) {
      Console::WriteLine("in AtClass Type ^ constructor");
   }
};

[attribute(AttributeTargets::All)]
ref class AtClass2 {
public:
   AtClass2() {
      Console::WriteLine("in AtClass2 constructor");
   }
};

// Apply the AtClass and AtClass2 attributes to class B
[AtClass(MyClass::typeid), AtClass2]
[AttributeUsage(AttributeTargets::All)]
ref class B : Attribute {};

int main() {
   Type ^ MyType = B::typeid;

   Console::WriteLine(MyType->IsClass);

   array<Object^>^ MyArray = MyType -> GetCustomAttributes(true);
   for (int i = 0 ; i < MyArray->Length ; i++ )
      Console::WriteLine(MyArray[i]);

   if (int::typeid != pointer_to_int::typeid)
      Console::WriteLine("int::typeid != pointer_to_int::typeid, as expected");

   if (int::typeid == handle_to_int::typeid)
      Console::WriteLine("int::typeid == handle_to_int::typeid, as expected");
}
```

```Output
True

in AtClass2 constructor

in AtClass Type ^ constructor

AtClass2

System.AttributeUsageAttribute

AtClass

int::typeid != pointer_to_int::typeid, as expected

int::typeid == handle_to_int::typeid, as expected
```

## <a name="see-also"></a>另请参阅

[ .NET 和 UWP 的组件扩展](component-extensions-for-runtime-platforms.md)
