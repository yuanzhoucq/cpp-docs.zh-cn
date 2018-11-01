---
title: 图形操作 (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- GDI+ [C++]
- .NET Framework [C++], graphics
- images [C++], .NET Framework and
- GDI+ [C++], about graphics operations
- graphics [C++], .NET Framework and
- GDI+ [C++], displaying images
- graphics [C++], displaying images
- GDI+, drawing shapes
- drawing, shapes
- shapes
- shapes, drawing
- GDI+ [C++], rotating images
- graphics [C++], rotating images
- GDI+ [C++], converting image file formats
- graphics [C++], converting image file formats
ms.assetid: bba27228-b9b3-4c9c-b31c-a04b76702a95
ms.openlocfilehash: dd27fc603454d18f30fb367399e0ee18be74015e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50505425"
---
# <a name="graphics-operations-ccli"></a>图形操作 (C++/CLI)

演示如何使用 Windows SDK 的图像操作。

以下主题说明如何使用<xref:System.Drawing.Image?displayProperty=fullName>类来执行映像操作。

## <a name="display"></a> 使用.NET Framework 显示图像

下面的代码示例修改 OnPaint 事件处理程序来检索一个指向<xref:System.Drawing.Graphics>主窗体的对象。 <xref:System.Windows.Forms.Form.OnPaint%2A>函数适用于 Windows 窗体应用程序，最有可能创建了使用 Visual Studio 应用程序向导。

表示图像<xref:System.Drawing.Image>类。 从.jpg 文件使用加载的图像数据<xref:System.Drawing.Image.FromFile%2A?displayProperty=fullName>方法。 图像绘制到窗体之前，请在窗体调整大小以容纳新映像。 使用执行绘制图像<xref:System.Drawing.Graphics.DrawImage%2A?displayProperty=fullName>方法。

<xref:System.Drawing.Graphics>并<xref:System.Drawing.Image>类都位于<xref:System.Drawing?displayProperty=fullName>命名空间。

### <a name="example"></a>示例

```cpp
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

## <a name="draw"></a> 使用.NET Framework 绘制形状

下面的代码示例使用<xref:System.Drawing.Graphics>类来修改<xref:System.Windows.Forms.Form.OnPaint%2A>事件处理程序来检索一个指向<xref:System.Drawing.Graphics>主窗体的对象。 然后使用此指针设置窗体的背景色和绘制直线和弧线使用<xref:System.Drawing.Graphics.DrawLine%2A?displayProperty=fullName>和<xref:System.Drawing.Graphics.DrawArc%2A>方法。

### <a name="example"></a>示例

```cpp
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

## <a name="rotate"></a> 使用.NET Framework 旋转图像

下面的代码示例演示如何将<xref:System.Drawing.Image?displayProperty=fullName>类从磁盘加载图像、 将其旋转 90 度，并将其保存为新的.jpg 文件。

### <a name="example"></a>示例

```cpp
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

## <a name="convert"></a> 转换图像文件格式与.NET Framework

下面的代码示例演示<xref:System.Drawing.Image?displayProperty=fullName>类和<xref:System.Drawing.Imaging.ImageFormat?displayProperty=fullName>枚举，用于将转换和保存图像文件。 下面的代码从.jpg 文件加载图像，然后将其保存在.gif 和.bmp 文件格式。

### <a name="example"></a>示例

```cpp
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

## <a name="related-sections"></a>相关章节

[图形编程入门](/dotnet/framework/winforms/advanced/getting-started-with-graphics-programming)

[关于 GDI+ 托管代码](/dotnet/framework/winforms/advanced/about-gdi-managed-code)

## <a name="see-also"></a>请参阅

[使用 C++/CLI (Visual C++) 进行 .NET 编程](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)

<xref:System.Drawing>
