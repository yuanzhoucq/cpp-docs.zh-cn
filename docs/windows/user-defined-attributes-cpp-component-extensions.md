---
title: "用户定义的属性 （c + + 组件扩展） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- metadata, extending
- custom attributes, extending metadata
ms.assetid: 98b29048-a3ea-4698-8441-f149cdaec9fb
caps.latest.revision: "27"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9d974e8526f983801ed011520f7f78ff8c6cb564
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="user-defined-attributes--c-component-extensions"></a>用户定义的特性（C++ 组件扩展）
自定义属性使您能够扩展接口、 类或结构、 方法、 参数或枚举的元数据。  
  
## <a name="all-runtimes"></a>所有运行时  
 所有运行时支持自定义属性。  
  
## <a name="windows-runtime"></a>Windows 运行时  
 C + + /cli CX 属性支持只有属性，但不是属性构造函数或方法。  
  
### <a name="remarks"></a>备注  
  
### <a name="requirements"></a>惠?  
 编译器选项： **/ZW**  
  
## <a name="common-language-runtime"></a>公共语言运行时  
 自定义特性使你可以扩展托管元素的元数据。 有关更多信息，请参阅[特性](/dotnet/standard/attributes/index)。  
  
### <a name="remarks"></a>备注  
 信息和本主题提供的语法旨在取代中提供的信息[属性](../windows/attribute.md)。  
  
 你可以定义的自定义特性定义类型，而使<xref:System.Attribute>基类类型和 （可选） 应用<xref:System.AttributeUsageAttribute>属性。  
  
 例如，在 Microsoft Transaction Server (MTS) 1.0，相关的行为时会事务，同步时，负载平衡，并通过插入类型库，通过使用 ODL 自定义特性的自定义 Guid 指定等等。 因此，MTS 服务器的客户端无法通过读取类型库确定其特征。 在.NET Framework 中，类型库的模拟元数据，且 ODL 自定义特性的模拟自定义属性。 此外，读取类型库是类似于对类型使用反射。  
  
 有关详细信息，请参阅  
  
-   [特性目标](../windows/attribute-targets-cpp-component-extensions.md)  
  
-   [特性参数类型](../windows/attribute-parameter-types-cpp-component-extensions.md)  
  
 有关 Visual c + + 中的签名程序集的信息，请参阅[强名称程序集 （程序集签名） (C + + /cli CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)。  
  
### <a name="requirements"></a>惠?  
 编译器选项： **/clr**  
  
### <a name="examples"></a>示例  
 **示例**  
  
 下面的示例演示如何定义自定义特性。  
  
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
  
 **示例**  
  
 下面的示例演示自定义特性的一些重要功能。 例如，此示例演示常见的自定义特性用法： 实例化完全可以向客户端描述本身的服务器。  
  
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
  
 **输出**  
  
```Output  
Service Priority = 0  
  
Service Access = Write  
  
Service Priority = 3  
  
Service Access = Write  
  
Service Priority = 1  
  
Service Access = Read  
```  
  
 **示例**  
  
 对象 ^ 类型替换的 variant 数据类型。 下面的示例定义采用对象的数组的自定义特性 ^ 作为参数。  
  
 特性自变量必须是编译时常量;在大多数情况下，它们应该是常量文字。  
  
 请参阅[typeid](../windows/typeid-cpp-component-extensions.md)有关如何从自定义特性块中返回的 system:: type 值的信息。  
  
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
  
 **示例**  
  
 运行时要求自定义特性类的公共部分必须是可序列化。  当编写自定义属性，自定义特性的命名自变量被限制为编译时常量。  （将它视为追加到你的元数据中的类布局的位序列。）  
  
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
 [适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)