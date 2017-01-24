---
title: "如何：使用 .NET Framework 绘制形状 | Microsoft Docs"
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
  - "绘图, 形状"
  - "GDI+, 绘制形状"
  - "形状"
  - "形状, 绘图"
ms.assetid: ffad5ae7-6ef4-4550-8940-be3f209a101d
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：使用 .NET Framework 绘制形状
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下面的代码示例使用 <xref:System.Drawing.Graphics> 类来修改 <xref:System.Windows.Forms.Form.OnPaint%2A> 事件处理程序，以便检索指向主窗体的 <xref:System.Drawing.Graphics> 对象的指针。  然后，此指针将用于设置窗体的背景色，并通过使用 <xref:System.Drawing.Graphics.DrawLine%2A?displayProperty=fullName> 和 <xref:System.Drawing.Graphics.DrawArc%2A> 方法来绘制直线和弧形。  
  
> [!NOTE]
>  GDI\+ 由 Windows XP 附带并且可作为 Windows NT 4.0 SP 6、Windows 2000、Windows 98 及 Windows Me 的可再发行组件提供。  若要下载最新的可再发行组件，请 [http:\/\/go.microsoft.com\/fwlink\/?linkid\=11232](http://go.microsoft.com/fwlink/?linkid=11232)参见。  有关更多信息，请参见 [GDI\+](_gdiplus_GDI_start_cpp)。  
  
## 示例  
  
```  
#using <system.drawing.dll>  
using namespace System;  
using namespace System::Drawing;  
// ...  
protected:   
virtual Void Form1::OnPaint(PaintEventArgs^ pe ) override  
{  
   Graphics^ g = pe->Graphics;  
   g->Clear(Color::AntiqueWhite);  
  
   Rectangle rect = Form::ClientRectangle;  
   Rectangle smallRect;  
   smallRect.X = rect.X + rect.Width / 4;  
   smallRect.Y = rect.Y + rect.Height / 4;  
   smallRect.Width = rect.Width / 2;  
   smallRect.Height = rect.Height / 2;  
  
   Pen^ redPen = gcnew Pen(Color::Red);  
   redPen->Width = 4;  
   g->DrawLine(redPen, 0, 0, rect.Width, rect.Height);  
  
   Pen^ bluePen = gcnew Pen(Color::Blue);  
   bluePen->Width = 10;  
   g->DrawArc( bluePen, smallRect, 90, 270 );  
}  
```  
  
## 请参阅  
 [使用 C\+\+\/CLI 进行 .NET 编程](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)   
 [System::Drawing 命名空间](https://msdn.microsoft.com/en-us/library/system.drawing.aspx)