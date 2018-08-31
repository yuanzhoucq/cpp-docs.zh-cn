---
title: 反射 (C + + CLI) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- typeid keyword [C++]
- reflection [C++}, about reflection
- metadata, reflection
- GetType method
- .NET Framework [C++], reflection
- data types [C++], reflection
- reflection [C++}
- plug-ins [C++]
- reflection [C++}, plug-ins
- assemblies [C++], enumerating data types in
- public types [C++]
- reflection [C++], external assemblies
- assemblies [C++]
- data types [C++], enumerating
- public members [C++]
ms.assetid: 46b6ff4a-e441-4022-8892-78e69422f230
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 0b5a352d10c1fd1f825cecbe3d6a1083f6efd425
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43212164"
---
# <a name="reflection-ccli"></a>反射 (C++/CLI)

反射允许在运行时检查已知的数据类型。 反射允许数据类型的枚举中给定的程序集，并且可以发现给定类或值类型的成员。 这是而不考虑是否已知或在编译时引用的类型，则返回 true。 这样，反射用于开发和管理工具的代码非常有用的功能。

请注意，提供的程序集名称是强名称 (请参阅[创建和使用具有强名称程序集](/dotnet/framework/app-domains/create-and-use-strong-named-assemblies))，其中包括程序集版本、 区域性和签名信息。 另请注意，在其中定义数据类型的命名空间的名称可以检索，以及类的基类的名称。

