---
title: "CDC 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDC"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDC 类"
  - "coordinates in Windows 95/98 [C++]"
  - "device contexts [C++], CDC 类"
  - "screen coordinates in device contexts"
  - "Windows [C++], device contexts"
  - "Windows 95 [C++], 屏幕坐标"
  - "Windows 98 [C++], 屏幕坐标"
ms.assetid: 715b3334-cb2b-4c9c-8067-02eb7c66c8b2
caps.latest.revision: 21
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDC 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

定义设备上下文对象选件类。  
  
## 语法  
  
```  
class CDC : public CObject  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CDC::CDC](../Topic/CDC::CDC.md)|构造 `CDC` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CDC::AbortDoc](../Topic/CDC::AbortDoc.md)|停止当前打印作业，清除应用程序的设备编写的内容，因为最后调用 `StartDoc` 成员函数。|  
|[CDC::AbortPath](../Topic/CDC::AbortPath.md)|在设备上下文块并放弃任何路径。|  
|[CDC::AddMetaFileComment](../Topic/CDC::AddMetaFileComment.md)|将缓冲区的注释到指定的引发格式图元文件。|  
|[CDC::AlphaBlend](../Topic/CDC::AlphaBlend.md)|显示具有透明或半透明的像素的位图。|  
|[CDC::AngleArc](../Topic/CDC::AngleArc.md)|绘制线段和弧线，并将当前位置移动到终点弧线。|  
|[CDC::Arc](../Topic/CDC::Arc.md)|绘制椭圆弧。|  
|[CDC::ArcTo](../Topic/CDC::ArcTo.md)|绘制椭圆弧。  此功能类似于 `Arc`，除此之外，当前位置更新。|  
|[CDC::Attach](../Topic/CDC::Attach.md)|附加Windows设备上下文此 `CDC` 对象。|  
|[CDC::BeginPath](../Topic/CDC::BeginPath.md)|在设备上下文打开一个路径括号。|  
|[CDC::BitBlt](../Topic/CDC::BitBlt.md)|复制从指定的设备上下文的位图。|  
|[CDC::Chord](../Topic/CDC::Chord.md)|绘制个字符串\(椭圆和线段的交集绑定的一个闭合图形）。|  
|[CDC::CloseFigure](../Topic/CDC::CloseFigure.md)|在路径关闭一个非闭合图形。|  
|[CDC::CreateCompatibleDC](../Topic/CDC::CreateCompatibleDC.md)|创建与另一个设备上下文兼容的一个内存设备上下文。  可以使用已准备内存中的图像。|  
|[CDC::CreateDC](../Topic/CDC::CreateDC.md)|创建特定设备的设备上下文。|  
|[CDC::CreateIC](../Topic/CDC::CreateIC.md)|创建特定计算机的信息上下文。  这提供了有关计算机的捷径获取信息，而无需创建设备上下文。|  
|[CDC::DeleteDC](../Topic/CDC::DeleteDC.md)|删除Windows设备上下文与此 `CDC` 对象。|  
|[CDC::DeleteTempMap](../Topic/CDC::DeleteTempMap.md)|调用 `CWinApp` 空闲时间处理程序删除 `FromHandle`创建的任何临时 `CDC` 对象。  和分离设备上下文。|  
|[CDC::Detach](../Topic/CDC::Detach.md)|分离此 `CDC` 对象的Windows设备上下文。|  
|[CDC::DPtoHIMETRIC](../Topic/CDC::DPtoHIMETRIC.md)|将组件单位转换为 **HIMETRIC** 单元。|  
|[CDC::DPtoLP](../Topic/CDC::DPtoLP.md)|将组件单位为逻辑单元。|  
|[CDC::Draw3dRect](../Topic/CDC::Draw3dRect.md)|绘制一个三维矩形。|  
|[CDC::DrawDragRect](../Topic/CDC::DrawDragRect.md)|以便在拖动，清除和绘制一个矩形。|  
|[CDC::DrawEdge](../Topic/CDC::DrawEdge.md)|绘制矩形的边缘。|  
|[CDC::DrawEscape](../Topic/CDC::DrawEscape.md)|通过绘制图形设备接口\(GDI\)不直接可用的视频显示功能的访问。|  
|[CDC::DrawFocusRect](../Topic/CDC::DrawFocusRect.md)|绘制在用于的样式的一个矩形指示焦点。|  
|[CDC::DrawFrameControl](../Topic/CDC::DrawFrameControl.md)|绘制frame控件。|  
|[CDC::DrawIcon](../Topic/CDC::DrawIcon.md)|绘制图标。|  
|[CDC::DrawState](../Topic/CDC::DrawState.md)|显示图像并应用一种视觉效果指示状态。|  
|[CDC::DrawText](../Topic/CDC::DrawText.md)|draws格式化在指定的矩形的文本。|  
|[CDC::DrawTextEx](../Topic/CDC::DrawTextEx.md)|使用其他布局，Draws格式化在指定的矩形的文本。|  
|[CDC::Ellipse](../Topic/CDC::Ellipse.md)|绘制椭圆形。|  
|[CDC::EndDoc](../Topic/CDC::EndDoc.md)|关闭 `StartDoc` 成员函数开始的打印作业。|  
|[CDC::EndPage](../Topic/CDC::EndPage.md)|通知设备驱动程序页结束。|  
|[CDC::EndPath](../Topic/CDC::EndPath.md)|关闭一个路径括号并选择括号定义的路径到设备上下文。|  
|[CDC::EnumObjects](../Topic/CDC::EnumObjects.md)|枚举钢笔和画笔可在设备上下文。|  
|[CDC::Escape](../Topic/CDC::Escape.md)|允许应用于从特定设备不直接获得通过GDI的访问结构。  并允许对Windows转义的功能。  转义调用由应用程序转换和发送到设备驱动程序。|  
|[CDC::ExcludeClipRect](../Topic/CDC::ExcludeClipRect.md)|创建包含递减该指定矩形的现有的剪辑区域的一个新的剪辑区域。|  
|[CDC::ExcludeUpdateRgn](../Topic/CDC::ExcludeUpdateRgn.md)|防止绘制在窗口中无效区域中通过排除在窗口中更新区域从一个剪辑区域。|  
|[CDC::ExtFloodFill](../Topic/CDC::ExtFloodFill.md)|用当前画笔填充区域。  比 [CDC::FloodFill](../Topic/CDC::FloodFill.md) 成员函数以提供更大的灵活性。|  
|[CDC::ExtTextOut](../Topic/CDC::ExtTextOut.md)|编写在矩形区域内的字符字符串使用当前选定的字体。|  
|[CDC::FillPath](../Topic/CDC::FillPath.md)|使用当前画笔和多边形加载模式，在当前路径关闭任何非闭合图形和加载路径的内部。|  
|[CDC::FillRect](../Topic/CDC::FillRect.md)|使用一个特定的画笔，加载特定矩形。|  
|[CDC::FillRgn](../Topic/CDC::FillRgn.md)|创建一个指定的画笔填充给定区域。|  
|[CDC::FillSolidRect](../Topic/CDC::FillSolidRect.md)|用纯色填充矩形。|  
|[CDC::FlattenPath](../Topic/CDC::FlattenPath.md)|转换任何曲线所选的路径转换为当前设备上下文，并将各种曲线更改行顺序。|  
|[CDC::FloodFill](../Topic/CDC::FloodFill.md)|用当前画笔填充区域。|  
|[CDC::FrameRect](../Topic/CDC::FrameRect.md)|在矩形周围绘制边框。|  
|[CDC::FrameRgn](../Topic/CDC::FrameRgn.md)|使用画笔，在给定区域周围绘制边框。|  
|[CDC::FromHandle](../Topic/CDC::FromHandle.md)|返回指向 `CDC` 对象，同时使处理设备上下文。  如果一 `CDC` 对象未附加到句柄，一个临时 `CDC` 对象创建并附加。|  
|[CDC::GetArcDirection](../Topic/CDC::GetArcDirection.md)|返回设备上下文的当前弧线方向。|  
|[CDC::GetAspectRatioFilter](../Topic/CDC::GetAspectRatioFilter.md)|检索当前设置方面的筛选器的。|  
|[CDC::GetBkColor](../Topic/CDC::GetBkColor.md)|检索当前背景色。|  
|[CDC::GetBkMode](../Topic/CDC::GetBkMode.md)|检索背景模式。|  
|[CDC::GetBoundsRect](../Topic/CDC::GetBoundsRect.md)|返回指定设备上下文的当前累积的边框。|  
|[CDC::GetBrushOrg](../Topic/CDC::GetBrushOrg.md)|检索当前画笔的原点。|  
|[CDC::GetCharABCWidths](../Topic/CDC::GetCharABCWidths.md)|从当前字体检索宽度，在逻辑单位，在特定范围的连续的字符。|  
|[CDC::GetCharABCWidthsI](../Topic/CDC::GetCharABCWidthsI.md)|从当前truetype字体检索宽度，在逻辑单位，在指定范围的连续的标志符号索引。|  
|[CDC::GetCharacterPlacement](../Topic/CDC::GetCharacterPlacement.md)|检索信息各种类型的有关字符字符串的。|  
|[CDC::GetCharWidth](../Topic/CDC::GetCharWidth.md)|从当前字体检索连续的字符的宽度在特定的大小。|  
|[CDC::GetCharWidthI](../Topic/CDC::GetCharWidthI.md)|从当前字体检索宽度，使用逻辑坐标，在指定范围的连续的标志符号索引。|  
|[CDC::GetClipBox](../Topic/CDC::GetClipBox.md)|在当前剪辑边界周围检索最紧凑的边框的大小。|  
|[CDC::GetColorAdjustment](../Topic/CDC::GetColorAdjustment.md)|检索设备上下文的颜色调整值。|  
|[CDC::GetCurrentBitmap](../Topic/CDC::GetCurrentBitmap.md)|返回指向当前选定的 `CBitmap` 对象。|  
|[CDC::GetCurrentBrush](../Topic/CDC::GetCurrentBrush.md)|返回指向当前选定的 `CBrush` 对象。|  
|[CDC::GetCurrentFont](../Topic/CDC::GetCurrentFont.md)|返回指向当前选定的 `CFont` 对象。|  
|[CDC::GetCurrentPalette](../Topic/CDC::GetCurrentPalette.md)|返回指向当前选定的 `CPalette` 对象。|  
|[CDC::GetCurrentPen](../Topic/CDC::GetCurrentPen.md)|返回指向当前选定的 `CPen` 对象。|  
|[CDC::GetCurrentPosition](../Topic/CDC::GetCurrentPosition.md)|检索钢笔的当前位置\(以逻辑坐标）。|  
|[CDC::GetDCBrushColor](../Topic/CDC::GetDCBrushColor.md)|检索当前画笔颜色。|  
|[CDC::GetDCPenColor](../Topic/CDC::GetDCPenColor.md)|检索当前钢笔颜色。|  
|[CDC::GetDeviceCaps](../Topic/CDC::GetDeviceCaps.md)|检索指定的有关特定的显示设备的功能的设备特定的信息。|  
|[CDC::GetFontData](../Topic/CDC::GetFontData.md)|从可缩放字体文件检索字体规格信息。  检索的信息由指定偏移量与字体文件和表的信息的长度返回确定的。|  
|[CDC::GetFontLanguageInfo](../Topic/CDC::GetFontLanguageInfo.md)|返回有关当前选定的字体的信息指定的显示上下文。|  
|[CDC::GetGlyphOutline](../Topic/CDC::GetGlyphOutline.md)|检索概述曲线或位图概述字符的当前字体。|  
|[CDC::GetGraphicsMode](../Topic/CDC::GetGraphicsMode.md)|检索指定的设备上下文的当前关系图模式。|  
|[CDC::GetHalftoneBrush](../Topic/CDC::GetHalftoneBrush.md)|检索一个半音画笔。|  
|[CDC::GetKerningPairs](../Topic/CDC::GetKerningPairs.md)|检索运行边距调整为字体对指定的设备上下文当前选定的字符。|  
|[CDC::GetLayout](../Topic/CDC::GetLayout.md)|检索设备上下文\(DC\)的格式。  布局可以从左到右\(默认值\)或从右至左的\(反射）。|  
|[CDC::GetMapMode](../Topic/CDC::GetMapMode.md)|检索当前映射的模式。|  
|[CDC::GetMiterLimit](../Topic/CDC::GetMiterLimit.md)|返回设备上下文的基数限制。|  
|[CDC::GetNearestColor](../Topic/CDC::GetNearestColor.md)|检索最接近的逻辑颜色设置为特定设备可能表示的指定逻辑颜色。|  
|[CDC::GetOutlineTextMetrics](../Topic/CDC::GetOutlineTextMetrics.md)|检索truetype字体的指标信息。|  
|[CDC::GetOutputCharWidth](../Topic/CDC::GetOutputCharWidth.md)|从使用输出设备上下文的当前字体在字符的控件续组中检索各个字符的宽度。|  
|[CDC::GetOutputTabbedTextExtent](../Topic/CDC::GetOutputTabbedTextExtent.md)|计算字符字符串的宽度和高度在输出设备上下文。|  
|[CDC::GetOutputTextExtent](../Topic/CDC::GetOutputTextExtent.md)|计算文本行的宽度和高度在输出设备上下文使用当前的字体确定维度。|  
|[CDC::GetOutputTextMetrics](../Topic/CDC::GetOutputTextMetrics.md)|从输出设备上下文检索当前字体的指标。|  
|[CDC::GetPath](../Topic/CDC::GetPath.md)|检索定义线条的终点坐标，而在中选择到设备上下文的路径找到的曲线的控制点。|  
|[CDC::GetPixel](../Topic/CDC::GetPixel.md)|检索在指定的像素的颜色RGB值点。|  
|[CDC::GetPolyFillMode](../Topic/CDC::GetPolyFillMode.md)|检索当前多边形加载模式。|  
|[CDC::GetROP2](../Topic/CDC::GetROP2.md)|检索当前绘图模式。|  
|[CDC::GetSafeHdc](../Topic/CDC::GetSafeHdc.md)|返回 [CDC::m\_hDC](../Topic/CDC::m_hDC.md)，输出设备上下文。|  
|[CDC::GetStretchBltMode](../Topic/CDC::GetStretchBltMode.md)|检索当前位图拉伸的模式。|  
|[CDC::GetTabbedTextExtent](../Topic/CDC::GetTabbedTextExtent.md)|计算字符字符串的宽度和高度在属性设备上下文。|  
|[CDC::GetTextAlign](../Topic/CDC::GetTextAlign.md)|检索文本对齐标志。|  
|[CDC::GetTextCharacterExtra](../Topic/CDC::GetTextCharacterExtra.md)|检索当前设置数量的intercharacter间隔。|  
|[CDC::GetTextColor](../Topic/CDC::GetTextColor.md)|检索当前文本颜色。|  
|[CDC::GetTextExtent](../Topic/CDC::GetTextExtent.md)|计算文本行的宽度和高度在属性设备上下文使用当前的字体确定维度。|  
|[CDC::GetTextExtentExPointI](../Topic/CDC::GetTextExtentExPointI.md)|检索字符数在一个指定空间中容纳的一个指定字符串的并将这些字符中的每一个文本边界加载数组。|  
|[CDC::GetTextExtentPointI](../Topic/CDC::GetTextExtentPointI.md)|检索指定的数组的宽度和高度标志符号索引。|  
|[CDC::GetTextFace](../Topic/CDC::GetTextFace.md)|复制当前字体的字样名称到缓冲区中，一个Null终止的字符串。|  
|[CDC::GetTextMetrics](../Topic/CDC::GetTextMetrics.md)|从属性设备上下文检索当前字体的指标。|  
|[CDC::GetViewportExt](../Topic/CDC::GetViewportExt.md)|检索视区的x和y区域。|  
|[CDC::GetViewportOrg](../Topic/CDC::GetViewportOrg.md)|检索x和y坐标视区源。|  
|[CDC::GetWindow](../Topic/CDC::GetWindow.md)|返回窗口与显示设备上下文。|  
|[CDC::GetWindowExt](../Topic/CDC::GetWindowExt.md)|检索关联的窗口的x和y区域。|  
|[CDC::GetWindowOrg](../Topic/CDC::GetWindowOrg.md)|检索x和y坐标关联的窗口的源。|  
|[CDC::GetWorldTransform](../Topic/CDC::GetWorldTransform.md)|检索当前全局空间页空间转换。|  
|[CDC::GradientFill](../Topic/CDC::GradientFill.md)|填充矩形和一个gradating颜色的三角形结构。|  
|[CDC::GrayString](../Topic/CDC::GrayString.md)|draws在给定位置为灰色了\(灰色\)的文本。|  
|[CDC::HIMETRICtoDP](../Topic/CDC::HIMETRICtoDP.md)|转换 **HIMETRIC** 单元到组件单元中。|  
|[CDC::HIMETRICtoLP](../Topic/CDC::HIMETRICtoLP.md)|转换 **HIMETRIC** 单元到逻辑单元中。|  
|[CDC::IntersectClipRect](../Topic/CDC::IntersectClipRect.md)|通过合并当前区域和矩形的交集创建新的剪辑区域。|  
|[CDC::InvertRect](../Topic/CDC::InvertRect.md)|反转矩形的内容。|  
|[CDC::InvertRgn](../Topic/CDC::InvertRgn.md)|在区域反转颜色。|  
|[CDC::IsPrinting](../Topic/CDC::IsPrinting.md)|确定设备上下文是否对打印使用。|  
|[CDC::LineTo](../Topic/CDC::LineTo.md)|从当前位置绘制线条，但不包括，点。|  
|[CDC::LPtoDP](../Topic/CDC::LPtoDP.md)|转换逻辑单位为组件度量单位。|  
|[CDC::LPtoHIMETRIC](../Topic/CDC::LPtoHIMETRIC.md)|转换逻辑单位转换为 **HIMETRIC** 单元。|  
|[CDC::MaskBlt](../Topic/CDC::MaskBlt.md)|使用给定的掩码和光栅操作，将颜色数据进行源和目标位图。|  
|[CDC::ModifyWorldTransform](../Topic/CDC::ModifyWorldTransform.md)|使用指定的模式，更改设备上下文的世界变换。|  
|[CDC::MoveTo](../Topic/CDC::MoveTo.md)|移动当前位置。|  
|[CDC::OffsetClipRgn](../Topic/CDC::OffsetClipRgn.md)|特定于移动设备的剪辑区域。|  
|[CDC::OffsetViewportOrg](../Topic/CDC::OffsetViewportOrg.md)|修改视区原点相对坐标当前视区源。|  
|[CDC::OffsetWindowOrg](../Topic/CDC::OffsetWindowOrg.md)|修改窗口原点相对坐标当前窗口源。|  
|[CDC::PaintRgn](../Topic/CDC::PaintRgn.md)|创建一个选定的画笔填充区域。|  
|[CDC::PatBlt](../Topic/CDC::PatBlt.md)|创建一个位组合。|  
|[CDC::Pie](../Topic/CDC::Pie.md)|绘制一个扇形类型楔子。|  
|[CDC::PlayMetaFile](../Topic/CDC::PlayMetaFile.md)|播放指定的图元文件的内容在特定设备的。  `PlayMetaFile` 增强的版本显示在特定引发格式图元文件中存储的图片。  该图元文件来播放任意多次。|  
|[CDC::PlgBlt](../Topic/CDC::PlgBlt.md)|在源设备上下文执行位的位阻塞调用颜色数据从指定的矩形到指定的平行四边形在特定设备上下文。|  
|[CDC::PolyBezier](../Topic/CDC::PolyBezier.md)|绘制一个或多Bzier样条。  不使用当前位置或更新。|  
|[CDC::PolyBezierTo](../Topic/CDC::PolyBezierTo.md)|绘制一个或多Bzier样条，并将当前位置移动到终点最后Bzier样条。|  
|[CDC::PolyDraw](../Topic/CDC::PolyDraw.md)|绘制设置线段和Bzier样条。  此功能更新当前位置。|  
|[CDC::Polygon](../Topic/CDC::Polygon.md)|绘制由两个或多个多边形的点\(顶点\)连接由行。|  
|[CDC::Polyline](../Topic/CDC::Polyline.md)|绘制设置连接的行段指定点。|  
|[CDC::PolylineTo](../Topic/CDC::PolylineTo.md)|绘制一个或多条直线和移动当前位置移动到终点最后一行。|  
|[CDC::PolyPolygon](../Topic/CDC::PolyPolygon.md)|创建使用当前多边形加载模式，加载的两个或多个多边形。  多边形可能是相交或其能重叠。|  
|[CDC::PolyPolyline](../Topic/CDC::PolyPolyline.md)|绘制相连的行段多个级数。  当前位置不使用或此功能不更新。|  
|[CDC::PtVisible](../Topic/CDC::PtVisible.md)|给出的点是否在该剪辑区域中。|  
|[CDC::RealizePalette](../Topic/CDC::RealizePalette.md)|映射在当前逻辑添加到该调色板项添加到系统调色板。|  
|[CDC::Rectangle](../Topic/CDC::Rectangle.md)|使用当前画笔，绘制矩形使用将向当前钢笔并加载它。|  
|[CDC::RectVisible](../Topic/CDC::RectVisible.md)|确定给定矩形的任何部分是否处于剪辑区域之间。|  
|[CDC::ReleaseAttribDC](../Topic/CDC::ReleaseAttribDC.md)|释放 `m_hAttribDC`，属性设备上下文。|  
|[CDC::ReleaseOutputDC](../Topic/CDC::ReleaseOutputDC.md)|释放 `m_hDC`，输出设备上下文。|  
|[CDC::ResetDC](../Topic/CDC::ResetDC.md)|更新 `m_hAttribDC` 设备上下文。|  
|[CDC::RestoreDC](../Topic/CDC::RestoreDC.md)|还原设备上下文到以前状态保存。`SaveDC`。|  
|[CDC::RoundRect](../Topic/CDC::RoundRect.md)|绘制带圆角的一个矩形都使用将向当前钢笔并将使用当前画笔。|  
|[CDC::SaveDC](../Topic/CDC::SaveDC.md)|保存设备上下文的当前状态。|  
|[CDC::ScaleViewportExt](../Topic/CDC::ScaleViewportExt.md)|修改视区边界相对于当前值。|  
|[CDC::ScaleWindowExt](../Topic/CDC::ScaleWindowExt.md)|修改窗口区域相对于当前值。|  
|[CDC::ScrollDC](../Topic/CDC::ScrollDC.md)|水平和垂直滚动个矩形。|  
|[CDC::SelectClipPath](../Topic/CDC::SelectClipPath.md)|选择当前路径作为一个剪辑区域的设备上下文，了新的区域与任何现有的剪辑区域通过使用指定的模式。|  
|[CDC::SelectClipRgn](../Topic/CDC::SelectClipRgn.md)|通过使用指定的模式，将给定区域与当前剪辑区域。|  
|[CDC::SelectObject](../Topic/CDC::SelectObject.md)|选择绘制对象如钢笔的GDI。|  
|[CDC::SelectPalette](../Topic/CDC::SelectPalette.md)|选择逻辑调色板。|  
|[CDC::SelectStockObject](../Topic/CDC::SelectStockObject.md)|选择Windows提供的某个预定义的库存钢笔、画笔或字体。|  
|[CDC::SetAbortProc](../Topic/CDC::SetAbortProc.md)|将Windows调用一个由程序员提供的回调函数，则必须中止打印作业。|  
|[CDC::SetArcDirection](../Topic/CDC::SetArcDirection.md)|设置为弧线将使用的绘制方向，而矩形函数。|  
|[CDC::SetAttribDC](../Topic/CDC::SetAttribDC.md)|设置 `m_hAttribDC`，属性设备上下文。|  
|[CDC::SetBkColor](../Topic/CDC::SetBkColor.md)|设置当前背景色。|  
|[CDC::SetBkMode](../Topic/CDC::SetBkMode.md)|设置背景模式。|  
|[CDC::SetBoundsRect](../Topic/CDC::SetBoundsRect.md)|绑定矩形信息的累计指定的设备上下文。|  
|[CDC::SetBrushOrg](../Topic/CDC::SetBrushOrg.md)|为下一个画笔指定原点选中到设备上下文。|  
|[CDC::SetColorAdjustment](../Topic/CDC::SetColorAdjustment.md)|使用指定的值，设置设备上下文的颜色调整值。|  
|[CDC::SetDCBrushColor](../Topic/CDC::SetDCBrushColor.md)|设置当前画笔颜色。|  
|[CDC::SetDCPenColor](../Topic/CDC::SetDCPenColor.md)|设置当前钢笔颜色。|  
|[CDC::SetGraphicsMode](../Topic/CDC::SetGraphicsMode.md)|设置指定的设备上下文的当前关系图模式。|  
|[CDC::SetLayout](../Topic/CDC::SetLayout.md)|更改设备上下文\(DC\)的格式。|  
|[CDC::SetMapMode](../Topic/CDC::SetMapMode.md)|将当前映射的模式。|  
|[CDC::SetMapperFlags](../Topic/CDC::SetMapperFlags.md)|修改字体制图员使用的算法，该控制器包含字体的物理字体时。|  
|[CDC::SetMiterLimit](../Topic/CDC::SetMiterLimit.md)|设置斜接的长度限制对设备上下文连接。|  
|[CDC::SetOutputDC](../Topic/CDC::SetOutputDC.md)|设置 `m_hDC`，输出设备上下文。|  
|[CDC::SetPixel](../Topic/CDC::SetPixel.md)|设置指定的像素指向一个指定颜色的近似列表。|  
|[CDC::SetPixelV](../Topic/CDC::SetPixelV.md)|设置像素在指定坐标到指定的颜色的近似。  因为它不需要返回实际绘制，的点的颜色值`SetPixelV` 比 `SetPixel` express。|  
|[CDC::SetPolyFillMode](../Topic/CDC::SetPolyFillMode.md)|将多边形加载模式。|  
|[CDC::SetROP2](../Topic/CDC::SetROP2.md)|设置当前绘图模式。|  
|[CDC::SetStretchBltMode](../Topic/CDC::SetStretchBltMode.md)|将位图拉伸的模式。|  
|[CDC::SetTextAlign](../Topic/CDC::SetTextAlign.md)|设置文本对齐标志。|  
|[CDC::SetTextCharacterExtra](../Topic/CDC::SetTextCharacterExtra.md)|设置数量intercharacter间隔。|  
|[CDC::SetTextColor](../Topic/CDC::SetTextColor.md)|设置文本颜色。|  
|[CDC::SetTextJustification](../Topic/CDC::SetTextJustification.md)|添加空间到字符串的换行符。|  
|[CDC::SetViewportExt](../Topic/CDC::SetViewportExt.md)|将视区的x和y区域。|  
|[CDC::SetViewportOrg](../Topic/CDC::SetViewportOrg.md)|设置视区原点。|  
|[CDC::SetWindowExt](../Topic/CDC::SetWindowExt.md)|设置关联的窗口的x和y区域。|  
|[CDC::SetWindowOrg](../Topic/CDC::SetWindowOrg.md)|设置设备上下文的窗口原点。|  
|[CDC::SetWorldTransform](../Topic/CDC::SetWorldTransform.md)|设置当前全局空间页空间转换。|  
|[CDC::StartDoc](../Topic/CDC::StartDoc.md)|通知设备驱动程序新的打印作业启动。|  
|[CDC::StartPage](../Topic/CDC::StartPage.md)|通知设备驱动程序新的页。|  
|[CDC::StretchBlt](../Topic/CDC::StretchBlt.md)|从源矩形将位图和设备目标矩形，如果需要，拉伸或压缩位图以适应目标矩形的尺寸。|  
|[CDC::StrokeAndFillPath](../Topic/CDC::StrokeAndFillPath.md)|通过使用将向当前钢笔，使用当前画笔，在路径关闭任何非闭合图形，触击路径的轮廓，将加载其内部。|  
|[CDC::StrokePath](../Topic/CDC::StrokePath.md)|通过使用将向当前钢笔，呈现指定的路径。|  
|[CDC::TabbedTextOut](../Topic/CDC::TabbedTextOut.md)|编写在指定位置的字符串中，展开切换到在指定的值制表位位置。|  
|[CDC::TextOut](../Topic/CDC::TextOut.md)|编写在指定位置的字符字符串使用当前选定的字体。|  
|[CDC::TransparentBlt](../Topic/CDC::TransparentBlt.md)|从指定的源设备上下文调用颜色数据位块到目标设备上下文，呈现一个指定的颜色透明调用。|  
|[CDC::UpdateColors](../Topic/CDC::UpdateColors.md)|通过与当前颜色在工作区更新设备上下文的工作区根据逐像素基类型的系统调色板。|  
|[CDC::WidenPath](../Topic/CDC::WidenPath.md)|重新定义当前路径作为要绘制的区域，如果路径。抚摸了使用钢笔当前选定到设备上下文。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CDC::operator HDC](../Topic/CDC::operator%20HDC.md)|检索设备上下文的句柄。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CDC::m\_hAttribDC](../Topic/CDC::m_hAttribDC.md)|此 `CDC` 使用对象的属性设备上下文。|  
|[CDC::m\_hDC](../Topic/CDC::m_hDC.md)|此 `CDC` 对象使用的输出设备上下文。|  
  
## 备注  
 `CDC` 对象提供使用成员函数与设备上下文，例如一个显示或打印机，以及成员工作以显示上下文与窗口的工作区。  
  
 通过 `CDC` 对象的成员函数执行所有绘图。  选件类的设备上下文操作提供成员函数，用于绘制工具、类型安全的图形设备接口\(GDI\)对象选择和使用颜色和调色板。  它提供用于获取和设置绘图特性，映射工作，视区，工作windows区域，转换坐标，合作以区域，"剪切"，绘制还提供成员函数行和绘制简单形状、椭圆和多边形。  成员函数用于绘制的文本也提供工作，字体，使用打印机转义，滚动并播放图元文件。  
  
 若要使用 `CDC` 对象，请构造它，然后并行调用Windows函数使用设备上下文的其成员函数。  
  
> [!NOTE]
>  在Windows 95 \/98下，所有屏幕坐标被限制为16位。  因此，`int` 传递给 `CDC` 成员函数在该范围\(– 32768到32767必须在。  
  
 针对特定的用途，Microsoft基础选件类库提供从 `CDC` 派生的几选件类。  `CPaintDC` 封装对 `BeginPaint` 和 `EndPaint`。  `CClientDC` 管理一个显示上下文与窗口的工作区。  `CWindowDC` 管理一个显示上下文与整个窗口，包括其框架和控件。  `CMetaFileDC` 关联设备上下文与图元文件。  
  
 `CDC` 为反转设备上下文的格式提供两个成员函数，[GetLayout](../Topic/CDC::GetLayout.md) 和 [SetLayout](../Topic/CDC::SetLayout.md)，因此，不继承windows窗体中。  此类从右向左的orientation为区域性编写的应用程序是必需的，例如阿拉伯语或希伯来语，其中字符格式不是europe standard。  
  
 `CDC` 包含两个设备上下文，[m\_hDC](../Topic/CDC::m_hDC.md)，并 [m\_hAttribDC](../Topic/CDC::m_hAttribDC.md)，在 `CDC` 对象创建，引用同一计算机。  `CDC` 处理所有输出GDI调用 `m_hDC`，并且大多数属性GDI调用 `m_hAttribDC`。  （属性的示例调用是 `GetTextColor`，`SetTextColor` 输出，而是调用。）  
  
 例如，框架使用这两个设备上下文实现将输出发送到图元文件，在读取属性从物理计算机上 `CMetaFileDC` 对象。  打印预览该结构相同的方式实现。  您在特定的代码的一个类似的方式也可以使用两个设备上下文。  
  
 当您可能需要从 `m_hDC` 和 `m_hAttribDC` 设备上下文时，的文本指标信息有时。  以下两个功能提供此功能:  
  
|使用m\_hAttribDC|使用m\_hDC|  
|--------------------|--------------|  
|[GetTextExtent](../Topic/CDC::GetTextExtent.md)|[GetOutputTextExtent](../Topic/CDC::GetOutputTextExtent.md)|  
|[GetTabbedTextExtent](../Topic/CDC::GetTabbedTextExtent.md)|[GetOutputTabbedTextExtent](../Topic/CDC::GetOutputTabbedTextExtent.md)|  
|[GetTextMetrics](../Topic/CDC::GetTextMetrics.md)|[GetOutputTextMetrics](../Topic/CDC::GetOutputTextMetrics.md)|  
|[GetCharWidth](../Topic/CDC::GetCharWidth.md)|[GetOutputCharWidth](../Topic/CDC::GetOutputCharWidth.md)|  
  
 有关 `CDC`的更多信息，请参见 [设备上下文](../../mfc/device-contexts.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDC`  
  
## 要求  
 **标头：**afxwin.h  
  
## 请参阅  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CPaintDC Class](../../mfc/reference/cpaintdc-class.md)   
 [CWindowDC Class](../../mfc/reference/cwindowdc-class.md)   
 [CClientDC Class](../../mfc/reference/cclientdc-class.md)   
 [CMetaFileDC Class](../../mfc/reference/cmetafiledc-class.md)