---
title: "如何：使用反射实现插件组件体系结构 (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "插件 [C++]"
  - "反射 [C++], 插件"
ms.assetid: 4f31e42b-78d1-48b9-8fdc-f28c75e8e77e
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：使用反射实现插件组件体系结构 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下面的代码示例演示如何使用反射来实现简单的“插件”结构。  首先列出的是应用程序，然后列出的是插件。  应用程序是多文档窗体，使用在插件 DLL（作为命令行参数提供）中找到的任何基于窗体的类填充其本身。  
  
 应用程序尝试使用 <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName> 方法来加载提供的程序集。  如果成功，则将使用 <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=fullName> 方法枚举该程序集中的类型。  然后使用 <xref:System.Type.IsAssignableFrom%2A?displayProperty=fullName> 方法检查每种类型的兼容性。  在此示例中，在提供的程序集中找到的类必须从 <xref:System.Windows.Forms.Form> 类中派生以便限定为插件。  
  
 然后将使用 <xref:System.Activator.CreateInstance%2A?displayProperty=fullName> 方法实例化兼容的类，该方法将 <xref:System.Type> 作为参数接受，并返回指向新实例的指针。  然后将每个新实例附加到窗体并进行显示。  
  
 请注意，<xref:System.Reflection.Assembly.Load%2A> 方法不接受包含文件扩展名的程序集名称。  应用程序中的主函数剪裁掉任何提供的扩展名，因此下面的代码示例可在其中任何一种情况下工作。  
  
## 示例  
 以下代码定义接受插件的应用程序。  程序集名称必须作为第一个参数提供。  此程序集应至少包含一个公共 <xref:System.Windows.Forms.Form> 派生类型。  
  
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
  
## 示例  
 以下代码定义了从 <xref:System.Windows.Forms.Form> 派生的三个类。  将生成的程序集名称传递到前面列表中的可执行文件时，尽管在编译时这三个类都不为宿主应用程序所知，但它们中的每一个类都将被发现并被实例化。  
  
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
  
## 请参阅  
 [反射](../dotnet/reflection-cpp-cli.md)