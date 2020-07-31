---
title: typeid（C++/CLI 和 C++/CX）
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- typeid keyword [C++]
ms.assetid: e9706cae-e7c4-4d6d-b474-646d73df3e70
ms.openlocfilehash: 56319fb773b8398f85f5fd82c812f0efdb7dde15
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225106"
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

### <a name="parameters"></a>参数

*T*<br/>
类型名称。

## <a name="windows-runtime"></a>Windows 运行时

### <a name="syntax"></a>语法

```cpp
Platform::Type^ type = T::typeid;
```

### <a name="parameters"></a>参数

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

### <a name="parameters"></a>参数

*type*<br/>
要为其获取 `System::Type` 对象的类型（抽象声明符）的名称。

### <a name="remarks"></a>备注

**`typeid`** 用于 <xref:System.Type> 在编译时获取类型的。

**`typeid`** 类似于 `System::Type` 在运行时使用或获取类型的 <xref:System.Type.GetType%2A> <xref:System.Object.GetType%2A> 。 但是， **`typeid`** 只接受类型名称作为参数。  如果要使用类型的实例来获取其 `System::Type` 名称，请使用 `GetType` 。

**`typeid`** 必须能够在编译时计算类型名称（类型），而 GetType 计算在运行时返回的类型。

**`typeid`** 可以采用本机类型名称或公共语言运行时别名作为本机类型名称;有关详细信息，请参阅[与 c + + 本机类型的等效 .NET Framework （c + +/cli）](../dotnet/dotnet-framework-equivalents-to-cpp-native-types-cpp-cli.md) 。

**`typeid`** 还适用于本机类型，但它仍返回 `System::Type` 。  若要获取 type_info 结构，请使用[ `typeid` 运算符](../cpp/typeid-operator.md)。

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

下面的示例展示了类型变量 System::Type 可用于获取类型的特性。  它还显示，对于某些类型，必须创建要使用的 typedef **`typeid`** 。

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

[适用于 .NET 和 UWP 的组件扩展](component-extensions-for-runtime-platforms.md)
