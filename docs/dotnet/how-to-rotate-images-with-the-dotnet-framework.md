---
title: 如何： 旋转使用.NET Framework 的映像 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- GDI+ [C++], rotating images
- graphics [C++], rotating images
ms.assetid: e32104d5-87d0-47a9-a22f-9bc835b7e8d7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 94290c05ecca9fc7211e2bc85640ec0308137804
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33129029"
---
# <a name="how-to-rotate-images-with-the-net-framework"></a>如何：使用 .NET Framework 旋转图像
下面的代码示例演示如何将<xref:System.Drawing.Image?displayProperty=fullName>类从磁盘加载图像、 旋转 90 度，并将其保存为新的.jpg 文件。  
  
## <a name="example"></a>示例  
  
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
  
## <a name="see-also"></a>请参阅  
 [使用 C++/CLI (Visual C++) 进行 .NET 编程](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)