若要访问的反射功能的最常见方法是通过<xref:System.Object.GetType%2A>方法。 此方法提供的[system:: object](https://msdn.microsoft.com/library/system.object.aspx)，从垃圾收集的所有类都派生的。

> [!NOTE]
> 如果使用生成.exe 只允许对用 Visual c + + 编译器生成的.exe 的反射 **/clr: pure**或 **/clr: safe**编译器选项。 **/Clr: pure**并 **/clr: safe**编译器选项都不建议使用在 Visual Studio 2015 和 Visual Studio 2017 中不可用。 请参阅[/clr （公共语言运行时编译）](../build/reference/clr-common-language-runtime-compilation.md)有关详细信息。

有关详细信息，请参阅[System.Reflection Namespace](https://msdn.microsoft.com/library/system.reflection.aspx)

## <a name="example-gettype"></a>示例： GetType

`GetType`方法返回一个指向<xref:System.Type>类对象，它描述当该对象所基于的类型。 (**类型**对象不包含任何特定于实例的信息。)其中一项是类型的可以按如下所示显示的完整名称：

请注意类型名称包括在其中定义该类型，它包括在命名空间的完整范围，它显示在.NET 语法中，使用范围解析运算符作为一个点。

```cpp
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

## <a name="example-boxed-value-types"></a>示例： 装箱的值类型

值类型可以与使用`GetType`函数，但必须首先装箱。

```cpp
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

## <a name="example-typeid"></a>示例： typeid

如同`GetType`方法， [typeid](../windows/typeid-cpp-component-extensions.md)运算符将返回一个指向**类型**对象，因此此代码指示的类型名称**System.Int32**。 显示类型名称是最基本的反射功能，但可能会更有用的方法是检查或发现枚举类型的有效值。 这可以通过使用静态**Enum::GetNames**函数，它返回数组的字符串，每个都包含以文本形式的枚举值。  下面的示例检索有关的值枚举值的字符串数组**选项**(CLR) 枚举并将它们显示在循环中。

如果第四个选项添加到**选项**枚举，此代码将报告无需重新编译，即使该枚举在单独的程序集中定义的新选项。

```cpp
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

## <a name="example-gettype-members-and-properties"></a>示例： GetType 成员和属性

`GetType`对象支持的成员和可用于检查类型的属性数。 此代码检索并显示其中一些信息：

```cpp
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

## <a name="example-enumeration-of-types"></a>类型的示例： 枚举

反射还允许在一个程序集的类型和类中的成员的枚举。 若要演示此功能，定义一个简单的类：

```cpp
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

## <a name="example-inspection-of-assemblies"></a>程序集的示例： 检查

如果上面的代码编译为 DLL 调用 vcpp_reflection_6.dll，可以使用反射来检查此程序集的内容。 这涉及到使用静态反射 API 函数[Assembly::Load](https://msdn.microsoft.com/library/system.reflection.assembly.load.aspx)加载程序集。 此函数返回的地址**程序集**然后可以查询有关模块中的类型的对象。

反射系统已成功加载程序集的数组后**类型**与检索对象[Assembly::GetTypes](https://msdn.microsoft.com/library/system.reflection.assembly.gettypes.aspx)函数。 每个数组元素包含有关不同类型的信息，尽管这种情况下，定义一个类。 使用循环，每个**类型**此数组中查询有关使用的类型成员**Type::GetMembers**函数。 此函数返回的数组**MethodInfo**对象，每个对象，其中包含有关成员函数、 数据成员或类型中的属性的信息。

请注意，方法的列表包含函数显式中定义**TestClass**和函数隐式继承自**system:: object**类。 在.NET 中，而不是在 Visual c + + 语法中所描述的一部分，属性显示为 get/set 函数访问的基础数据成员。 Get/set 函数在此列表中显示为常规方法。 通过公共语言运行时，不是由 Visual c + + 编译器支持反射。

尽管此代码用于检查你定义的程序集，但您可以使用此代码检查.NET 程序集。 例如，如果对 mscorlib 更改 TestAssembly，然后将看到每个类型和方法在 mscorlib.dll 中定义的列表。

```cpp
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

## <a name="implement"></a> 如何： 实现使用反射的插件组件体系结构
下面的代码示例演示如何使用反射可以实现简单的"插件"体系结构。 列的第一个部分是应用程序，第二项是插件。 应用程序是填充本身使用作为命令行参数提供的插件 DLL 中找到任何基于窗体的类的多个文档窗体。  
  
 应用程序尝试加载提供的程序集使用<xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName>方法。 如果成功，在程序集中的类型进行枚举<xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=fullName>方法。 每个类型然后检查兼容性使用<xref:System.Type.IsAssignableFrom%2A?displayProperty=fullName>方法。 在此示例中，找到中提供的程序集的类必须派生自<xref:System.Windows.Forms.Form>类才会被视为一个插件。  
  
 使用然后实例化兼容类<xref:System.Activator.CreateInstance%2A?displayProperty=fullName>方法，用于接受<xref:System.Type>作为参数并返回一个指向新实例。 然后附加到窗体，显示每个新实例。  
  
 请注意，<xref:System.Reflection.Assembly.Load%2A>方法不接受包含文件扩展名的程序集名称。 因此下面的代码示例适用于在任一情况下，应用程序中的主函数裁剪掉任何提供的扩展。  
  
### <a name="example"></a>示例  
 下面的代码定义接受插件的应用程序。程序集名称必须作为第一个参数提供。 此程序集应包含至少一个公共<xref:System.Windows.Forms.Form>派生类型。  
  
```cpp
// plugin_application.cpp  
// compile with: /clr /c  
#using <system.dll>  
#using <system.drawing.dll>  
#using <system.windows.forms.dll>  
  
using namespace System;  
using namespace System::Windows::Forms;  
using namespace System::Reflection;  
  
ref class PluggableForm : public Form  {  
public:  
   PluggableForm() {}  
   PluggableForm(Assembly^ plugAssembly) {  
      Text = "plug-in example";  
      Size = Drawing::Size(400, 400);  
      IsMdiContainer = true;  
  
      array<Type^>^ types = plugAssembly->GetTypes( );  
      Type^ formType = Form::typeid;  
  
      for (int i = 0 ; i < types->Length ; i++) {  
         if (formType->IsAssignableFrom(types[i])) {  
            // Create an instance given the type description.  
            Form^ f = dynamic_cast<Form^> (Activator::CreateInstance(types[i]));  
            if (f) {  
               f->Text = types[i]->ToString();  
               f->MdiParent = this;  
               f->Show();  
            }  
         }  
      }  
   }  
};  
  
int main() {  
   Assembly^ a = Assembly::LoadFrom("plugin_application.exe");  
   Application::Run(gcnew PluggableForm(a));  
}  
```  
  
### <a name="example"></a>示例  
 下面的代码定义了三个类派生自<xref:System.Windows.Forms.Form>。 生成的程序集名称的名称传递给前面列表中的可执行文件，这三个类的每个将发现并实例化，它们是所有托管应用程序在编译时未知的情况。  
  
```cpp  
// plugin_assembly.cpp  
// compile with: /clr /LD  
#using <system.dll>  
#using <system.drawing.dll>  
#using <system.windows.forms.dll>  
  
using namespace System;  
using namespace System::Windows::Forms;  
using namespace System::Reflection;  
using namespace System::Drawing;  
  
public ref class BlueForm : public Form {  
public:  
   BlueForm() {  
      BackColor = Color::Blue;  
   }  
};  
  
public ref class CircleForm : public Form {  
protected:  
   virtual void OnPaint(PaintEventArgs^ args) override {  
      args->Graphics->FillEllipse(Brushes::Green, ClientRectangle);  
   }  
};  
  
public ref class StarburstForm : public Form {  
public:  
   StarburstForm(){  
      BackColor = Color::Black;  
   }  
protected:  
   virtual void OnPaint(PaintEventArgs^ args) override {  
      Pen^ p = gcnew Pen(Color::Red, 2);  
      Random^ r = gcnew Random( );  
      Int32 w = ClientSize.Width;  
      Int32 h = ClientSize.Height;  
      for (int i=0; i<100; i++) {  
         float x1 = w / 2;  
         float y1 = h / 2;  
         float x2 = r->Next(w);  
         float y2 = r->Next(h);  
         args->Graphics->DrawLine(p, x1, y1, x2, y2);  
      }  
   }  
};  
```  

## <a name="enumerate"></a> 如何： 枚举使用反射程序集中的数据类型
下面的代码演示的公共类型和成员使用枚举<xref:System.Reflection>。  
  
 给定的程序集名称，在本地目录中或在 GAC 中，尝试打开程序集并检索说明下面的代码。 如果成功，其公共成员显示每个类型。  
  
 请注意，<xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName>要求使用文件没有扩展名。 因此，使用"mscorlib.dll"作为命令行自变量时将失败，使用只是"mscorlib"将会生成.NET Framework 类型的显示。 如果未不提供任何程序集名称，代码将检测并报告 (此代码生成的 EXE) 的当前程序集中的类型。  
  
### <a name="example"></a>示例  
  
```cpp  
// self_reflection.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::Reflection;  
using namespace System::Collections;  
  
public ref class ExampleType {  
public:  
   ExampleType() {}  
   void Func() {}  
};  
  
int main() {  
   String^ delimStr = " ";  
   array<Char>^ delimiter = delimStr->ToCharArray( );  
   array<String^>^ args = Environment::CommandLine->Split( delimiter );  
  
// replace "self_reflection.exe" with an assembly from either the local  
// directory or the GAC  
   Assembly^ a = Assembly::LoadFrom("self_reflection.exe");  
   Console::WriteLine(a);  
  
   int count = 0;  
   array<Type^>^ types = a->GetTypes();  
   IEnumerator^ typeIter = types->GetEnumerator();  
  
   while ( typeIter->MoveNext() ) {  
      Type^ t = dynamic_cast<Type^>(typeIter->Current);  
      Console::WriteLine("   {0}", t->ToString());  
  
      array<MemberInfo^>^ members = t->GetMembers();  
      IEnumerator^ memberIter = members->GetEnumerator();  
      while ( memberIter->MoveNext() ) {  
         MemberInfo^ mi = dynamic_cast<MemberInfo^>(memberIter->Current);  
         Console::Write("      {0}", mi->ToString( ) );  
         if (mi->MemberType == MemberTypes::Constructor)  
            Console::Write("   (constructor)");  
  
         Console::WriteLine();  
      }  
      count++;  
   }  
   Console::WriteLine("{0} types found", count);  
}  
```  

## <a name="see-also"></a>请参阅

- [使用 C++/CLI (Visual C++) 进行 .NET 编程](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
