---
title: "如何： 转换使用.NET Framework 的图像文件格式 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- GDI+ [C++], converting image file formats
- graphics [C++], converting image file formats
ms.assetid: 5d5384b0-b9b7-4262-b9ad-c4cb95f75ee4
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: eff94d00f92fe0a52162c986662209168974e072
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-convert-image-file-formats-with-the-net-framework"></a>如何：使用 .NET Framework 转换图像文件格式
下面的代码示例演示<xref:System.Drawing.Image?displayProperty=fullName>类和<xref:System.Drawing.Imaging.ImageFormat?displayProperty=fullName>枚举，用于将转换和保存图像文件。 下面的代码从.jpg 文件加载图像，然后将其保存在.gif 和.bmp 文件格式。  
  
> [!NOTE]
>  GDI + 随 Windows XP、 Windows Server 2003 和 Windows Vista，可用作 Windows 2000 的可再发行。 若要下载最新可再发行组件，请参阅[http://go.microsoft.com/fwlink/?linkid=11232](http://go.microsoft.com/fwlink/?linkid=11232)。   
  
## <a name="example"></a>示例  
  
```  
#using <system.drawing.dll>  
  
using namespace System;  
using namespace System::Drawing;  
using namespace System::Drawing::Imaging;  
  
int main()  
{  
   Image^ image = Image::FromFile("SampleImage.jpg");  
   image->Save("SampleImage.png", ImageFormat::Png);  
   image->Save("SampleImage.bmp", ImageFormat::Bmp);  
  
   return 0;  
}  
```  
  
## <a name="see-also"></a>另请参阅  
 <xref:System.Drawing>   
 [使用 C++/CLI (Visual C++) 进行 .NET 编程](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)