---
title: "用户定义的特性（C++ 组件扩展） | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "自定义特性, 扩展元数据"
  - "元数据, 扩展"
ms.assetid: 98b29048-a3ea-4698-8441-f149cdaec9fb
caps.latest.revision: 27
caps.handback.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 用户定义的特性（C++ 组件扩展）
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

自定义特性可扩展接口的元数据、类、结构、方法、参数或枚举。  
  
## 所有运行时  
 所有运行时支持自定义特性。  
  
## Windows Runtime — Windows 运行时  
 C\+\+\/CX 特性只支持属性，但未特性化构造函数或方法。  
  
### 备注  
  
### 要求  
 编译器选项：**\/ZW**  
  
## 公共语言运行时  
 自定义特性可扩展宿主元素的元数据。  有关详细信息，请参阅[特性](../Topic/Extending%20Metadata%20Using%20Attributes.md)。  
  
### 备注  
 本主题和语法存在的信息会取代在 [attribute](../windows/attribute.md)存在的信息。  
  
 通过定义类型并使 <xref:System.Attribute> 类型的基类和选项应用 <xref:System.AttributeUsageAttribute> 特性定义自定义属性。  
  
 例如，在 Microsoft Transaction Server \(MTS\) 1.0，与事务的行为，同步，负载平衡，依此类推通过自定义类型库 GUID 指定的插入使用 ODL 自定义属性。  因此，服务器 MTS 的客户可能通过读取类型库确定其属性。  在 .NET Framework 中，类型库的元数据，模拟是，并 ODL 自定义属性的模拟是自定义属性。  另外，读取类型库类似于使用类型上的反射。  
  
 有关详细信息，请参阅  
  
-   [特性目标](../windows/attribute-targets-cpp-component-extensions.md)  
  
-   [特性参数类型](../windows/attribute-parameter-types-cpp-component-extensions.md)  
  
 有关对 Visual C\+\+ 项目中的程序集进行签名的信息，请参见[强名称程序集（程序集签名）](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)。  
  
### 要求  
 编译器选项：**\/clr**  
  
### 示例  
 **示例**  
  
 下面的示例显示您可以如何定义特性：  
  
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
  
 下面的示例演示自定义属性一些重要功能。  例如，下面的示例演示自定义特性的常见用法：实例化自己可以描述对客户端的服务器。  
  
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
  
 **Output**  
  
  **服务优先级别 \= 0**  
 **服务访问编写为 \= Write**  
 **服务优先级别 \= 3**  
 **服务访问编写为 \= Write**  
 **服务优先级别 \= 1**  
 **服务访问 \= 读取** **示例**  
  
 Object^ 类型替换不同的数据类型。  下面的示例定义带有参数数组 Object^ 为的自定义属性。  
  
 特性参数必须是一个编译时常数；在许多情况下，它们应是常量文本。  
  
 参见 [typeid](../windows/typeid-cpp-component-extensions.md) 有关如何返回值信息的自定义属性的 System::Type 块。  
  
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
  
 运行时需要自定义属性类的公共部分必须是可序列化的。在创作自定义属性时，自定义特性的命名参数被限制为编译时常数。\(请考虑它作为位序列追加到元数据的类的布局。\)  
  
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
  
## 请参阅  
 [适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)