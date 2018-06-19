---
title: 实现插件体系结构 (C + + /cli CLI) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- plug-ins [C++]
- reflection [C++}, plug-ins
ms.assetid: 4f31e42b-78d1-48b9-8fdc-f28c75e8e77e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 4e001ef88af0727a994c309d45167787d3e6677b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33135208"
---
# <a name="how-to-implement-a-plug-in-component-architecture-using-reflection-ccli"></a>如何：使用反射实现插件组件体系结构 (C++/CLI)
下面的代码示例演示使用反射可以实现一个简单的"插件"体系结构。 第一个列表应用程序，且第二个插件。 应用程序是填充本身使用作为命令行自变量提供该插件 DLL 中任何基于窗体的类的多个文档窗体。  
  
 应用程序尝试加载使用提供程序集<xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName>方法。 如果成功，在程序集中的类型枚举使用<xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=fullName>方法。 每种类型会检查兼容性使用<xref:System.Type.IsAssignableFrom%2A?displayProperty=fullName>方法。 在此示例中，在提供的程序集中找到的类必须派生自<xref:System.Windows.Forms.Form>类才会被视为插件。  
  
 使用然后实例化兼容类<xref:System.Activator.CreateInstance%2A?displayProperty=fullName>方法，它接受<xref:System.Type>作为自变量并将指针返回到的新实例。 然后，每个新的实例已连接到该窗体，并显示。  
  
 请注意，<xref:System.Reflection.Assembly.Load%2A>方法不接受包括文件扩展名的程序集名称。 应用程序中的主函数修剪任何提供的扩展，因此下面的代码示例在任一情况下工作。  
  
## <a name="example"></a>示例  
 下面的代码定义的应用程序接受插件。程序集名称必须作为第一个自变量提供。 此程序集应包含至少一个公共<xref:System.Windows.Forms.Form>派生类型。  
  
```  
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
  
## <a name="example"></a>示例  
 下面的代码定义三个类派生自<xref:System.Windows.Forms.Form>。 当生成的程序集名称的名称传递到前面列表中的可执行文件时，这三个类的每个将发现并实例化，它们是所有未知的主机应用程序在编译时的情况下。  
  
```  
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
  
## <a name="see-also"></a>请参阅  
 [反射 (C++/CLI)](../dotnet/reflection-cpp-cli.md)