---
title: "反射 (C + + /cli CLI) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- typeid keyword [C++]
- reflection [C++}, about reflection
- metadata, reflection
- GetType method
- .NET Framework [C++], reflection
- data types [C++], reflection
- reflection [C++}
ms.assetid: 46b6ff4a-e441-4022-8892-78e69422f230
caps.latest.revision: "24"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: fab5bb3c912aeea2598189965d424ba4508cf5c8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="reflection-ccli"></a>反射 (C++/CLI)
反射允许要在运行时检查已知的数据类型。 反射允许数据类型的枚举中给定的程序集，而且不会发现给定类或值类型的成员。 这是不管是否已知或在编译时引用的类型。 这样，反射非常有用的功能，用于开发和代码管理工具。  
  
 请注意，提供的程序集名称是强名称 (请参阅[创建和使用具有强名称程序集](/dotnet/framework/app-domains/create-and-use-strong-named-assemblies))，其中包括程序集版本、 区域性和签名信息。 另请注意，在其中定义数据类型的命名空间的名称可以来检索，以及类的基类的名称。  
  
 若要访问反射功能的最常见方法是通过<xref:System.Object.GetType%2A>方法。 此方法由[system:: object](https://msdn.microsoft.com/en-us/library/system.object.aspx)，从所有垃圾回收的类都派生的。  
  
 如果使用生成.exe 只允许用 Visual c + + 编译器生成的.exe 上的反射**/clr: pure**或**/clr: safe**编译器选项。 **/clr:pure** 和 **/clr:safe** 编译器选项在 Visual Studio 2015 中已弃用。 请参阅[/clr （公共语言运行时编译）](../build/reference/clr-common-language-runtime-compilation.md)有关详细信息。  
  
 本节中的主题：  
  
-   [如何：使用反射实现插件组件体系结构 (C++/CLI)](../dotnet/how-to-implement-a-plug-in-component-architecture-using-reflection-cpp-cli.md)  
  
-   [如何：使用反射枚举程序集中的数据类型 (C++/CLI)](../dotnet/how-to-enumerate-data-types-in-assemblies-using-reflection-cpp-cli.md)  
  
 有关详细信息，请参阅[System.Reflection Namespace](https://msdn.microsoft.com/en-us/library/system.reflection.aspx)  
  
## <a name="example"></a>示例  
 `GetType`方法返回一个指向<xref:System.Type>类对象，其中介绍了当基于对象的类型。 (**类型**对象不包含任何特定于实例的信息。)其中一项是类型的可以按以下方式显示的完整名称：  
  
 请注意，类型名称包含在其中定义类型，它包括命名空间的完整范围，并且它显示在.NET 语法中，使用点号作为范围解析运算符。  
  
```  
// vcpp_reflection.cpp  
// compile with: /clr  
using namespace System;  
int main() {  
   String ^ s = "sample string";  
   Console::WriteLine("full type name of '{0}' is '{1}'", s, s->GetType());  
}  
```  
  
```Output  
full type name of 'sample string' is 'System.String'  
```  
  
## <a name="example"></a>示例  
 值类型可以与使用`GetType`函数，但必须首先装箱。  
  
```  
// vcpp_reflection_2.cpp  
// compile with: /clr  
using namespace System;  
int main() {  
   Int32 i = 100;   
   Object ^ o = i;  
   Console::WriteLine("type of i = '{0}'", o->GetType());  
}  
```  
  
```Output  
type of i = 'System.Int32'  
```  
  
## <a name="example"></a>示例  
 与`GetType`方法， [typeid](../windows/typeid-cpp-component-extensions.md)运算符返回指向的指针**类型**对象，所以此代码指示的类型名称**System.Int32**。 显示类型名称是反射的最基本功能，但可能更可取的做法是若要检查或发现枚举类型的有效值。 这可以通过使用静态**Enum::GetNames**函数，返回一个字符串，数组各包含一个以文本形式的枚举值。  下面的示例检索的描述的值枚举值的字符串数组**选项**(CLR) 枚举并将它们显示在循环中。  
  
 如果第四个选项添加到**选项**枚举，此代码将报告无需重新编译，即使该枚举定义在单独的程序集的新选项。  
  
```  
// vcpp_reflection_3.cpp  
// compile with: /clr  
using namespace System;  
  
enum class Options {   // not a native enum  
   Option1, Option2, Option3  
};  
  
int main() {  
   array<String^>^ names = Enum::GetNames(Options::typeid);  
  
   Console::WriteLine("there are {0} options in enum '{1}'",   
               names->Length, Options::typeid);  
  
   for (int i = 0 ; i < names->Length ; i++)  
      Console::WriteLine("{0}: {1}", i, names[i]);  
  
   Options o = Options::Option2;  
   Console::WriteLine("value of 'o' is {0}", o);  
}  
```  
  
```Output  
there are 3 options in enum 'Options'  
0: Option1  
1: Option2  
2: Option3  
value of 'o' is Option2  
```  
  
## <a name="example"></a>示例  
 `GetType`对象支持的成员，并且可以用于检查类型的属性数。 此代码检索并显示此信息的一些：  
  
```  
// vcpp_reflection_4.cpp  
// compile with: /clr  
using namespace System;  
int main() {  
   Console::WriteLine("type information for 'String':");  
   Type ^ t = String::typeid;  
  
   String ^ assemblyName = t->Assembly->FullName;  
   Console::WriteLine("assembly name: {0}", assemblyName);  
  
   String ^ nameSpace = t->Namespace;  
   Console::WriteLine("namespace: {0}", nameSpace);  
  
   String ^ baseType = t->BaseType->FullName;  
   Console::WriteLine("base type: {0}", baseType);  
  
   bool isArray = t->IsArray;  
   Console::WriteLine("is array: {0}", isArray);  
  
   bool isClass = t->IsClass;  
   Console::WriteLine("is class: {0}", isClass);  
}  
```  
  
```Output  
type information for 'String':  
assembly name: mscorlib, Version=1.0.5000.0, Culture=neutral,   
PublicKeyToken=b77a5c561934e089  
namespace: System  
base type: System.Object  
is array: False  
is class: True  
```  
  
## <a name="example"></a>示例  
 反射还允许的程序集内的类型和类中的成员的枚举。 若要演示此功能，请定义一个简单的类：  
  
```  
// vcpp_reflection_5.cpp  
// compile with: /clr /LD  
using namespace System;  
public ref class TestClass {  
   int m_i;  
public:  
   TestClass() {}  
   void SimpleTestMember1() {}  
   String ^ SimpleMember2(String ^ s) { return s; }   
   int TestMember(int i) { return i; }  
   property int Member {  
      int get() { return m_i; }  
      void set(int i) { m_i = i; }  
   }  
};  
```  
  
## <a name="example"></a>示例  
 如果上面的代码会编译成 DLL 调用 vcpp_reflection_6.dll，则可以使用反射检查此程序集的内容。 这涉及到使用静态反射 API 函数[Assembly::Load](https://msdn.microsoft.com/en-us/library/system.reflection.assembly.load.aspx)加载程序集。 此函数将返回的地址**程序集**然后即可查询有关的模块和中的类型的对象。  
  
 一旦反射系统成功加载程序集的数组**类型**对象检索与[Assembly::GetTypes](https://msdn.microsoft.com/en-us/library/system.reflection.assembly.gettypes.aspx)函数。 尽管在这种情况下，定义只有一个类，每个数组元素将包含有关类型不同，信息。 使用循环，每个**类型**此数组中查询有关使用的类型成员**Type::GetMembers**函数。 此函数返回的数组**MethodInfo**对象，每个对象，其中包含有关成员函数、 数据成员或类型中的属性的信息。  
  
 请注意，方法的列表包含函数显式定义中**TestClass**和函数隐式继承自**system:: object**类。 作为在.NET 中，而不是 Visual c + + 语法中所描述的一部分，属性显示为 get/set 函数访问的基础数据成员。 Get/set 函数显示在此列表作为常规方法。 不是由 Visual c + + 编译器通过公共语言运行时，支持反射。  
  
 尽管此代码用于检查你定义程序集，你还可以使用此代码检查.NET 程序集。 例如，如果对 mscorlib 更改 TestAssembly，你将看到每个类型和 mscorlib.dll 中定义的方法的列表。  
  
```  
// vcpp_reflection_6.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::IO;  
using namespace System::Reflection;  
int main() {  
   Assembly ^ a = nullptr;  
   try {  
      // load assembly -- do not use file extension  
      // will look for .dll extension first  
      // then .exe with the filename  
      a = Assembly::Load("vcpp_reflection_5");  
   }  
   catch (FileNotFoundException ^ e) {  
      Console::WriteLine(e->Message);  
      return -1;  
   }  
  
   Console::WriteLine("assembly info:");  
   Console::WriteLine(a->FullName);  
   array<Type^>^ typeArray = a->GetTypes();  
  
   Console::WriteLine("type info ({0} types):", typeArray->Length);  
  
   int totalTypes = 0;  
   int totalMembers = 0;  
   for (int i = 0 ; i < typeArray->Length ; i++) {  
      // retrieve array of member descriptions  
      array<MemberInfo^>^ member = typeArray[i]->GetMembers();  
  
      Console::WriteLine("  members of {0} ({1} members):",   
      typeArray[i]->FullName, member->Length);  
      for (int j = 0 ; j < member->Length ; j++) {  
         Console::Write("       ({0})",   
         member[j]->MemberType.ToString() );  
         Console::Write("{0}  ", member[j]);  
         Console::WriteLine("");  
         totalMembers++;  
      }  
      totalTypes++;  
   }  
   Console::WriteLine("{0} total types, {1} total members",  
   totalTypes, totalMembers);  
}  
```  
  
## <a name="see-also"></a>请参阅  
 [使用 C++/CLI (Visual C++) 进行 .NET 编程](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)