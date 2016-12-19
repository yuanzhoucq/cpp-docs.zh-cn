---
title: "如何：使用 .NET Framework 显示图像 | Microsoft Docs"
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
  - "GDI+ [C++], 显示图像"
  - "图形 [C++], 显示图像"
ms.assetid: c0eddfa1-4bd6-4af5-a533-1fa84b360325
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：使用 .NET Framework 显示图像
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下面的代码示例修改 OnPaint 事件处理程序，以便检索指向主窗体的 <xref:System.Drawing.Graphics> 对象的指针。  <xref:System.Windows.Forms.Form.OnPaint%2A> 函数用于极有可能使用 Visual Studio 应用程序向导创建的 Windows 窗体应用程序。  
  
 图像由 <xref:System.Drawing.Image> 类表示。  图像数据是使用 <xref:System.Drawing.Image.FromFile%2A?displayProperty=fullName> 方法从 .jpg 文件中加载的。  在向窗体中绘制图像之前，窗体将调整大小，以容纳图像。  图像的绘制是使用 <xref:System.Drawing.Graphics.DrawImage%2A?displayProperty=fullName> 方法执行的。  
  
 <xref:System.Drawing.Graphics> 和 <xref:System.Drawing.Image> 类都位于 <xref:System.Drawing?displayProperty=fullName> 命名空间中。  
  
> [!NOTE]
>  GDI\+ 由 Windows XP 附带并且可作为 Windows NT 4.0 SP 6、Windows 2000、Windows 98 及 Windows Me 的可再发行组件提供。  若要下载最新的可再发行组件，请 [http:\/\/go.microsoft.com\/fwlink\/?linkid\=11232](http://go.microsoft.com/fwlink/?linkid=11232)参见。  有关更多信息，请参见 [GDI\+](_gdiplus_GDI_start_cpp) 中的 GDI\+ SDK 文档。  
  
## 示例  
  
```  
#using <system.drawing.dll>  
  
using namespace System;  
using namespace System::Drawing;  
  
protected:  
virtual Void Form1::OnPaint(PaintEventArgs^ pe) override  
{  
    Graphics^ g = pe->Graphics;  
    Image^ image = Image::FromFile("SampleImage.jpg");  
    Form::ClientSize = image->Size;  
    g->DrawImage( image, 0, 0, image->Size.Width, image->Size.Height );  
}  
```  
  
## 请参阅  
 <xref:System.Drawing?displayProperty=fullName>   
 [使用 C\+\+\/CLI 进行 .NET 编程](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)