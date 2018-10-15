---
title: 用户定义的属性 (C + + /cli 和 C + + /cli CX) |Microsoft Docs
ms.custom: ''
ms.date: 10/12/2018
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- metadata, extending
- custom attributes, extending metadata
ms.assetid: 98b29048-a3ea-4698-8441-f149cdaec9fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 004c4c30c6e7e75f626e1ac87c09cb0a87f1c8cc
ms.sourcegitcommit: 3f4e92266737ecb70507871e87dc8e2965ad7e04
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2018
ms.locfileid: "49328436"
---
# <a name="user-defined-attributes--ccli-and-ccx"></a>用户定义的属性 (C + + /cli 和 C + + /cli CX)

C + + /cli 和 C + + /cli CX 使您能够创建扩展的接口、 类或结构、 方法、 参数或枚举元数据的特定于平台的属性。 这些属性都是不同于[标准 c + + 特性](../cpp/attributes.md)。

## <a name="windows-runtime"></a>Windows 运行时

您可以应用的 C + + /cli CX 属性的属性，但无法构造函数或方法。

### <a name="requirements"></a>要求

编译器选项：`/ZW`

## <a name="common-language-runtime"></a>公共语言运行时

信息和本主题中的语法旨在取代中提供的信息[属性](attributes/attribute.md)。

可以通过定义一个类型并使定义的自定义特性<xref:System.Attribute>基类的类型和 （可选） 将应用<xref:System.AttributeUsageAttribute>属性。

有关详细信息，请参见:

- [特性目标](attribute-targets-cpp-component-extensions.md)

- [特性参数类型](attribute-parameter-types-cpp-component-extensions.md)

有关 Visual c + + 中签名程序集的信息，请参阅[强名称程序集 （程序集签名） (C + + CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)。

### <a name="requirements"></a>要求

编译器选项：`/clr`

### <a name="examples"></a>示例

下面的示例演示如何定义自定义属性。

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

下面的示例演示自定义特性的一些重要的功能。 例如，此示例显示了自定义特性的常见用法： 实例化的服务器的完全可向客户端描述自身。

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

`Object^`类型替换变量数据类型。 下面的示例定义采用的数组的自定义属性`Object^`作为参数。

特性参数必须是编译时常量;在大多数情况下，它们应是常量文字。

请参阅[typeid](typeid-cpp-component-extensions.md)有关如何从自定义特性块中返回的 system:: type 值的信息。

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

在运行时要求必须可序列化自定义特性类的公共部分。  创建自定义属性时，自定义特性的命名的参数仅限于编译时常量。  （将其视为一系列追加到您的类布局的元数据中的位。）

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

## <a name="see-also"></a>请参阅

[适用于.NET 和 UWP 组件扩展](component-extensions-for-runtime-platforms.md)