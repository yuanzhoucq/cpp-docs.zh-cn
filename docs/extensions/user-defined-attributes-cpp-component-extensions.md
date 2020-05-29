---
title: 用户定义特性（C++/CLI 和 C++/CX）
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- metadata, extending
- custom attributes, extending metadata
ms.assetid: 98b29048-a3ea-4698-8441-f149cdaec9fb
ms.openlocfilehash: aed36ac7fed7eb1f16f8648f7bcd7efb37f43a75
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171887"
---
# <a name="user-defined-attributes--ccli-and-ccx"></a>用户定义特性（C++/CLI 和 C++/CX）

使用 C++/CLI 和 C++/CX，可以创建平台专用特性来扩展接口、类或结构、方法、参数或枚举的元数据。 这些特性不同于[标准 C++ 特性](../cpp/attributes.md)。

## <a name="windows-runtime"></a>Windows 运行时

C++/CX 特性可应用于属性，但无法应用于构造函数或方法。

### <a name="requirements"></a>要求

编译器选项：`/ZW`

## <a name="common-language-runtime"></a>公共语言运行时

本主题中的信息和语法旨在取代 [attribute](../windows/attributes/attribute.md) 中的信息。

可以定义自定义特性，具体方法为定义类型，让 <xref:System.Attribute> 成为此类型的基类，并视需要应用 <xref:System.AttributeUsageAttribute> 特性。

有关详细信息，请参阅：

- [特性目标](attribute-targets-cpp-component-extensions.md)

- [特性参数类型](attribute-parameter-types-cpp-component-extensions.md)

若要了解如何在 Visual C++ 中签名程序集，请参阅[强名称程序集（程序集签名）(C++/CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)。

### <a name="requirements"></a>要求

编译器选项：`/clr`

### <a name="examples"></a>示例

下面的示例展示了如何定义自定义特性。

```cpp
// user_defined_attributes.cpp
// compile with: /clr /c
using namespace System;

[AttributeUsage(AttributeTargets::All)]
ref struct Attr : public Attribute {
   Attr(bool i){}
   Attr(){}
};

[Attr]
ref class MyClass {};
```

下面的示例展示了自定义特性的一些重要功能。 例如，此示例展示了自定义特性的一种常见用法，即实例化可完全向客户端描述自身的服务器。

```cpp
// extending_metadata_b.cpp
// compile with: /clr
using namespace System;
using namespace System::Reflection;

public enum class Access { Read, Write, Execute };

// Defining the Job attribute:
[AttributeUsage(AttributeTargets::Class, AllowMultiple=true )]
public ref class Job : Attribute {
public:
   property int Priority {
      void set( int value ) { m_Priority = value; }
      int get() { return m_Priority; }
   }

   // You can overload constructors to specify Job attribute in different ways
   Job() { m_Access = Access::Read; }
   Job( Access a ) { m_Access = a; }
   Access m_Access;

protected:
   int m_Priority;
};

interface struct IService {
   void Run();
};

   // Using the Job attribute:
   // Here we specify that QueryService is to be read only with a priority of 2.
   // To prevent namespace collisions, all custom attributes implicitly
   // end with "Attribute".

[Job( Access::Read, Priority=2 )]
ref struct QueryService : public IService {
   virtual void Run() {}
};

// Because we said AllowMultiple=true, we can add multiple attributes
[Job(Access::Read, Priority=1)]
[Job(Access::Write, Priority=3)]
ref struct StatsGenerator : public IService {
   virtual void Run( ) {}
};

int main() {
   IService ^ pIS;
   QueryService ^ pQS = gcnew QueryService;
   StatsGenerator ^ pSG = gcnew StatsGenerator;

   //  use QueryService
   pIS = safe_cast<IService ^>( pQS );

   // use StatsGenerator
   pIS = safe_cast<IService ^>( pSG );

   // Reflection
   MemberInfo ^ pMI = pIS->GetType();
   array <Object ^ > ^ pObjs = pMI->GetCustomAttributes(false);

   // We can now quickly and easily view custom attributes for an
   // Object through Reflection */
   for( int i = 0; i < pObjs->Length; i++ ) {
      Console::Write("Service Priority = ");
      Console::WriteLine(static_cast<Job^>(pObjs[i])->Priority);
      Console::Write("Service Access = ");
      Console::WriteLine(static_cast<Job^>(pObjs[i])->m_Access);
   }
}
```

```Output
Service Priority = 0

Service Access = Write

Service Priority = 3

Service Access = Write

Service Priority = 1

Service Access = Read
```

`Object^` 类型替换变量数据类型。 下面的示例定义需要使用一组 `Object^` 作为参数的自定义特性。

特性参数必须是编译时常量；在大多数情况下，它们应是常量文字。

若要了解如何从自定义特性块返回 System::Type 值，请参阅 [typeid](typeid-cpp-component-extensions.md)。

```cpp
// extending_metadata_e.cpp
// compile with: /clr /c
using namespace System;
[AttributeUsage(AttributeTargets::Class | AttributeTargets::Method)]
public ref class AnotherAttr : public Attribute {
public:
   AnotherAttr(array<Object^>^) {}
   array<Object^>^ var1;
};

// applying the attribute
[ AnotherAttr( gcnew array<Object ^> { 3.14159, "pi" }, var1 = gcnew array<Object ^> { "a", "b" } ) ]
public ref class SomeClass {};
```

运行时要求，自定义特性类的公共部分必须是可序列化的。  创建自定义特性时，自定义特性的命名参数仅限于编译时常量。  （将它视为追加到元数据中类布局的位序列。）

```cpp
// extending_metadata_f.cpp
// compile with: /clr /c
using namespace System;
ref struct abc {};

[AttributeUsage( AttributeTargets::All )]
ref struct A : Attribute {
   A( Type^ ) {}
   A( String ^ ) {}
   A( int ) {}
};

[A( abc::typeid )]
ref struct B {};
```

## <a name="see-also"></a>另请参阅

[ .NET 和 UWP 的组件扩展](component-extensions-for-runtime-platforms.md)
