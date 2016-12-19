---
title: "如何：使用 .NET Framework 旋转图像 | Microsoft Docs"
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
  - "GDI+ [C++], 旋转图像"
  - "图形 [C++], 旋转图像"
ms.assetid: e32104d5-87d0-47a9-a22f-9bc835b7e8d7
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：使用 .NET Framework 旋转图像
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下面的代码示例演示如何使用 <xref:System.Drawing.Image?displayProperty=fullName> 类从磁盘中加载图像，将图像旋转 90 度并将其另存为新的 .jpg 文件。  
  
> [!NOTE]
>  GDI\+ 由 Windows XP 附带并且可作为 Windows NT 4.0 SP 6、Windows 2000、Windows 98 及 Windows Millennium Edition 的可再发行组件提供。  若要下载最新的可再发行组件，请 [http:\/\/go.microsoft.com\/fwlink\/?linkid\=11232](http://go.microsoft.com/fwlink/?linkid=11232)参见。  有关更多信息，请参见 [GDI\+](_gdiplus_GDI_start_cpp)。  
  
## 示例  
  
```  
#using <system.drawing.dll>  
  
using namespace System;  
using namespace System::Drawing;  
  
int main()  
{  
   Image^ image = Image::FromFile("SampleImage.jpg");  
   image->RotateFlip( RotateFlipType::Rotate90FlipNone );  
   image->Save("SampleImage_rotated.jpg");  
   return 0;  
}  
```  
  
## 请参阅  
 [使用 C\+\+\/CLI 进行 .NET 编程](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)