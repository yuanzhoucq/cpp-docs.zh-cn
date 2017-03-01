---
title: "CDC 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDC
dev_langs:
- C++
helpviewer_keywords:
- Windows [C++], device contexts
- Windows 95 [C++], screen coordinates
- device contexts [C++], CDC class
- screen coordinates in device contexts
- coordinates in Windows 95/98 [C++]
- Windows 98 [C++], screen coordinates
- CDC class
ms.assetid: 715b3334-cb2b-4c9c-8067-02eb7c66c8b2
caps.latest.revision: 21
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 80ccd3f8bed6bd74e22d4db5e176ee50528d3187
ms.lasthandoff: 02/24/2017

---
# <a name="cdc-class"></a>CDC 类
定义设备上下文对象的类。  
  
## <a name="syntax"></a>语法  
  
```  
class CDC : public CObject  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CDC::CDC](#cdc)|构造 `CDC` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CDC::AbortDoc](#abortdoc)|终止当前的打印作业，并擦除所有内容自上次调用的应用程序已写入到设备`StartDoc`成员函数。|  
|[CDC::AbortPath](#abortpath)|关闭并将丢弃设备上下文中的任何路径。|  
|[CDC::AddMetaFileComment](#addmetafilecomment)|将批注缓冲区中复制到指定的增强格式图元文件。|  
|[CDC::AlphaBlend](#alphablend)|显示具有透明或半透明的像素的位图。|  
|[CDC::AngleArc](#anglearc)|用于绘制直线线段和一段弧线，并将当前位置移到弧线的结束点。|  
|[CDC::Arc](#arc)|绘制椭圆弧。|  
|[CDC::ArcTo](#arcto)|绘制椭圆弧。 此函数是类似于`Arc`，只不过当前位置被更新。|  
|[CDC::Attach](#attach)|将 Windows 设备上下文附加到此`CDC`对象。|  
|[Cdc:: beginpath](#beginpath)|在设备上下文中打开一个路径方括号。|  
|[CDC::BitBlt](#bitblt)|从指定的设备上下文中复制位图。|  
|[CDC::Chord](#chord)|绘制弦 （受限于一个椭圆和一条线段的交集的闭合图形）。|  
|[CDC::CloseFigure](#closefigure)|关闭开放的图形路径中。|  
|[CDC::CreateCompatibleDC](#createcompatibledc)|创建与另一个设备上下文的内存设备上下文。 可用于准备在内存中的映像。|  
|[CDC::CreateDC](#createdc)|创建特定设备的设备上下文。|  
|[CDC::CreateIC](#createic)|创建特定设备的信息上下文。 这提供了一种以获取有关设备的信息，而无需创建设备上下文的快速方法。|  
|[CDC::DeleteDC](#deletedc)|删除与此关联的 Windows 设备上下文`CDC`对象。|  
|[CDC::DeleteTempMap](#deletetempmap)|由调用`CWinApp`空闲时间处理程序，以删除任何临时`CDC`创建的对象`FromHandle`。 此外将分离的设备上下文。|  
|[CDC::Detach](#detach)|从此的 Windows 设备上下文中分离`CDC`对象。|  
|[CDC::DPtoHIMETRIC](#dptohimetric)|将转换到的设备单位**HIMETRIC**单位。|  
|[CDC::DPtoLP](#dptolp)|将设备单位转换为逻辑单元。|  
|[CDC::Draw3dRect](#draw3drect)|绘制一个三维的矩形。|  
|[CDC::DrawDragRect](#drawdragrect)|清除并重新绘制一个矩形，如拖动它。|  
|[CDC::DrawEdge](#drawedge)|绘制一个矩形的边缘。|  
|[CDC::DrawEscape](#drawescape)|绘制视频显示器直接通过不可用的图形设备接口 (GDI) 的功能的访问。|  
|[CDC::DrawFocusRect](#drawfocusrect)|绘制一个矩形中用来指示焦点的样式。|  
|[CDC::DrawFrameControl](#drawframecontrol)|绘制一个框架控件。|  
|[CDC::DrawIcon](#drawicon)|绘制一个图标。|  
|[CDC::DrawState](#drawstate)|显示图像，并应用视觉效果以指示状态。|  
|[CDC::DrawText](#drawtext)|绘制格式化文本中指定的矩形。|  
|[CDC::DrawTextEx](#drawtextex)|绘制格式化文本中指定的矩形使用其他格式。|  
|[CDC::Ellipse](#ellipse)|绘制椭圆形。|  
|[CDC::EndDoc](#enddoc)|结束启动的打印作业`StartDoc`成员函数。|  
|[CDC::EndPage](#endpage)|通知的设备驱动程序结束一个页面。|  
|[CDC::EndPath](#endpath)|关闭路径括号，并选择到设备上下文由方括号定义的路径。|  
|[Cdc:: enumobjects](#enumobjects)|枚举钢笔和画笔在设备上下文中可用。|  
|[CDC::Escape](#escape)|允许应用程序访问的功能，就不来自特定设备通过 GDI 直接可用。 此外允许对 Windows 转义函数的访问。 转义调用应用程序进行的转换，并且发送到的设备驱动程序。|  
|[CDC::ExcludeClipRect](#excludecliprect)|创建新的剪辑区域，其中包含减去指定的矩形的现有剪辑区域。|  
|[CDC::ExcludeUpdateRgn](#excludeupdatergn)|通过从剪辑区域排除在窗口中的更新的区域来防止无效窗口区域内的绘制。|  
|[CDC::ExtFloodFill](#extfloodfill)|使用当前画笔填充一块区域。 提供了更大的灵活性比[CDC::FloodFill](#floodfill)成员函数。|  
|[CDC::ExtTextOut](#exttextout)|将使用当前所选的字体中的矩形区域中的一个字符串。|  
|[CDC::FillPath](#fillpath)|关闭当前路径中的任何开放图形，并使用当前画笔和多边形填充模式填充的路径的内部。|  
|[CDC::FillRect](#fillrect)|通过使用特定的画笔填充给定的矩形。|  
|[CDC::FillRgn](#fillrgn)|用指定的画笔填充的特定区域。|  
|[CDC::FillSolidRect](#fillsolidrect)|使用纯色填充的矩形。|  
|[CDC::FlattenPath](#flattenpath)|转换到当前的设备上下文中，选择的路径中的任何曲线，并将每条曲线转换为行的序列。|  
|[CDC::FloodFill](#floodfill)|使用当前画笔填充一块区域。|  
|[CDC::FrameRect](#framerect)|绘制一个矩形周围的边框。|  
|[CDC::FrameRgn](#framergn)|使用画笔的特定区域周围绘制边框。|  
|[CDC::FromHandle](#fromhandle)|返回一个指向`CDC`对象时提供给设备上下文的句柄。 如果 `CDC` 对象未附加到该句柄，则会创建并附加一个临时 `CDC` 对象。|  
|[CDC::GetArcDirection](#getarcdirection)|返回设备上下文的当前弧方向。|  
|[CDC::GetAspectRatioFilter](#getaspectratiofilter)|检索当前的长宽比筛选器的设置。|  
|[CDC::GetBkColor](#getbkcolor)|检索当前的背景色。|  
|[CDC::GetBkMode](#getbkmode)|检索后台模式。|  
|[CDC::GetBoundsRect](#getboundsrect)|返回指定的设备上下文的当前累计边界矩形。|  
|[CDC::GetBrushOrg](#getbrushorg)|检索当前画笔的原点。|  
|[CDC::GetCharABCWidths](#getcharabcwidths)|检索的宽度，以逻辑单元的当前字体从给定范围中的连续字符。|  
|[CDC::GetCharABCWidthsI](#getcharabcwidthsi)|检索的宽度，以从当前的 TrueType 字体在指定范围中的连续标志符号索引的逻辑单元。|  
|[CDC::GetCharacterPlacement](#getcharacterplacement)|检索各种类型的一个字符的字符串的信息。|  
|[CDC::GetCharWidth](#getcharwidth)|从当前的字体中检索给定范围中的连续字符的小数部分的宽度。|  
|[CDC::GetCharWidthI](#getcharwidthi)|检索的宽度，以逻辑坐标中，从当前的字体在指定范围中的连续标志符号索引。|  
|[CDC::GetClipBox](#getclipbox)|检索当前的剪辑边界周围 tightest 边界的矩形的尺寸。|  
|[CDC::GetColorAdjustment](#getcoloradjustment)|检索设备上下文的颜色调整值。|  
|[CDC::GetCurrentBitmap](#getcurrentbitmap)|将指针返回到当前所选`CBitmap`对象。|  
|[CDC::GetCurrentBrush](#getcurrentbrush)|将指针返回到当前所选`CBrush`对象。|  
|[CDC::GetCurrentFont](#getcurrentfont)|将指针返回到当前所选`CFont`对象。|  
|[CDC::GetCurrentPalette](#getcurrentpalette)|将指针返回到当前所选`CPalette`对象。|  
|[CDC::GetCurrentPen](#getcurrentpen)|将指针返回到当前所选`CPen`对象。|  
|[CDC::GetCurrentPosition](#getcurrentposition)|检索笔的当前位置 （以逻辑坐标表示）。|  
|[CDC::GetDCBrushColor](#getdcbrushcolor)|检索当前画笔的颜色。|  
|[CDC::GetDCPenColor](#getdcpencolor)|检索当前的钢笔颜色。|  
|[CDC::GetDeviceCaps](#getdevicecaps)|检索指定的类型的给定的显示设备的功能有关的特定于设备的信息。|  
|[CDC::GetFontData](#getfontdata)|从可缩放字体文件检索字体度量信息。 指定的偏移量到字体文件和要返回的信息的长度以标识要检索的信息。|  
|[CDC::GetFontLanguageInfo](#getfontlanguageinfo)|返回有关指定的显示上下文的当前选定字体的信息。|  
|[CDC::GetGlyphOutline](#getglyphoutline)|检索大纲曲线或大纲中的字符的当前字体的位图。|  
|[CDC::GetGraphicsMode](#getgraphicsmode)|检索指定的设备上下文的当前图形模式。|  
|[CDC::GetHalftoneBrush](#gethalftonebrush)|检索一个半色调画笔。|  
|[CDC::GetKerningPairs](#getkerningpairs)|检索字距调整对指定的设备上下文中当前选定的字体的字符。|  
|[CDC::GetLayout](#getlayout)|检索设备上下文 (DC) 的布局。 布局可以既左到右 （默认值） 或从右到左 （镜像）。|  
|[CDC::GetMapMode](#getmapmode)|检索当前的映射模式。|  
|[CDC::GetMiterLimit](#getmiterlimit)|返回设备上下文的斜角限制。|  
|[CDC::GetNearestColor](#getnearestcolor)|检索指定的逻辑颜色可以表示给定的设备到最接近的逻辑颜色。|  
|[CDC::GetOutlineTextMetrics](#getoutlinetextmetrics)|检索指标 TrueType 字体的字体信息。|  
|[CDC::GetOutputCharWidth](#getoutputcharwidth)|从当前字体使用输出的设备上下文中检索一组连续的字符中的单个字符的宽度。|  
|[CDC::GetOutputTabbedTextExtent](#getoutputtabbedtextextent)|计算的宽度和高度的输出设备上下文的字符串。|  
|[CDC::GetOutputTextExtent](#getoutputtextextent)|计算宽度，并使用当前的字体来确定维度的输出设备上下文上的文本行的高度。|  
|[CDC::GetOutputTextMetrics](#getoutputtextmetrics)|从输出设备上下文中检索当前字体的度量值。|  
|[CDC::GetPath](#getpath)|检索定义的终结点的直线和曲线路径选入设备上下文中找到的控点的坐标。|  
|[CDC::GetPixel](#getpixel)|检索指定点处的像素的 RGB 颜色值。|  
|[CDC::GetPolyFillMode](#getpolyfillmode)|检索当前的多边形填充模式。|  
|[CDC::GetROP2](#getrop2)|检索当前绘图模式。|  
|[CDC::GetSafeHdc](#getsafehdc)|返回[CDC::m_hDC](#m_hdc)，输出设备上下文。|  
|[CDC::GetStretchBltMode](#getstretchbltmode)|检索当前的位图拉伸模式。|  
|[CDC::GetTabbedTextExtent](#gettabbedtextextent)|计算的宽度和高度属性设备上下文的字符串。|  
|[CDC::GetTextAlign](#gettextalign)|检索文本对齐方式的标志。|  
|[CDC::GetTextCharacterExtra](#gettextcharacterextra)|检索已 intercharacter 间距量的当前设置。|  
|[CDC::GetTextColor](#gettextcolor)|检索当前的文本颜色。|  
|[CDC::GetTextExtent](#gettextextent)|计算宽度，并使用当前的字体来确定维度的属性设备上下文上的文本行的高度。|  
|[CDC::GetTextExtentExPointI](#gettextextentexpointi)|检索指定字符串将使其容纳在指定的空间，这些字符的每个文本范围与填充数组中的字符数。|  
|[CDC::GetTextExtentPointI](#gettextextentpointi)|检索的宽度和高度指定的标志符号索引数组。|  
|[CDC::GetTextFace](#gettextface)|以 null 结尾的字符串复制到缓冲区的当前字体的字体名称。|  
|[CDC::GetTextMetrics](#gettextmetrics)|从属性的设备上下文中检索当前字体的度量值。|  
|[CDC::GetViewportExt](#getviewportext)|检索 x-和 y 的范围内的视区。|  
|[CDC::GetViewportOrg](#getviewportorg)|检索视区原点 x 和 y 坐标。|  
|[CDC::GetWindow](#getwindow)|返回与显示设备上下文关联的窗口。|  
|[CDC::GetWindowExt](#getwindowext)|检索 x-和 y 的扩展盘区的关联窗口中。|  
|[CDC::GetWindowOrg](#getwindoworg)|检索的源关联的窗口的 x 和 y 坐标。|  
|[CDC::GetWorldTransform](#getworldtransform)|检索页面空间转换到的当前世界空间。|  
|[CDC::GradientFill](#gradientfill)|用 gradating 颜色填充矩形和三角形结构。|  
|[Cdc:: graystring](#graystring)|绘制变灰 （灰色） 中的给定位置的文本。|  
|[CDC::HIMETRICtoDP](#himetrictodp)|将转换**HIMETRIC**设备单位为单位。|  
|[CDC::HIMETRICtoLP](#himetrictolp)|将转换**HIMETRIC**分成逻辑单元的单元。|  
|[CDC::IntersectClipRect](#intersectcliprect)|通过为当前区域和一个矩形的交集创建新的剪辑区域。|  
|[CDC::InvertRect](#invertrect)|反转矩形的内容。|  
|[CDC::InvertRgn](#invertrgn)|反转区域中的颜色。|  
|[CDC::IsPrinting](#isprinting)|确定是否正在使用的设备上下文进行打印。|  
|[CDC::LineTo](#lineto)|从当前位置到，但不是包括、 一个点绘制的直线。|  
|[CDC::LPtoDP](#lptodp)|将设备单位转换为逻辑单元。|  
|[CDC::LPtoHIMETRIC](#lptohimetric)|将转换到逻辑单元**HIMETRIC**单位。|  
|[CDC::MaskBlt](#maskblt)|将组合使用给定的掩码和光栅操作的源和目标位图的颜色数据。|  
|[CDC::ModifyWorldTransform](#modifyworldtransform)|更改为使用指定的模式的设备上下文的世界变换。|  
|[CDC::MoveTo](#moveto)|将当前位置的移动。|  
|[CDC::OffsetClipRgn](#offsetcliprgn)|将移动给定设备的剪辑区域。|  
|[CDC::OffsetViewportOrg](#offsetviewportorg)|修改视区原点相对于当前视区原点坐标。|  
|[CDC::OffsetWindowOrg](#offsetwindoworg)|修改窗口原点相对于当前窗口起始地址的坐标。|  
|[CDC::PaintRgn](#paintrgn)|使用选择的画笔填充区域。|  
|[CDC::PatBlt](#patblt)|创建一个位模式。|  
|[CDC::Pie](#pie)|绘制饼形楔形。|  
|[CDC::PlayMetaFile](#playmetafile)|在给定的设备上播放指定的图元文件的内容。 增强的版本`PlayMetaFile`显示存储在给定的增强格式图元文件中的图片。 任意数量的时间就可以播放图元文件。|  
|[CDC::PlgBlt](#plgblt)|来自源设备上下文中指定的矩形执行颜色数据的位的位块传输到给定的设备上下文中指定的平行四边形。|  
|[CDC::PolyBezier](#polybezier)|绘制一个或多个 Bzier 样条。 当前的位置不使用也不更新。|  
|[CDC::PolyBezierTo](#polybezierto)|绘制一个或多个 Bzier 样条，并将当前位置移到最后一个 Bzier 样条曲线的结束点。|  
|[CDC::PolyDraw](#polydraw)|绘制直线线段和 Bzier 样条的一组。 此函数更新当前位置。|  
|[CDC::Polygon](#polygon)|绘制多边形包含两个或多个点 （顶点） 由直线连接。|  
|[CDC::Polyline](#polyline)|绘制一组连接的指定的点的直线线段。|  
|[CDC::PolylineTo](#polylineto)|绘制一个或多个直线，并将当前位置移到最后一行的结束点。|  
|[CDC::PolyPolygon](#polypolygon)|创建两个或多个使用当前的多边形填充模式填充的多边形。 多边形可能是不相互连接，或者它们可能会重叠。|  
|[CDC::PolyPolyline](#polypolyline)|绘制多个系列相连的线段。 当前的位置不使用也不更新此函数。|  
|[CDC::PtVisible](#ptvisible)|指定给定的点是否是剪辑区域内。|  
|[CDC::RealizePalette](#realizepalette)|将当前的逻辑调色板中的调色板条目映射到系统调色板。|  
|[CDC::Rectangle](#rectangle)|使用当前笔绘制一个矩形，并使用当前画笔进行填充。|  
|[CDC::RectVisible](#rectvisible)|确定给定的任何的矩形部分的剪辑区域内是否存在于。|  
|[CDC::ReleaseAttribDC](#releaseattribdc)|版本`m_hAttribDC`，属性的设备上下文。|  
|[CDC::ReleaseOutputDC](#releaseoutputdc)|版本`m_hDC`，输出设备上下文。|  
|[CDC::ResetDC](#resetdc)|更新`m_hAttribDC`设备上下文。|  
|[CDC::RestoreDC](#restoredc)|将设备上下文恢复到以前的状态与保存`SaveDC`。|  
|[CDC::RoundRect](#roundrect)|绘制带有圆角使用当前笔并使用当前画笔填充的矩形。|  
|[CDC::SaveDC](#savedc)|保存的设备上下文的当前状态。|  
|[CDC::ScaleViewportExt](#scaleviewportext)|修改的视区范围相对于当前值。|  
|[CDC::ScaleWindowExt](#scalewindowext)|修改范围相对于当前值，该窗口。|  
|[CDC::ScrollDC](#scrolldc)|水平和垂直滚动的矩形的位数。|  
|[CDC::SelectClipPath](#selectclippath)|选择作为设备上下文中，使用指定的模式来组合具有任何现有的剪辑区域的新区域的剪辑区域的当前路径。|  
|[CDC::SelectClipRgn](#selectcliprgn)|通过使用指定的模式将组合为当前剪辑区域与给定的区域。|  
|[CDC::SelectObject](#selectobject)|选择一个 GDI 绘图对象，如钢笔。|  
|[CDC::SelectPalette](#selectpalette)|选择逻辑的调色板。|  
|[CDC::SelectStockObject](#selectstockobject)|选择其中一种预定义的股票钢笔、 画笔或由 Windows 提供的字体。|  
|[Cdc:: setabortproc](#setabortproc)|设置 Windows，如果必须中止打印作业将调用的由程序员提供的回调函数。|  
|[CDC::SetArcDirection](#setarcdirection)|绘制将方向设置为用于弧线和矩形功能。|  
|[CDC::SetAttribDC](#setattribdc)|集`m_hAttribDC`，属性的设备上下文。|  
|[CDC::SetBkColor](#setbkcolor)|设置当前的背景色。|  
|[CDC::SetBkMode](#setbkmode)|将后台模式设置。|  
|[CDC::SetBoundsRect](#setboundsrect)|控制边界矩形指定的设备上下文的信息的累计。|  
|[CDC::SetBrushOrg](#setbrushorg)|指定为选入设备上下文的下一步画笔的原点。|  
|[CDC::SetColorAdjustment](#setcoloradjustment)|设置使用指定的值的设备上下文的颜色调整值。|  
|[CDC::SetDCBrushColor](#setdcbrushcolor)|设置当前画笔的颜色。|  
|[CDC::SetDCPenColor](#setdcpencolor)|设置当前的钢笔颜色。|  
|[CDC::SetGraphicsMode](#setgraphicsmode)|设置指定的设备上下文的当前图形模式。|  
|[CDC::SetLayout](#setlayout)|设备上下文 (DC) 的布局更改。|  
|[CDC::SetMapMode](#setmapmode)|设置当前的映射模式。|  
|[CDC::SetMapperFlags](#setmapperflags)|更改时它映射到物理字体的逻辑字体的字体映射程序使用的算法。|  
|[CDC::SetMiterLimit](#setmiterlimit)|设置的设备上下文的斜接联接的长度的限制。|  
|[CDC::SetOutputDC](#setoutputdc)|集`m_hDC`，输出设备上下文。|  
|[CDC::SetPixel](#setpixel)|将像素设置为指定的颜色最接近的近似的指定点处。|  
|[CDC::SetPixelV](#setpixelv)|在指定坐标对指定的颜色最接近的近似设置像素。 `SetPixelV`快于`SetPixel`因为它不需要返回实际绘制的点的颜色值。|  
|[CDC::SetPolyFillMode](#setpolyfillmode)|将多边形的填充模式设置。|  
|[CDC::SetROP2](#setrop2)|设置当前绘图模式。|  
|[CDC::SetStretchBltMode](#setstretchbltmode)|设置位图拉伸模式。|  
|[CDC::SetTextAlign](#settextalign)|设置文本对齐方式的标志。|  
|[CDC::SetTextCharacterExtra](#settextcharacterextra)|设置 intercharacter 间距的大小。|  
|[CDC::SetTextColor](#settextcolor)|设置文本颜色。|  
|[CDC::SetTextJustification](#settextjustification)|将空间添加到字符串中的中断字符。|  
|[CDC::SetViewportExt](#setviewportext)|设置 x-和 y 的范围内的视区。|  
|[CDC::SetViewportOrg](#setviewportorg)|设置视区原点。|  
|[CDC::SetWindowExt](#setwindowext)|设置 x-和 y 的扩展盘区的关联窗口中。|  
|[CDC::SetWindowOrg](#setwindoworg)|设置设备上下文的窗口原点。|  
|[CDC::SetWorldTransform](#setworldtransform)|将当前的世界空间设置为页面空间转换。|  
|[CDC::StartDoc](#startdoc)|通知的设备驱动程序启动新的打印作业。|  
|[CDC::StartPage](#startpage)|通知的设备驱动程序正在启动一个新页。|  
|[CDC::StretchBlt](#stretchblt)|将位图从一个源矩形和设备移动到目标矩形，可拉伸或压缩位图，如有必要以符合目标矩形的尺寸。|  
|[CDC::StrokeAndFillPath](#strokeandfillpath)|关闭任何开放的图形路径中，通过使用当前笔降临路径轮廓并通过使用当前画笔填充其内部。|  
|[CDC::StrokePath](#strokepath)|使用当前笔呈现指定的路径。|  
|[CDC::TabbedTextOut](#tabbedtextout)|将字符字符串中指定的位置，将选项卡扩展到指定数组中的制表位位置的值。|  
|[CDC::TextOut](#textout)|将使用当前所选的字体中指定位置处的字符字符串。|  
|[CDC::TransparentBlt](#transparentblt)|从指定的源设备上下文可将颜色数据位块传输到目标设备上下文，呈现透明在传输中指定的颜色。|  
|[CDC::UpdateColors](#updatecolors)|向系统调色板在逐像素基础上的工作区中更新通过匹配当前的设备上下文的工作区的颜色。|  
|[CDC::WidenPath](#widenpath)|将当前路径重新定义为将如果该路径已对其应用笔划使用实际选入设备上下文笔进行绘画的区域。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|说明|  
|----------|-----------------|  
|[CDC::operator HDC](#operator_hdc)|检索设备上下文的句柄。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CDC::m_hAttribDC](#m_hattribdc)|使用由此属性设备上下文`CDC`对象。|  
|[CDC::m_hDC](#m_hdc)|使用此输出设备上下文`CDC`对象。|  
  
## <a name="remarks"></a>备注  
 `CDC`对象提供用于为使用与客户端区域窗口的关联显示上下文使用的设备上下文，如显示器或打印机，以及成员的成员函数。  
  
 执行的函数的所有绘图经过成员`CDC`对象。 类提供成员函数对于设备上下文的操作，使用绘图工具，类型安全图形设备接口 (GDI) 对象选项，然后使用颜色和调色板。 它还提供用于获取和设置绘图属性，映射，并使用视区中，使用的窗口范围内，转换坐标、 使用区域，剪辑，绘制线条，并绘制简单形状、 椭圆和多边形的成员函数。 此外提供用于绘制文本、 使用的字体、 使用打印机转义符、 滚动和播放的图元文件的成员函数。  
  
 若要使用`CDC`对象，构造它，然后调用其成员的并行使用设备上下文的 Windows 函数的函数。  
  
> [!NOTE]
>  在 Windows 95/98 中，所有的屏幕坐标被限制为 16 位。 因此，`int`传递给`CDC`成员函数必须介于-32768 到 32767 之间。  
  
 为特定用途，Microsoft 基础类库提供了几个类派生自`CDC`。 `CPaintDC`封装对调用`BeginPaint`和`EndPaint`。 `CClientDC`管理与窗口的工作区相关联的显示上下文。 `CWindowDC`管理与整个窗口，包括其框架和控件显示上下文。 `CMetaFileDC`将设备上下文与图元文件相关联。  
  
 `CDC`提供了两个成员函数， [GetLayout](#getlayout)和[SetLayout](#setlayout)，用于反转设备上下文，不会继承其布局从窗口布局。 此类从右到左方向是对于区域性，例如阿拉伯语或希伯来语字符布局不是欧洲的标准编写的应用程序必需的。  
  
 `CDC`包含两个设备上下文、 [m_hDC](#m_hdc)和[m_hAttribDC](#m_hattribdc)，而后者在创建`CDC`对象，请参阅同一个设备。 `CDC`将定向到的所有输出 GDI 调用`m_hDC`和大多数属性 GDI 调用`m_hAttribDC`。 (属性调用的一个示例是`GetTextColor`，尽管`SetTextColor`是一个输出调用。)  
  
 例如，框架将使用以下两个设备上下文实现`CMetaFileDC`将输出发送到图元文件从物理设备读取的属性时的对象。 在框架中以类似的方式实现打印预览。 您还可以在特定于应用程序代码中以类似的方式使用两个设备上下文。  
  
 有的时间时，您可能需要这两处的度量值的文本信息`m_hDC`和`m_hAttribDC`设备上下文。 以下对函数提供此功能︰  
  
|使用 m_hAttribDC|使用 m_hDC|  
|-----------------------|-----------------|  
|[GetTextExtent](#gettextextent)|[GetOutputTextExtent](#getoutputtextextent)|  
|[GetTabbedTextExtent](#gettabbedtextextent)|[GetOutputTabbedTextExtent](#getoutputtabbedtextextent)|  
|[GetTextMetrics](#gettextmetrics)|[GetOutputTextMetrics](#getoutputtextmetrics)|  
|[GetCharWidth](#getcharwidth)|[GetOutputCharWidth](#getoutputcharwidth)|  
  
 有关详细信息`CDC`，请参阅[设备上下文](../../mfc/device-contexts.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDC`  
  
## <a name="requirements"></a>要求  
 **标头:** afxwin.h  
  
##  <a name="a-nameabortdoca--cdcabortdoc"></a><a name="abortdoc"></a>CDC::AbortDoc  
 终止当前的打印作业，并清除所有内容自上次调用写入到设备应用程序具有[StartDoc](#startdoc)成员函数。  
  
```  
int AbortDoc();
```  
  
### <a name="return-value"></a>返回值  
 值大于或等于如果成功，则为 0 或负值如果出现错误。 以下列表显示了常见的错误值及其含义︰  
  
- **SP_ERROR**时出现常规错误。  
  
- **SP_OUTOFDISK**用于后台打印，目前没有足够的磁盘空间并无更多空间将变为可用。  
  
- **SP_OUTOFMEMORY**没有足够的内存可用于后台打印。  
  
- **SP_USERABORT**用户终止通过打印管理器作业。  
  
### <a name="remarks"></a>备注  
 此成员函数将替换`ABORTDOC`打印机转义。  
  
 **AbortDoc**应该用于终止以下︰  
  
-   未指定中止函数使用的打印操作[SetAbortProc](#setabortproc)。  
  
-   尚未到达他们的名字的打印操作**NEWFRAME**或**NEXTBAND**转义调用。  
  
 如果应用程序会遭遇打印错误或已取消的打印操作，它不能尝试通过使用终止操作[EndDoc](#enddoc)或**AbortDoc**类的成员函数`CDC`。 GDI 自动终止了操作后，再返回的错误值。  
  
 如果应用程序显示一个对话框，允许用户取消打印操作，则必须调用**AbortDoc**之前销毁对话框。  
  
 如果已使用打印管理器开始打印作业，则调用**AbortDoc**清除整个后台处理作业 — 打印机接收执行任何操作。 如果不使用打印管理器开始打印作业，数据可能会被发送到打印机之前**AbortDoc**调用。 在这种情况下，打印机驱动程序将重置打印机 （如果可能），并关闭打印作业。  
  
### <a name="example"></a>示例  
  请参阅示例[CDC::StartDoc](#startdoc)。  
  
##  <a name="a-nameabortpatha--cdcabortpath"></a><a name="abortpath"></a>CDC::AbortPath  
 关闭并将丢弃设备上下文中的任何路径。  
  
```  
BOOL AbortPath();
```  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 如果在设备上下文中有一个开放路径方括号，路径括号已关闭，并且该路径将被丢弃。 如果在设备上下文中没有闭合的路径，路径将被放弃。  
  
##  <a name="a-nameaddmetafilecommenta--cdcaddmetafilecomment"></a><a name="addmetafilecomment"></a>CDC::AddMetaFileComment  
 将批注缓冲区中复制到指定的增强格式图元文件。  
  
```  
BOOL AddMetaFileComment(
    UINT nDataSize,  
    const BYTE* pCommentData);
```  
  
### <a name="parameters"></a>参数  
 *nDataSize*  
 以字节为单位指定注释缓冲区的长度。  
  
 *pCommentData*  
 指向包含注释的缓冲区。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 注释可以包含任何隐私信息 — 例如，图片和日期的源创建它。 注释应该开头数据应遵循的一个应用程序签名。 注释不应包含特定于位置的数据。 位置特定的数据指定的位置记录，它应该不会包括与因为一个图元文件可能会嵌入到另一个图元文件中。 此函数仅用于增强型图元文件。  
  
##  <a name="a-namealphablenda--cdcalphablend"></a><a name="alphablend"></a>CDC::AlphaBlend  
 调用该成员函数以显示具有透明或半透明的像素的位图。  
  
```  
BOOL AlphaBlend(
    int xDest,  
    int yDest,  
    int nDestWidth,  
    int nDestHeight,  
    CDC* pSrcDC,  
    int xSrc,  
    int ySrc,  
    int nSrcWidth,  
    int nSrcHeight,  
    BLENDFUNCTION blend);
```  
  
### <a name="parameters"></a>参数  
 `xDest`  
 指定使用逻辑单位，目标矩形的左上角的 x 坐标。  
  
 `yDest`  
 指定使用逻辑单位，目标矩形的左上角的 y 坐标。  
  
 `nDestWidth`  
 指定不使用逻辑单位，目标矩形的宽度。  
  
 `nDestHeight`  
 指定的高度，以目标矩形的逻辑单元。  
  
 `pSrcDC`  
 指向源设备上下文的指针。  
  
 `xSrc`  
 指定使用逻辑单位，源矩形的左上角的 x 坐标。  
  
 `ySrc`  
 指定使用逻辑单位，源矩形的左上角的 y 坐标。  
  
 `nSrcWidth`  
 指定不使用逻辑单位，源矩形的宽度。  
  
 `nSrcHeight`  
 指定使用逻辑单位，源矩形的高度。  
  
 *blend*  
 指定[BLENDFUNCTION](http://msdn.microsoft.com/library/windows/desktop/dd183393)结构。  
  
### <a name="return-value"></a>返回值  
 **TRUE**如果成功，否则为**FALSE**。  
  
### <a name="remarks"></a>备注  
 请参阅[AlphaBlend](http://msdn.microsoft.com/library/windows/desktop/dd183351)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]有关详细信息。  
  
##  <a name="a-nameanglearca--cdcanglearc"></a><a name="anglearc"></a>CDC::AngleArc  
 用于绘制直线线段和一段弧线。  
  
```  
BOOL AngleArc(
    int x,  
    int y,  
    int nRadius,  
    float fStartAngle,  
    float fSweepAngle);
```  
  
### <a name="parameters"></a>参数  
 *x*  
 指定圆的中心的逻辑 x 坐标值。  
  
 *y*  
 指定圆的中心的逻辑 y 坐标值。  
  
 *nRadius*  
 指定使用逻辑单位圆的半径。 此值必须是正数。  
  
 *fStartAngle*  
 以相对于 x 轴度为单位指定的开始角度。  
  
 *fSweepAngle*  
 指定以度为单位的起始角度相对的扫描角度。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 直线线段绘制从当前位置到弧线的起始位置。 弧绘制沿给定的半径和中心圆的周长。 通过给定的开始和扫描角度定义弧的长度。  
  
 `AngleArc`将当前位置移到弧线的结束点。 此函数绘制弧线可能看起来是椭圆，具体取决于当前的转换和映射模式。 绘制之前弧线，此函数将绘制直线线段从当前位置到弧线的起始位置。 通过建立与指定的中心点附近指定半径假想圆绘制弧。 通过从圆的 x 轴按逆时针方向测量的起始角度的度数确定弧线的起始点。 通过从起点按逆时针方向测量的扫描角度的度数位于同样到结束点。  
  
 如果扫描角度为 360 度大于弧是扫多次。 此函数使用当前的钢笔绘制线条。 不填充该图中。  
  
##  <a name="a-namearca--cdcarc"></a><a name="arc"></a>CDC::Arc  
 绘制椭圆弧。  
  
```  
BOOL Arc(
    int x1,  
    int y1,  
    int x2,  
    int y2,  
    int x3,  
    int y3,  
    int x4,  
    int y4);

 
BOOL Arc(
    LPCRECT lpRect,  
    POINT ptStart,  
    POINT ptEnd);
```  
  
### <a name="parameters"></a>参数  
 `x1`  
 指定 （使用逻辑单位） 的绑定矩形的左上角的 x 坐标。  
  
 `y1`  
 指定 （使用逻辑单位） 的绑定矩形的左上角的 y 坐标。  
  
 `x2`  
 指定的边框 （使用逻辑单位） 的右下角的 x 坐标。  
  
 `y2`  
 指定的边框 （使用逻辑单位） 的右下角的 y 坐标。  
  
 *x3*  
 指定定义弧的点的 x 坐标的起始位置 （使用逻辑单位）。 此时没有要将其完全置于弧。  
  
 `y3`  
 指定定义弧的点的 y 坐标的起始位置 （使用逻辑单位）。 此时没有要将其完全置于弧。  
  
 `x4`  
 指定定义 （使用逻辑单位） 的弧线的终结点的点的 x 坐标。 此时没有要将其完全置于弧。  
  
 `y4`  
 指定定义 （使用逻辑单位） 的弧线的终结点的点的 y 坐标。 此时没有要将其完全置于弧。  
  
 `lpRect`  
 指定的边框 （使用逻辑单位）。 您可以传递`LPRECT`或[CRect](../../atl-mfc-shared/reference/crect-class.md)为此参数的对象。  
  
 `ptStart`  
 指定定义弧的点 x 和 y 坐标的起始位置 （使用逻辑单位）。 此时没有要将其完全置于弧。 您可以传递[点](../../mfc/reference/point-structure1.md)结构或[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)为此参数的对象。  
  
 `ptEnd`  
 指定定义弧线的结束点 （使用逻辑单位） 的点 x 和 y 坐标。 此时没有要将其完全置于弧。 您可以传递**点**结构或`CPoint`为此参数的对象。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 通过使用函数绘制弧线是椭圆的由指定的边框定义的段。  
  
 圆弧的实际起始点是从通过指定的起始点的绑定矩形的中心绘制一条射线与椭圆的交点的点。 圆弧的实际结束点是从通过指定的结束点的绑定矩形的中心绘制一条射线与椭圆的交点的点。 以逆时针方向绘制弧。 由于一段弧线，不是闭合的图形，没有填充。 宽度和矩形的高度必须大于 2 个单位和小于 32767 个单位。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&29;](../../mfc/codesnippet/cpp/cdc-class_1.cpp)]  
  
##  <a name="a-namearctoa--cdcarcto"></a><a name="arcto"></a>CDC::ArcTo  
 绘制椭圆弧。  
  
```  
BOOL ArcTo(
    int x1,  
    int y1,  
    int x2,  
    int y2,  
    int x3,  
    int y3,  
    int x4,  
    int y4);

 
BOOL ArcTo(
    LPCRECT lpRect,  
    POINT ptStart,  
    POINT ptEnd);
```  
  
### <a name="parameters"></a>参数  
 `x1`  
 指定 （使用逻辑单位） 的绑定矩形的左上角的 x 坐标。  
  
 `y1`  
 指定 （使用逻辑单位） 的绑定矩形的左上角的 y 坐标。  
  
 `x2`  
 指定的边框 （使用逻辑单位） 的右下角的 x 坐标。  
  
 `y2`  
 指定的边框 （使用逻辑单位） 的右下角的 y 坐标。  
  
 *x3*  
 指定定义弧的点的 x 坐标的起始位置 （使用逻辑单位）。 此时没有要将其完全置于弧。  
  
 `y3`  
 指定定义弧的点的 y 坐标的起始位置 （使用逻辑单位）。 此时没有要将其完全置于弧。  
  
 `x4`  
 指定定义 （使用逻辑单位） 的弧线的终结点的点的 x 坐标。 此时没有要将其完全置于弧。  
  
 `y4`  
 指定定义 （使用逻辑单位） 的弧线的终结点的点的 y 坐标。 此时没有要将其完全置于弧。  
  
 `lpRect`  
 指定的边框 （使用逻辑单位）。 您可以将传递指向的指针[RECT](../../mfc/reference/rect-structure1.md)数据结构或[CRect](../../atl-mfc-shared/reference/crect-class.md)为此参数的对象。  
  
 `ptStart`  
 指定定义弧的点 x 和 y 坐标的起始位置 （使用逻辑单位）。 此时没有要将其完全置于弧。 您可以传递[点](../../mfc/reference/point-structure1.md)数据结构或[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)为此参数的对象。  
  
 `ptEnd`  
 指定定义弧线的结束点 （使用逻辑单位） 的点 x 和 y 坐标。 此时没有要将其完全置于弧。 您可以传递**点**数据结构或`CPoint`为此参数的对象。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 此函数是类似于`CDC::Arc`，只不过当前位置被更新。 点 ( `x1`， `y1`) 和 ( `x2`， `y2`) 指定的绑定矩形。 通过给定的绑定矩形而形成的椭圆定义的曲线弧。 圆弧逆时针延展 （默认弧方向） 从点相交的中心到边框中的径向一行 ( *x3*， `y3`)。 弧端点相交的中心到边框中的径向一行 ( `x4`， `y4`)。 如果起始点和结束点是相同的将绘制整个椭圆。  
  
 从当前位置到弧线的起始点绘制线条。 如果没有出现错误，则将当前位置设置为弧线的结束点。 使用当前笔; 绘制弧线未填写。  
  
##  <a name="a-nameattacha--cdcattach"></a><a name="attach"></a>CDC::Attach  
 使用此成员函数将附加`hDC`到`CDC`对象。  
  
```  
BOOL Attach(HDC hDC);
```  
  
### <a name="parameters"></a>参数  
 `hDC`  
 Windows 设备上下文。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 `hDC`中同时存储`m_hDC`，输出设备上下文中，然后在`m_hAttribDC`，属性的设备上下文。  
  
##  <a name="a-namebeginpatha--cdcbeginpath"></a><a name="beginpath"></a>Cdc:: beginpath  
 在设备上下文中打开一个路径方括号。  
  
```  
BOOL BeginPath();
```  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 打开一个路径括号后，应用程序可以开始调用 GDI 绘图函数来定义路径中存在的点。 应用程序可以通过调用关闭一个开放路径方括号`EndPath`成员函数。 在应用程序调用`BeginPath`，以前的任何路径将被丢弃。  
  
 请参阅[BeginPath](http://msdn.microsoft.com/library/windows/desktop/dd183363)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]有关定义路径中的点的绘图函数的列表。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&30;](../../mfc/codesnippet/cpp/cdc-class_2.cpp)]  
  
##  <a name="a-namebitblta--cdcbitblt"></a><a name="bitblt"></a>CDC::BitBlt  
 将源设备上下文的位图复制到此当前的设备上下文。  
  
```  
BOOL BitBlt(
    int x,  
    int y,  
    int nWidth,  
    int nHeight,  
    CDC* pSrcDC,  
    int xSrc,  
    int ySrc,  
    DWORD dwRop);
```  
  
### <a name="parameters"></a>参数  
 *x*  
 指定目标矩形的左上角的逻辑 x 坐标。  
  
 *y*  
 指定目标矩形的左上角的逻辑 y 坐标。  
  
 `nWidth`  
 指定目标矩形，源位图的宽度 （以逻辑单位）。  
  
 `nHeight`  
 指定目标矩形，源位图的高度 （以逻辑单位）。  
  
 `pSrcDC`  
 指向`CDC`对象，用于标识将被复制位图的设备上下文。 它必须是**NULL**如果*dwRop*指定不包含源光栅操作。  
  
 `xSrc`  
 指定的源位图的左上角的逻辑 x 坐标。  
  
 `ySrc`  
 指定的源位图的左上角的逻辑 y 坐标。  
  
 *dwRop*  
 指定要执行的光栅操作。 光栅操作代码定义 GDI 如何合并涉及当前画笔、 可能的源位图和目标位图的输出操作中的颜色。 请参阅[BitBlt](http://msdn.microsoft.com/library/windows/desktop/dd183370)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]有关的光栅操作代码的列表*dwRop*及其说明  
  
 光栅操作代码的完整列表，请参阅[有关光栅操作代码](http://msdn.microsoft.com/library/windows/desktop/dd162892)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 应用程序可以将 windows 或在字节边界，以确保客户端区域对齐`BitBlt`操作发生在字节对齐矩形上。 (设置**CS_BYTEALIGNWINDOW**或**CS_BYTEALIGNCLIENT**标志时注册窗口类。)  
  
 `BitBlt`在字节对齐矩形上的操作都是远远快于速度`BitBlt`上不是字节对齐的矩形的操作。 如果您想要指定类样式，例如您自己的设备上下文的字节对齐方式，您将需要注册窗口类而不是依赖 Microsoft 基础类来为您代劳。 使用全局函数[AfxRegisterWndClass](../../mfc/reference/application-information-and-management.md#afxregisterwndclass)。  
  
 GDI 转换`nWidth`和`nHeight`、 一次使用目标设备上下文中，以及一次使用源设备上下文。 如果生成的扩展盘区不匹配，GDI 将使用 Windows`StretchBlt`函数进行压缩或扩展所需的源位图。  
  
 如果目标、 源位图和模式位图没有相同的颜色格式，`BitBlt`函数将转换源位图和模式位图以与目标匹配的。 在转换过程中使用目标位图的前景色和背景颜色。  
  
 当`BitBlt`函数将单色位图转换为颜色，它会将白色位 (1) 设置为背景色，黑色位 (0) 为前景色。 使用目标设备上下文的前景色和背景颜色。 若要将彩色位图转换为单色，`BitBlt`将与背景色为白色的像素设置和其他所有像素都设置为黑色。 `BitBlt`使用彩色设备上下文的前景色和背景色来从颜色转换为单色。  
  
 请注意，并非所有的设备上下文支持`BitBlt`。 若要检查是否支持给定的设备上下文`BitBlt`，使用`GetDeviceCaps`成员函数，并指定**RASTERCAPS**索引。  
  
### <a name="example"></a>示例  
  请参阅示例[CDC::CreateCompatibleDC](#createcompatibledc)。  
  
##  <a name="a-namecdca--cdccdc"></a><a name="cdc"></a>CDC::CDC  
 构造 `CDC` 对象。  
  
```  
CDC();
```  
  
##  <a name="a-namechorda--cdcchord"></a><a name="chord"></a>CDC::Chord  
 绘制弦 （受限于一个椭圆和一条线段的交集的闭合图形）。  
  
```  
BOOL Chord(
    int x1,  
    int y1,  
    int x2,  
    int y2,  
    int x3,  
    int y3,  
    int x4,  
    int y4);

 
BOOL Chord(
    LPCRECT lpRect,  
    POINT ptStart,  
    POINT ptEnd);
```  
  
### <a name="parameters"></a>参数  
 `x1`  
 指定的电源线的窗口左上角的 x 坐标的边框 （使用逻辑单位）。  
  
 `y1`  
 指定的电源线的窗口左上角的 y 坐标的边框 （使用逻辑单位）。  
  
 `x2`  
 指定的电源线的右下角的 x 坐标的边框 （使用逻辑单位）。  
  
 `y2`  
 指定的电源线的右下角的 y 坐标的边框 （使用逻辑单位）。  
  
 *x3*  
 指定定义该弦的点的 x 坐标的起始位置 （使用逻辑单位）。  
  
 `y3`  
 指定定义该弦的点的 y 坐标的起始位置 （使用逻辑单位）。  
  
 `x4`  
 指定定义该弦终结点 （使用逻辑单位） 的点的 x 坐标。  
  
 `y4`  
 指定定义该弦终结点 （使用逻辑单位） 的点的 y 坐标。  
  
 `lpRect`  
 指定的边框 （使用逻辑单位）。 您可以传递`LPRECT`或[CRect](../../atl-mfc-shared/reference/crect-class.md)为此参数的对象。  
  
 `ptStart`  
 指定定义该弦点 x 和 y 坐标的起始位置 （使用逻辑单位）。 此时没有要将其完全置于电源线。 您可以传递**点**结构或`CPoint`为此参数的对象。  
  
 `ptEnd`  
 指定定义该弦 （使用逻辑单位） 的结束点的点 x 和 y 坐标。 此时没有要将其完全置于电源线。 您可以传递[点](../../mfc/reference/point-structure1.md)结构或[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)为此参数的对象。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 ( `x1`， `y1`) 和 ( `x2`， `y2`) 参数的左上角和右下角，分别指定边界是电源线的一部分的椭圆的矩形。 ( *X3*， `y3`) 和 ( `x4`， `y4`) 参数指定的椭圆的直线的终结点。 该弦是使用所选的笔绘制，并通过使用所选的画笔填充。  
  
 该图中绘制的`Chord`函数最多扩展，但不包括右边和底边坐标。 这意味着该图的高度是`y2`–`y1`和图形的宽度是`x2`– `x1`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&31;](../../mfc/codesnippet/cpp/cdc-class_3.cpp)]  
  
##  <a name="a-nameclosefigurea--cdcclosefigure"></a><a name="closefigure"></a>CDC::CloseFigure  
 关闭开放的图形路径中。  
  
```  
BOOL CloseFigure();
```  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 函数通过从当前位置到图中的第一个点绘制一条线闭合图形 (通常情况下，到最近的调用由指定的点`MoveTo`成员函数) 并将这些行连接通过使用线段联接样式。 如果通过使用闭合图形时`LineTo`成员函数而不是`CloseFigure`，端帽用于创建而不是一个联接的角。 `CloseFigure`只应调用的设备上下文中是开放路径括号是否。  
  
 图的路径中处于打开状态，除非它显式关闭使用此函数。 （图可以打开即使当前点和该图中的起始点是相同的。）任何直线或曲线添加到路径后`CloseFigure`开始一个新图形。  
  
##  <a name="a-namecreatecompatibledca--cdccreatecompatibledc"></a><a name="createcompatibledc"></a>CDC::CreateCompatibleDC  
 创建与由指定的设备兼容的内存设备上下文`pDC`。  
  
```  
BOOL CreateCompatibleDC(CDC* pDC);
```  
  
### <a name="parameters"></a>参数  
 `pDC`  
 一个指向设备上下文的指针。 如果`pDC`是**NULL**，该函数将创建与系统显示兼容的内存设备上下文。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 内存设备上下文是内存的一个表示显示图面块。 可用来将其复制到兼容的设备的实际设备面之前准备在内存中的图像。  
  
 时都会创建一个内存设备上下文，GDI 将自动为其选择 1-1 的单色股票位图。 输出的 GDI 函数可以用于内存设备上下文，仅当创建位图并将其选入该上下文。  
  
 此函数仅用于创建支持光栅操作的设备兼容的设备上下文。 请参阅[CDC::BitBlt](#bitblt)设备上下文之间的位块传输有关的信息的成员函数。 若要确定设备上下文是否支持光栅操作，请参阅**RC_BITBLT**光栅功能在成员函数中的`CDC::GetDeviceCaps`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&32;](../../mfc/codesnippet/cpp/cdc-class_4.cpp)]  
  
##  <a name="a-namecreatedca--cdccreatedc"></a><a name="createdc"></a>CDC::CreateDC  
 创建指定的设备的设备上下文。  
  
```  
BOOL CreateDC(
    LPCTSTR lpszDriverName,  
    LPCTSTR lpszDeviceName,  
    LPCTSTR lpszOutput,  
    const void* lpInitData);
```  
  
### <a name="parameters"></a>参数  
 `lpszDriverName`  
 指向以 null 结尾的字符串，指定设备驱动程序 (例如，"EPSON") 的文件名 （不带扩展名）。 您还可以传递`CString`为此参数的对象。  
  
 `lpszDeviceName`  
 指向以 null 结尾的字符串，指定的特定设备必须支持 （例如"EPSON FX-80"） 的名称。 `lpszDeviceName`如果模块支持多个设备，则使用参数。 您还可以传递`CString`为此参数的对象。  
  
 `lpszOutput`  
 指向以 null 结尾的字符串，它指定物理输出媒体 （文件或输出端口） 的文件或设备名称。 您还可以传递`CString`为此参数的对象。  
  
 `lpInitData`  
 指向`DEVMODE`包含设备驱动程序的特定于设备的初始化数据结构。 Windows **DocumentProperties**函数可检索针对给定设备中填充此结构。 `lpInitData`参数必须是**NULL**如果设备驱动程序是使用由用户通过控制面板中指定的默认初始化 （如果有）。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 打印。H 标头文件是必需的如果[DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565)使用结构。  
  
 设备名称遵循以下约定︰ 结束冒号 （:） 是推荐，但为可选。 Windows 抽出终止冒号，以便以冒号结尾的设备名称映射到与不带冒号相同的名称相同的端口。 驱动程序和端口名称不能包含前导或尾随空格。 不能与信息的上下文中使用 GDI 输出函数。  
  
##  <a name="a-namecreateica--cdccreateic"></a><a name="createic"></a>CDC::CreateIC  
 创建指定的设备的信息上下文。  
  
```  
BOOL CreateIC(
    LPCTSTR lpszDriverName,  
    LPCTSTR lpszDeviceName,  
    LPCTSTR lpszOutput,  
    const void* lpInitData);
```  
  
### <a name="parameters"></a>参数  
 `lpszDriverName`  
 指向以 null 结尾的字符串，指定设备驱动程序 (例如，"EPSON") 的文件名 （不带扩展名）。 您可以将传递`CString`为此参数的对象。  
  
 `lpszDeviceName`  
 指向以 null 结尾的字符串，指定的特定设备必须支持 （例如"EPSON FX-80"） 的名称。 `lpszDeviceName`如果模块支持多个设备，则使用参数。 您可以将传递`CString`为此参数的对象。  
  
 `lpszOutput`  
 指向以 null 结尾的字符串，它指定物理输出媒体 （文件或端口） 的文件或设备名称。 您可以将传递`CString`为此参数的对象。  
  
 `lpInitData`  
 指向设备驱动程序的特定于设备的初始化数据。 `lpInitData`参数必须是**NULL**如果设备驱动程序是使用由用户通过控制面板中指定的默认初始化 （如果有）。 请参阅`CreateDC`为设备特定的初始化的数据格式。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 信息上下文提供了一种以获取有关设备的信息，而无需创建设备上下文的快速方法。  
  
 设备名称遵循以下约定︰ 结束冒号 （:） 是推荐，但为可选。 Windows 抽出终止冒号，以便以冒号结尾的设备名称映射到与不带冒号相同的名称相同的端口。 驱动程序和端口名称不能包含前导或尾随空格。 不能与信息的上下文中使用 GDI 输出函数。  
  
##  <a name="a-namedeletedca--cdcdeletedc"></a><a name="deletedc"></a>CDC::DeleteDC  
 一般情况下，不调用此函数;析构函数将为您完成它。  
  
```  
BOOL DeleteDC();
```  
  
### <a name="return-value"></a>返回值  
 如果成功，则完成此函数，则为非否则为 0。  
  
### <a name="remarks"></a>备注  
 `DeleteDC`成员函数删除与之关联的 Windows 设备上下文`m_hDC`在当前`CDC`对象。 如果此`CDC`对象是为给定设备的最后一个活动的设备上下文、 通知设备和释放设备所使用的所有存储和系统资源。  
  
 应用程序不应调用`DeleteDC`如果到设备上下文中选择了对象。 被删除之前，首先必须从设备上下文选择对象。  
  
 应用程序不得删除设备上下文的句柄通过调用获得[CWnd::GetDC](../../mfc/reference/cwnd-class.md#getdc)。 相反，它必须调用[CWnd::ReleaseDC](../../mfc/reference/cwnd-class.md#releasedc)以释放设备上下文。 [CClientDC](../../mfc/reference/cclientdc-class.md)和[CWindowDC](../../mfc/reference/cwindowdc-class.md)提供类，以封装此功能。  
  
 `DeleteDC`函数通常用于删除与创建设备上下文[CreateDC](#createdc)， [CreateIC](#createic)，或[CreateCompatibleDC](#createcompatibledc)。  
  
### <a name="example"></a>示例  
  请参阅示例[CPrintDialog::GetPrinterDC](../../mfc/reference/cprintdialog-class.md#getprinterdc)。  
  
##  <a name="a-namedeletetempmapa--cdcdeletetempmap"></a><a name="deletetempmap"></a>CDC::DeleteTempMap  
 自动调用`CWinApp`空闲时间处理程序中，`DeleteTempMap`删除任何临时`CDC`由创建的对象`FromHandle`，但不会销毁设备上下文句柄 ( `hDC`s) 与临时关联`CDC`对象。  
  
```  
static void PASCAL DeleteTempMap();
```  
  
##  <a name="a-namedetacha--cdcdetach"></a><a name="detach"></a>CDC::Detach  
 调用此函数可分离`m_hDC`（输出设备上下文） 从`CDC`对象，并同时设置`m_hDC`和`m_hAttribDC`到**NULL**。  
  
```  
HDC Detach();
```  
  
### <a name="return-value"></a>返回值  
 Windows 设备上下文。  
  
##  <a name="a-namedptohimetrica--cdcdptohimetric"></a><a name="dptohimetric"></a>CDC::DPtoHIMETRIC  
 使用此函数在您向提供**HIMETRIC**给 OLE，将转换为像素大小**HIMETRIC**。  
  
```  
void DPtoHIMETRIC(LPSIZE lpSize) const;  
```  
  
### <a name="parameters"></a>参数  
 `lpSize`  
 指向[大小](http://msdn.microsoft.com/library/windows/desktop/dd145106)结构或[CSize](../../atl-mfc-shared/reference/csize-class.md)对象。  
  
### <a name="remarks"></a>备注  
 设备上下文对象的映射模式是否`MM_LOENGLISH`， `MM_HIENGLISH`， `MM_LOMETRIC`，或`MM_HIMETRIC`，则转换基于中物理英寸的像素数。 如果映射模式是其他非受限模式之一 (例如， `MM_TEXT`)，则转换基于中逻辑英寸的像素数。  
  
##  <a name="a-namedptolpa--cdcdptolp"></a><a name="dptolp"></a>CDC::DPtoLP  
 将设备单位转换为逻辑单元。  
  
```  
void DPtoLP(
    LPPOINT lpPoints,  
    int nCount = 1) const;  
  
void DPtoLP(LPRECT lpRect) const;
void DPtoLP(LPSIZE lpSize) const;  
```  
  
### <a name="parameters"></a>参数  
 `lpPoints`  
 指向数组的[点](../../mfc/reference/point-structure1.md)结构或[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)对象。  
  
 `nCount`  
 数组中的点的数目。  
  
 `lpRect`  
 指向[RECT](../../mfc/reference/rect-structure1.md)结构或[CRect](../../atl-mfc-shared/reference/crect-class.md)对象。 此参数用于将一个矩形从设备点转换为逻辑磅的简单情况。  
  
 `lpSize`  
 指向[大小](http://msdn.microsoft.com/library/windows/desktop/dd145106)结构或[CSize](../../atl-mfc-shared/reference/csize-class.md)对象。  
  
### <a name="remarks"></a>备注  
 该函数将映射每个点的坐标或大小，从设备坐标系统为 GDI 的逻辑坐标系统的维度。 转换取决于当前的映射模式和来源和设备的窗口和视区的范围的设置。  
  
##  <a name="a-namedraw3drecta--cdcdraw3drect"></a><a name="draw3drect"></a>CDC::Draw3dRect  
 调用该成员函数以绘制一个三维的矩形。  
  
```  
void Draw3dRect(
    LPCRECT lpRect,  
    COLORREF clrTopLeft,  
    COLORREF clrBottomRight);

 
void Draw3dRect(
    int x,  
    int y,  
    int cx,  
    int cy,  
    COLORREF clrTopLeft,  
    COLORREF clrBottomRight);
```  
  
### <a name="parameters"></a>参数  
 `lpRect`  
 指定的边框 （使用逻辑单位）。 您可以将传递指向的指针[RECT](../../mfc/reference/rect-structure1.md)结构或[CRect](../../atl-mfc-shared/reference/crect-class.md)为此参数的对象。  
  
 *clrTopLeft*  
 指定三维矩形的顶部和左侧边的颜色。  
  
 `clrBottomRight`  
 指定底部的颜色和三维矩形的右侧。  
  
 *x*  
 指定三维矩形的左上角的逻辑 x 坐标。  
  
 *y*  
 指定三维矩形的左上角的逻辑 y 坐标。  
  
 cx  
 指定三维矩形的宽度。  
  
 cy  
 指定三维矩形的高度。  
  
### <a name="remarks"></a>备注  
 该矩形将绘制带中指定的颜色的顶部和左侧边*clrTopLeft*下和在指定的颜色的左右两侧`clrBottomRight`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView 第&33;](../../mfc/codesnippet/cpp/cdc-class_5.cpp)]  
  
##  <a name="a-namedrawdragrecta--cdcdrawdragrect"></a><a name="drawdragrect"></a>CDC::DrawDragRect  
 调用此成员函数反复进行重绘拖动矩形。  
  
```  
void DrawDragRect(
    LPCRECT lpRect,  
    SIZE size,  
    LPCRECT lpRectLast,  
    SIZE sizeLast,  
    CBrush* pBrush = NULL,  
    CBrush* pBrushLast = NULL);
```  
  
### <a name="parameters"></a>参数  
 `lpRect`  
 指向[RECT](../../mfc/reference/rect-structure1.md)结构或[CRect](../../atl-mfc-shared/reference/crect-class.md)对象，它指定的矩形的逻辑坐标 — 在本例中为要重新绘制的矩形的结束位置。  
  
 `size`  
 指定从左上角外边框的针对换一个矩形的内部边框 （即，边框的粗细） 的左上角。  
  
 `lpRectLast`  
 指向[RECT](../../mfc/reference/rect-structure1.md)结构或[CRect](../../atl-mfc-shared/reference/crect-class.md)对象，它指定的逻辑坐标的矩形的位置 — 在本例中为要重新绘制的矩形的原始位置。  
  
 *sizeLast*  
 指定从左上角外边框的针对换重绘的原始矩形的内部边框 （即，边框的粗细） 的左上角。  
  
 `pBrush`  
 指向 brush 对象的指针。 设置为**NULL**若要使用的默认半色调画笔。  
  
 *pBrushLast*  
 指向使用的最后一个画笔对象的指针。 设置为**NULL**若要使用的默认半色调画笔。  
  
### <a name="remarks"></a>备注  
 若要为提供直观反馈示例鼠标位置，请调用它循环。 当您调用`DrawDragRect`，以前的矩形将被删除，绘制一个新。 例如，作为用户在屏幕上，拖动矩形`DrawDragRect`将清除原始矩形，重绘一个新的新位置。 默认情况下，`DrawDragRect`来消除闪烁以及创建平稳移动矩形的外观使用半色调画笔绘制的矩形。  
  
 首次调用`DrawDragRect`、`lpRectLast`参数应为**NULL**。  
  
##  <a name="a-namedrawedgea--cdcdrawedge"></a><a name="drawedge"></a>CDC::DrawEdge  
 调用该成员函数以绘制指定的类型和样式的矩形的边缘。  
  
```  
BOOL DrawEdge(
    LPRECT lpRect,  
    UINT nEdge,  
    UINT nFlags);
```  
  
### <a name="parameters"></a>参数  
 `lpRect`  
 一个指向**RECT**结构，其中包含逻辑的矩形的坐标。  
  
 *nEdge*  
 指定要绘制的内部和外部边缘的类型。 此参数必须是一个内部边框标志和一个外部边框标志的组合。 请参阅[DrawEdge](http://msdn.microsoft.com/library/windows/desktop/dd162477)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]有关参数的类型的表。  
  
 `nFlags`  
 用于指定要绘制的边框类型的标志。 请参阅`DrawEdge`中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]有关参数的值的表。 有关对角线， **BF_RECT**标志指定向量由矩形参数绑定的终结点。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
##  <a name="a-namedrawescapea--cdcdrawescape"></a><a name="drawescape"></a>CDC::DrawEscape  
 绘制视频显示器直接通过不可用的图形设备接口 (GDI) 的功能的访问。  
  
```  
int DrawEscape(
    int nEscape,  
    int nInputSize,  
    LPCSTR lpszInputData);
```  
  
### <a name="parameters"></a>参数  
 `nEscape`  
 指定要执行的转义函数。  
  
 `nInputSize`  
 指定指向的数据的字节数`lpszInputData`参数。  
  
 `lpszInputData`  
 指向输入结构所需的指定转义符。  
  
### <a name="return-value"></a>返回值  
 指定该函数的结果。 大于零; 如果成功，除**QUERYESCSUPPORT**绘制转义符，用于实现; 或为零的检查未实现转义符; 或小于零，如果错误发生。  
  
### <a name="remarks"></a>备注  
 在应用程序调用`DrawEscape`，数据由标识`nInputSize`和`lpszInputData`直接传递到指定的显示驱动程序。  
  
##  <a name="a-namedrawfocusrecta--cdcdrawfocusrect"></a><a name="drawfocusrect"></a>CDC::DrawFocusRect  
 绘制一个矩形中用来指示该矩形有焦点的样式。  
  
```  
void DrawFocusRect(LPCRECT lpRect);
```  
  
### <a name="parameters"></a>参数  
 `lpRect`  
 指向[RECT](../../mfc/reference/rect-structure1.md)结构或[CRect](../../atl-mfc-shared/reference/crect-class.md)对象，它指定要绘制的矩形的逻辑坐标。  
  
### <a name="remarks"></a>备注  
 由于这是一个布尔 XOR 函数，调用该函数将第二次使用同一矩形从中删除该矩形显示。 不能滚动此函数绘制的矩形。 若要滚动包含此函数绘制的矩形区域，请首先调用`DrawFocusRect`不再显示该矩形，区域中，然后向下滚动，然后调用`DrawFocusRect`再次用于绘制矩形中的新位置。  
  
> [!CAUTION]
> `DrawFocusRect`只适用于`MM_TEXT`模式。 在其他模式下，此函数不绘制聚焦框正确，但它不返回错误值。  
  
##  <a name="a-namedrawframecontrola--cdcdrawframecontrol"></a><a name="drawframecontrol"></a>CDC::DrawFrameControl  
 调用该成员函数以绘制帧控件的指定的类型和样式。  
  
```  
BOOL DrawFrameControl(
    LPRECT lpRect,  
    UINT nType,  
    UINT nState);
```  
  
### <a name="parameters"></a>参数  
 `lpRect`  
 一个指向**RECT**结构，其中包含逻辑的矩形的坐标。  
  
 `nType`  
 指定要绘制的帧控件的类型。 请参阅*uType*中的参数[DrawFrameControl](http://msdn.microsoft.com/library/windows/desktop/dd162480)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]有关此参数的可能值的列表。  
  
 `nState`  
 指定框架控件的初始状态。 可以是一个或多个值所述*uState*中的参数`DrawFrameControl`中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 使用`nState`值**DFCS_ADJUSTRECT**调整要排除的推送按钮周围边缘的边框。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 在某些情况下，`nState`取决于`nType`参数。 以下列表显示了四个之间的关系`nType`值和`nState`:  
  
- **DFC_BUTTON**  
  
    - **DFCS_BUTTON3STATE**三个状态的按钮  
  
    - **DFCS_BUTTONCHECK**复选框  
  
    - **DFCS_BUTTONPUSH**下压按钮  
  
    - **DFCS_BUTTONRADIO**单选按钮  
  
    - **DFCS_BUTTONRADIOIMAGE**单选按钮图像 （非方形需要图像）  
  
    - **DFCS_BUTTONRADIOMASK**单选按钮的掩码 （非方形需要掩码）  
  
- **DFC_CAPTION**  
  
    - **DFCS_CAPTIONCLOSE**关闭按钮  
  
    - **DFCS_CAPTIONHELP**帮助按钮  
  
    - **DFCS_CAPTIONMAX**最大化按钮  
  
    - **DFCS_CAPTIONMIN**最小化按钮  
  
    - **DFCS_CAPTIONRESTORE**还原按钮  
  
- **DFC_MENU**  
  
    - **DFCS_MENUARROW**子菜单箭头  
  
    - **DFCS_MENUBULLET**项目符号  
  
    - **DFCS_MENUCHECK**复选标记  
  
- **DFC_SCROLL**  
  
    - **DFCS_SCROLLCOMBOBOX**组合框中滚动条  
  
    - **DFCS_SCROLLDOWN**向下滚动条箭头  
  
    - **DFCS_SCROLLLEFT**滚动条向左的箭头  
  
    - **DFCS_SCROLLRIGHT**向右滚动条箭头  
  
    - **DFCS_SCROLLSIZEGRIP**窗口的右下角的大小调整手柄  
  
    - **DFCS_SCROLLUP**向上滚动条箭头  
  
### <a name="example"></a>示例  
 此代码在您的窗口的右下角中绘制大小控制手柄。 适用于`OnPaint`的对话框中，具有无样式，但通常不包含可能会为其指定的大小控制手柄的其他控件 （如状态栏） 处理程序。  
  
 [!code-cpp[NVC_MFCDocView #&34;](../../mfc/codesnippet/cpp/cdc-class_6.cpp)]  
  
##  <a name="a-namedrawicona--cdcdrawicon"></a><a name="drawicon"></a>CDC::DrawIcon  
 在当前所表示的设备上绘制一个图标`CDC`对象。  
  
```  
BOOL DrawIcon(
    int x,  
    int y,  
    HICON hIcon);

 
BOOL DrawIcon(
    POINT point,  
    HICON hIcon);
```  
  
### <a name="parameters"></a>参数  
 *x*  
 指定的窗口左上角的图标的逻辑 x 坐标。  
  
 *y*  
 指定的窗口左上角的图标的逻辑 y 坐标。  
  
 `hIcon`  
 标识要绘制的图标的句柄。  
  
 `point`  
 指定逻辑 x 坐标和 y 坐标的左上角的图标。 您可以将传递[点](../../mfc/reference/point-structure1.md)结构或[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)为此参数的对象。  
  
### <a name="return-value"></a>返回值  
 如果成功，则完成此函数，则为非否则为 0。  
  
### <a name="remarks"></a>备注  
 该函数由指定的位置处放置图标的左上角*x*和*y*。 位置是根据设备上下文的当前映射模式。  
  
 图标资源必须先前已加载，使用的功能`CWinApp::LoadIcon`， `CWinApp::LoadStandardIcon`，或`CWinApp::LoadOEMIcon`。 `MM_TEXT`必须使用此函数之前选择的映射模式。  
  
### <a name="example"></a>示例  
  请参阅示例[CWnd::IsIconic](../../mfc/reference/cwnd-class.md#isiconic)。  
  
##  <a name="a-namedrawstatea--cdcdrawstate"></a><a name="drawstate"></a>CDC::DrawState  
 调用此成员函数来显示图像和应用外观效果以指示状态，如已禁用或默认状态。  
  
> [!NOTE]
>  为所有`nFlag`状态除外**DSS_NORMAL**，图像转换为单色之前应用的视觉效果。  
  
```  
BOOL DrawState(
    CPoint pt,  
    CSize size,  
    HBITMAP hBitmap,  
    UINT nFlags,  
    HBRUSH hBrush = NULL);

 
BOOL DrawState(
    CPoint pt,  
    CSize size,  
    CBitmap* pBitmap,  
    UINT nFlags,  
    CBrush* pBrush = NULL);

 
BOOL DrawState(
    CPoint pt,  
    CSize size,  
    HICON hIcon,  
    UINT nFlags,  
    HBRUSH hBrush = NULL);

 
BOOL DrawState(
    CPoint pt,  
    CSize size,  
    HICON hIcon,  
    UINT nFlags,  
    CBrush* pBrush = NULL);

 
BOOL DrawState(
    CPoint pt,  
    CSize size,  
    LPCTSTR lpszText,  
    UINT nFlags,  
    BOOL bPrefixText = TRUE,  
    int nTextLen = 0,  
    HBRUSH hBrush = NULL);

 
BOOL DrawState(
    CPoint pt,  
    CSize size,  
    LPCTSTR lpszText,  
    UINT nFlags,  
    BOOL bPrefixText = TRUE,  
    int nTextLen = 0,  
    CBrush* pBrush = NULL);

 
BOOL DrawState(
    CPoint pt,  
    CSize size,  
    DRAWSTATEPROC lpDrawProc,  
    LPARAM lData,  
    UINT nFlags,  
    HBRUSH hBrush = NULL);

 
BOOL DrawState(
    CPoint pt,  
    CSize size,  
    DRAWSTATEPROC lpDrawProc,  
    LPARAM lData,  
    UINT nFlags,  
    CBrush* pBrush = NULL);
```  
  
### <a name="parameters"></a>参数  
 `pt`  
 指定的映像的位置。  
  
 `size`  
 指定图像的大小。  
  
 `hBitmap`  
 指向位图的句柄。  
  
 `nFlags`  
 指定图像类型和状态的标志。 请参阅[DrawState](http://msdn.microsoft.com/library/windows/desktop/dd162496)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]以尽可能高`nFlags`类型和状态。  
  
 `hBrush`  
 为画笔句柄。  
  
 `pBitmap`  
 指向 CBitmap 对象的指针。  
  
 `pBrush`  
 指向 CBrush 对象的指针。  
  
 `hIcon`  
 指向一个图标的句柄。  
  
 `lpszText`  
 指向文本指针。  
  
 *bPrefixText*  
 可能包含加速器助记键的文本。 `lData`参数指定的字符串的地址和`nTextLen`参数指定的长度。 如果`nTextLen`为 0，则假定以 null 结尾的字符串。  
  
 `nTextLen`  
 指向的文本字符串的长度`lpszText`。 如果`nTextLen`为 0，则假定以 null 结尾的字符串。  
  
 *lpDrawProc*  
 指向用于呈现的图像的回调函数的指针。 此参数是必需的当在中键入图像`nFlags`是**DST_COMPLEX**。 它是可选的可以是**NULL**图像类型是否**DST_TEXT**。 对于所有其他图像类型，则忽略此参数。 回调函数的详细信息，请参阅[DrawStateProc](http://msdn.microsoft.com/library/windows/desktop/dd162497) ，此功能在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `lData`  
 指定映像的信息。 此参数的含义取决于图像类型。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
##  <a name="a-namedrawtexta--cdcdrawtext"></a><a name="drawtext"></a>CDC::DrawText  
 调用此成员函数设置给定的矩形中的文本的格式。 若要指定其他格式选项，请使用[CDC::DrawTextEx](#drawtextex)。  
  
```  
virtual int DrawText(
    LPCTSTR lpszString,  
    int nCount,  
    LPRECT lpRect,  
    UINT nFormat);

 
int DrawText(
    const CString& str,  
    LPRECT lpRect,  
    UINT nFormat);
```  
  
### <a name="parameters"></a>参数  
 `lpszString`  
 指向要绘制的字符串。 如果`nCount`为 –&1;，该字符串必须是以 null 结尾。  
  
 `nCount`  
 在字符串中指定字符的数。 如果`nCount`为 –&1;，则`lpszString`被假定为指向以 null 结尾的字符串的长指针和`DrawText`自动计算的字符数。  
  
 `lpRect`  
 指向[RECT](../../mfc/reference/rect-structure1.md)结构或[CRect](../../atl-mfc-shared/reference/crect-class.md)对象，其中包含在其中的文本是要设置格式的矩形 （以逻辑坐标表示）。  
  
 `str`  
 一个[CString](../../atl-mfc-shared/reference/cstringt-class.md)对象，其中包含要绘制的指定的字符。  
  
 `nFormat`  
 指定的设置文本格式的方法。 它可以是针对所述的值的任意组合`uFormat`中的参数[DrawText](http://msdn.microsoft.com/library/windows/desktop/dd162498)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 （结合使用按位 OR 运算符）︰  
  
> [!NOTE]
>  某些`uFormat`标志组合可能会导致要修改所传递的字符串。 使用**DT_MODIFYSTRING**与**DT_END_ELLIPSIS**或**DT_PATH_ELLIPSIS**可能会导致字符串被修改，导致断言`CString`重写。 值`DT_CALCRECT`， `DT_EXTERNALLEADING`， **DT_INTERNAL**， `DT_NOCLIP`，和`DT_NOPREFIX`不能与使用`DT_TABSTOP`值。  
  
### <a name="return-value"></a>返回值  
 如果函数运行成功的文本的高度。  
  
### <a name="remarks"></a>备注  
 设置文本格式到适当的空格，对齐到左、 右、 文本或给定矩形的中心展开选项卡，然后将文本分成容纳在给定的矩形内的行。 由指定的格式设置类型`nFormat`。  
  
 此成员函数使用的设备上下文的所选的字体、 文本颜色和背景颜色绘制文本。 除非`DT_NOCLIP`使用格式时，`DrawText`剪切文本以便在给定的矩形的外部不显示文字。 所有格式，则假定具有多个行，除非`DT_SINGLELINE`给出格式。  
  
 如果所选的字体来说太大的指定矩形`DrawText`成员函数不会尝试替换为较小的字体。  
  
 如果`DT_CALCRECT`指定标志，指定的矩形`lpRect`将更新以反映的宽度和高度需要用于绘制文本。  
  
 如果**TA_UPDATECP**设置文本对齐标志 (请参阅[CDC::SetTextAlign](#settextalign))，`DrawText`将显示在当前的位置，而不给定的矩形的左侧开始的文本。 `DrawText`不会换行文本时**TA_UPDATECP**设置了标志 (即，`DT_WORDBREAK`标志不会有影响)。  
  
 可以设置文本颜色[CDC::SetTextColor](#settextcolor)。  
  
##  <a name="a-namedrawtextexa--cdcdrawtextex"></a><a name="drawtextex"></a>CDC::DrawTextEx  
 设置给定的矩形中的文本的格式。  
  
```  
virtual int DrawTextEx(
    LPTSTR lpszString,  
    int nCount,  
    LPRECT lpRect,  
    UINT nFormat,
    LPDRAWTEXTPARAMS lpDTParams);

 
int DrawTextEx(
    const CString& str,  
    LPRECT lpRect,  
    UINT nFormat,
    LPDRAWTEXTPARAMS lpDTParams);
```  
  
### <a name="parameters"></a>参数  
 `lpszString`  
 指向要绘制的字符串。 如果`nCount`为 –&1;，该字符串必须是以 null 结尾。  
  
 `nCount`  
 在字符串中指定字符的数。 如果`nCount`为 –&1;，则`lpszString`被假定为指向以 null 结尾的字符串的长指针和`DrawText`自动计算的字符数。  
  
 `lpRect`  
 指向[RECT](../../mfc/reference/rect-structure1.md)结构或[CRect](../../atl-mfc-shared/reference/crect-class.md)对象，其中包含在其中的文本是要设置格式的矩形 （以逻辑坐标表示）。  
  
 `str`  
 一个[CString](../../atl-mfc-shared/reference/cstringt-class.md)对象，其中包含要绘制的指定的字符。  
  
 `nFormat`  
 指定的设置文本格式的方法。 它可以是针对所述的值的任意组合`uFormat`中的参数[DrawText](http://msdn.microsoft.com/library/windows/desktop/dd162498)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 (使用按位组合`OR`运算符):  
  
> [!NOTE]
>  某些`uFormat`标志组合可能会导致要修改所传递的字符串。 使用**DT_MODIFYSTRING**与**DT_END_ELLIPSIS**或**DT_PATH_ELLIPSIS**可能会导致字符串被修改，导致断言`CString`重写。 值`DT_CALCRECT`， `DT_EXTERNALLEADING`， **DT_INTERNAL**， `DT_NOCLIP`，和`DT_NOPREFIX`不能与使用`DT_TABSTOP`值。  
  
 `lpDTParams`  
 指向[DRAWTEXTPARAMS](http://msdn.microsoft.com/library/windows/desktop/dd162500)结构，它指定附加的格式设置选项。 此参数可以为**NULL**。  
  
### <a name="remarks"></a>备注  
 设置文本格式到适当的空格，对齐到左、 右、 文本或给定矩形的中心展开选项卡，然后将文本分成容纳在给定的矩形内的行。 由指定的格式设置类型`nFormat`和`lpDTParams`。 有关详细信息，请参阅[CDC::DrawText](#drawtext)和[DrawTextEx](http://msdn.microsoft.com/library/windows/desktop/dd162499)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 可以设置文本颜色[CDC::SetTextColor](#settextcolor)。  
  
##  <a name="a-nameellipsea--cdcellipse"></a><a name="ellipse"></a>CDC::Ellipse  
 绘制椭圆形。  
  
```  
BOOL Ellipse(
    int x1,  
    int y1,  
    int x2,  
    int y2);  
  
BOOL Ellipse(LPCRECT lpRect);
```  
  
### <a name="parameters"></a>参数  
 `x1`  
 指定的椭圆的边框的左上角的逻辑 x 坐标。  
  
 `y1`  
 指定的椭圆的边框的左上角的逻辑 y 坐标。  
  
 `x2`  
 指定的椭圆的边框的右下角的逻辑 x 坐标。  
  
 `y2`  
 指定的椭圆的边框的右下角的逻辑 y 坐标。  
  
 `lpRect`  
 指定的椭圆的边框。 您还可以传递[CRect](../../atl-mfc-shared/reference/crect-class.md)为此参数的对象。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 椭圆的中心是由指定的绑定矩形的中心`x1`， `y1`， `x2`，和`y2`，或`lpRect`。 使用当前笔绘制椭圆，并用当前画笔填充其内部。  
  
 此函数绘制图最多扩展，但不包括右边和底边坐标。 这意味着该图的高度是`y2`–`y1`和图形的宽度是`x2`– `x1`。  
  
 如果边界的矩形的高度或宽度为 0，将绘制没有椭圆。  
  
##  <a name="a-nameenddoca--cdcenddoc"></a><a name="enddoc"></a>CDC::EndDoc  
 结束调用启动的打印作业[StartDoc](#startdoc)成员函数。  
  
```  
int EndDoc();
```  
  
### <a name="return-value"></a>返回值  
 大于或等于 0，如果函数运行成功，则为负值是否发生了错误。  
  
### <a name="remarks"></a>备注  
 此成员函数将替换**ENDDOC**打印机转义，并应在完成打印作业的顺利完成后立即调用。  
  
 如果应用程序会遭遇打印错误或已取消的打印操作，它不能尝试通过使用终止操作`EndDoc`或[AbortDoc](#abortdoc)。 GDI 自动终止了操作后，再返回的错误值。  
  
 此函数不应在图元文件内使用。  
  
### <a name="example"></a>示例  
  请参阅示例[CDC::StartDoc](#startdoc)。  
  
##  <a name="a-nameendpagea--cdcendpage"></a><a name="endpage"></a>CDC::EndPage  
 通知设备应用程序已完成对页的写。  
  
```  
int EndPage();
```  
  
### <a name="return-value"></a>返回值  
 大于或等于 0，如果函数运行成功，则为负值是否发生了错误。  
  
### <a name="remarks"></a>备注  
 此成员函数通常用于直接在前进到新页的设备驱动程序。  
  
 此成员函数将替换**NEWFRAME**打印机转义。 与不同**NEWFRAME**，始终在打印页面后调用此函数。  
  
### <a name="example"></a>示例  
  请参阅示例[CDC::StartDoc](#startdoc)。  
  
##  <a name="a-nameendpatha--cdcendpath"></a><a name="endpath"></a>CDC::EndPath  
 关闭路径括号，并选择到设备上下文由方括号定义的路径。  
  
```  
BOOL EndPath();
```  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
### <a name="example"></a>示例  
  请参阅示例[cdc:: beginpath](#beginpath)。  
  
##  <a name="a-nameenumobjectsa--cdcenumobjects"></a><a name="enumobjects"></a>Cdc:: enumobjects  
 枚举钢笔和画笔在设备上下文中可用。  
  
```  
int EnumObjects(
    int nObjectType,  
    int (CALLBACK* lpfn)(
    LPVOID,
    LPARAM),  
    LPARAM lpData);
```  
  
### <a name="parameters"></a>参数  
 *nObjectType*  
 指定的对象类型。 它可以具有值**OBJ_BRUSH**或**OBJ_PEN**。  
  
 `lpfn`  
 是由应用程序提供的回调函数的过程实例地址。 请参阅下面的"备注"部分。  
  
 `lpData`  
 指向应用程序提供的数据。 数据传递给回调函数和对象信息。  
  
### <a name="return-value"></a>返回值  
 指定返回的最后一个值[回调函数](../../mfc/reference/callback-function-for-cdc-enumobjects.md)。 其含义是用户定义的。  
  
### <a name="remarks"></a>备注  
 对于给定类型的每个对象，您传递的回调函数称为与该对象的信息。 系统调用的回调函数，直到没有更多的对象或回调函数返回 0。  
  
 请注意，Microsoft Visual c + + 的新增功能让您可以使用普通函数，该函数传递给`EnumObjects`。 地址传递给`EnumObjects`是指向与导出的函数的指针**导出**和调用约定 Pascal。 在保护模式的应用程序，无需使用 Windows MakeProcInstance 函数创建此函数，或与 FreeProcInstance Windows 函数一起使用后释放函数。  
  
 您还不需要导出中的函数名称**导出**应用程序的模块定义文件中的语句。 你可以改用**导出**函数修饰符，如下所示  
  
 **int 回调导出**AFunction **(LPSTR**， **LPSTR);**  
  
 若要使编译器将发出导出的正确导出记录由不带别名名称。 这适用于大多数需求。 对于某些特殊的情况下，例如导出函数的序号比较还是别名导出，仍需要使用**导出**模块定义文件中的语句。  
  
 有关 Microsoft Foundation 编译程序，你通常将使用 /GA 和 /GEs 编译器选项。 /Gw 编译器选项不与 Microsoft 基础类使用。 (如果您确实要使用 Windows 函数**MakeProcInstance**，您将需要显式强制转换返回的函数指针从**FARPROC**此 API 中所需的类型。)回调注册接口现在是类型安全的 （必须传递一个指向正确类型的特定的回调函数的函数指针）。  
  
 另请注意所有的回调函数必须捕获返回到 Windows 帐户，因为不能跨回调边界引发异常之前的 Microsoft 基础异常。 关于异常的详细信息，请参阅文章[异常](../../mfc/exception-handling-in-mfc.md)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&35;](../../mfc/codesnippet/cpp/cdc-class_7.cpp)]  
  
##  <a name="a-nameescapea--cdcescape"></a><a name="escape"></a>CDC::Escape  
 此成员函数是几乎已过时的 Win32 编程。  
  
```  
virtual int Escape(
    int nEscape,  
    int nCount,  
    LPCSTR lpszInData,  
    LPVOID lpOutData);

 
int Escape(
    int nEscape,  
    int nInputSize,  
    LPCSTR lpszInputData,  
    int nOutputSize,  
    LPSTR lpszOutputData);
```  
  
### <a name="parameters"></a>参数  
 `nEscape`  
 指定要执行的转义函数。  
  
 转义函数的完整列表，请参阅[转义](http://msdn.microsoft.com/library/windows/desktop/dd162701)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `nCount`  
 指定指向的数据的字节数`lpszInData`。  
  
 `lpszInData`  
 指向此转义所需的输入的数据结构。  
  
 `lpOutData`  
 指向要从该转义接收输出的结构。 `lpOutData`参数是**NULL**如果未不返回任何数据。  
  
 `nInputSize`  
 指定指向的数据的字节数`lpszInputData`参数。  
  
 `lpszInputData`  
 指向输入结构所需的指定转义符。  
  
 `nOutputSize`  
 指定指向的数据的字节数`lpszOutputData`参数。  
  
 `lpszOutputData`  
 指向以接收来自此转义输出的结构。 此参数应为**NULL**如果未不返回任何数据。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，但返回一个正值**QUERYESCSUPPORT**转义符，仅检查实现。 如果未实现转义符，则返回零。 如果出现错误，则返回值为负。 以下是常见的错误值︰  
  
- **SP_ERROR**时出现常规错误。  
  
- **SP_OUTOFDISK**用于后台打印，目前没有足够的磁盘空间并无更多空间将变为可用。  
  
- **SP_OUTOFMEMORY**没有足够的内存可用于后台打印。  
  
- **SP_USERABORT**用户结束通过打印管理器作业。  
  
### <a name="remarks"></a>备注  
 原始打印机转义，仅**QUERYESCSUPPORT** Win32 应用程序的支持。 所有其他打印机转义已过时，并支持只是为了与 16 位应用程序兼容性。  
  
 对于 Win32 编程，`CDC`现在提供了取代其相应的打印机转义符的六个成员函数︰  
  
- [CDC::AbortDoc](#abortdoc)  
  
- [CDC::EndDoc](#enddoc)  
  
- [CDC::EndPage](#endpage)  
  
- [Cdc:: setabortproc](#setabortproc)  
  
- [CDC::StartDoc](#startdoc)  
  
- [CDC::StartPage](#startpage)  
  
 此外， [CDC::GetDeviceCaps](#getdevicecaps)支持 Win32 索引取代其他打印机转义符的应用程序。 请参阅[GetDeviceCaps](http://msdn.microsoft.com/library/windows/desktop/dd144877)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]有关详细信息。  
  
 此成员函数允许应用程序访问特定设备的直接不可通过 GDI 的功能。  
  
 如果您的应用程序使用预定义的转义值，请使用第一个版本。 如果您的应用程序定义的私有转义值，请使用第二个版本。 请参阅[ExtEscape](http://msdn.microsoft.com/library/windows/desktop/dd162708)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]有关第二个版本的详细信息。  
  
##  <a name="a-nameexcludecliprecta--cdcexcludecliprect"></a><a name="excludecliprect"></a>CDC::ExcludeClipRect  
 创建新的剪辑区域，其中包含减去指定的矩形的现有剪辑区域。  
  
```  
int ExcludeClipRect(
    int x1,  
    int y1,  
    int x2,  
    int y2);  
  
int ExcludeClipRect(LPCRECT lpRect);
```  
  
### <a name="parameters"></a>参数  
 `x1`  
 指定的矩形的左上角的逻辑 x 坐标。  
  
 `y1`  
 指定的矩形的左上角的逻辑 y 坐标。  
  
 `x2`  
 指定矩形右下角的逻辑 x 坐标。  
  
 `y2`  
 指定矩形右下角的逻辑 y 坐标。  
  
 `lpRect`  
 指定的矩形。 也可以是`CRect`对象。  
  
### <a name="return-value"></a>返回值  
 指定新的剪辑区域类型。 它可以是任何以下值︰  
  
- **COMPLEXREGION**区域有重叠的边框。  
  
- **错误**没有地区已创建。  
  
- **NULLREGION**区域为空。  
  
- **SIMPLEREGION**区域具有不重叠的边框。  
  
### <a name="remarks"></a>备注  
 所指定的数值的绝对值的矩形的宽度`x2`– `x1`，不能超过 32767 的单位。 此限制适用于以及矩形的高度。  
  
##  <a name="a-nameexcludeupdatergna--cdcexcludeupdatergn"></a><a name="excludeupdatergn"></a>CDC::ExcludeUpdateRgn  
 防止通过从与关联的剪辑区域排除在窗口中的更新的区域内无效窗口区域中绘图`CDC`对象。  
  
```  
int ExcludeUpdateRgn(CWnd* pWnd);
```  
  
### <a name="parameters"></a>参数  
 `pWnd`  
 指向要更新其窗口的窗口对象。  
  
### <a name="return-value"></a>返回值  
 排除区域的类型。 它可以是下列值之一︰  
  
- **COMPLEXREGION**区域有重叠的边框。  
  
- **错误**没有地区已创建。  
  
- **NULLREGION**区域为空。  
  
- **SIMPLEREGION**区域具有不重叠的边框。  
  
##  <a name="a-nameextfloodfilla--cdcextfloodfill"></a><a name="extfloodfill"></a>CDC::ExtFloodFill  
 用当前画笔填充显示图面的区域。  
  
```  
BOOL ExtFloodFill(
    int x,  
    int y,  
    COLORREF crColor,  
    UINT nFillType);
```  
  
### <a name="parameters"></a>参数  
 *x*  
 指定用于填充的开始位置的点的逻辑 x 坐标。  
  
 *y*  
 指定用于填充的开始位置的点的逻辑 y 坐标。  
  
 `crColor`  
 指定边界的或要填充的区域的颜色。 解释`crColor`的值取决于`nFillType`。  
  
 `nFillType`  
 指定要执行填充的类型。 它必须是下列值之一︰  
  
- **FLOODFILLBORDER**受指定的颜色填充区域`crColor`。 此样式等同于由执行在填充`FloodFill`。  
  
- **FLOODFILLSURFACE**由指定的颜色填充区域定义`crColor`。 填充在继续进行向外所有方向，只要遇到颜色。 此样式可用于使用彩色边界填充区域。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则非零值反之，如果在填充无法完成，如果给定的点的边界将 0 指定颜色`crColor`(如果**FLOODFILLBORDER**请求)，如果给定的点没有指定的颜色`crColor`(如果**FLOODFILLSURFACE**请求)，或如果该点以外的剪辑区域。  
  
### <a name="remarks"></a>备注  
 此成员函数提供了更大的灵活性比`FloodFill`因为您可以指定在填充类型`nFillType`。  
  
 如果`nFillType`设置为**FLOODFILLBORDER**，区域被认为完全受指定的颜色`crColor`。 此函数首先在指定的点*x*和*y*并填充到颜色边界所有方向。  
  
 如果`nFillType`设置为**FLOODFILLSURFACE**，此函数首先在指定的点*x*和*y* ，并在所有方向，填充所有包含指定的颜色的相邻区域继续`crColor`。  
  
 只有内存设备上下文和支持光栅显示技术支持的设备`ExtFloodFill`。 有关详细信息，请参阅[GetDeviceCaps](#getdevicecaps)成员函数。  
  
##  <a name="a-nameexttextouta--cdcexttextout"></a><a name="exttextout"></a>CDC::ExtTextOut  
 调用该成员函数以编写使用当前所选的字体中的矩形区域中的一个字符串。  
  
```  
virtual BOOL ExtTextOut(
    int x,  
    int y,  
    UINT nOptions,  
    LPCRECT lpRect,  
    LPCTSTR lpszString,  
    UINT nCount,  
    LPINT lpDxWidths);

 
BOOL ExtTextOut(
    int x,  
    int y,  
    UINT nOptions,  
    LPCRECT lpRect,  
    const CString& str,  
    LPINT lpDxWidths);
```  
  
### <a name="parameters"></a>参数  
 *x*  
 将指定字符串中指定的第一个字符的字符单元格的逻辑 x 坐标。  
  
 *y*  
 将指定字符串中指定的第一个字符的字符单元格的前逻辑 y 坐标。  
  
 `nOptions`  
 指定的矩形类型。 此参数可以为其中一个，这两种，还是两者皆否以下值︰  
  
- **ETO_CLIPPED**指定文本被截断到该矩形。  
  
- **ETO_OPAQUE**指定当前的背景色填充该矩形。 (您可以设置和查询与当前的背景色[SetBkColor](#setbkcolor)和[GetBkColor](#getbkcolor)成员函数。)  
  
 `lpRect`  
 指向[RECT](../../mfc/reference/rect-structure1.md)结构，它确定矩形的尺寸。 此参数可以为**NULL**。 您还可以传递[CRect](../../atl-mfc-shared/reference/crect-class.md)为此参数的对象。  
  
 `lpszString`  
 指向要绘制的指定的字符字符串。 您还可以传递[CString](../../atl-mfc-shared/reference/cstringt-class.md)为此参数的对象。  
  
 `nCount`  
 指定字符串中的字符数。  
  
 `lpDxWidths`  
 指向数组值，用于指示来源的相邻字符单元格之间的距离。 例如， `lpDxWidths`[*我*] 逻辑单元将分隔字符单元格的来源*我*和字符单元格*我*+ 1。 如果`lpDxWidths`是**NULL**，`ExtTextOut`使用字符之间的默认间距。  
  
 `str`  
 一个`CString`对象，其中包含要绘制的指定的字符。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 矩形区域可以是不透明的 （用当前的背景色填充），并且它可以是剪辑区域。  
  
 如果`nOptions`为 0 和`lpRect`是**NULL**，函数将文本写入到设备上下文，而无需使用一个矩形区域。 默认情况下，函数不使用或更新当前位置。 如果应用程序时需要更新当前位置，它调用`ExtTextOut`，应用程序可以调用`CDC`成员函数[SetTextAlign](#settextalign)与`nFlags`设置为**TA_UPDATECP**。 当设置此标志时，Windows 将忽略*x*和*y*到后续调用`ExtTextOut`并改为使用当前的位置。 当应用程序使用**TA_UPDATECP**更新当前位置，`ExtTextOut`设置当前位置到文本的前一行的结尾或指定指向该数组的最后一个元素的位置`lpDxWidths`，两者中较大。  
  
##  <a name="a-namefillpatha--cdcfillpath"></a><a name="fillpath"></a>CDC::FillPath  
 关闭当前路径中的任何开放图形，并使用当前画笔和多边形填充模式填充的路径的内部。  
  
```  
BOOL FillPath();
```  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 填充其内部后，该路径将从设备上下文被丢弃。  
  
##  <a name="a-namefillrecta--cdcfillrect"></a><a name="fillrect"></a>CDC::FillRect  
 调用该成员函数以填充给定的矩形使用指定的画笔。  
  
```  
void FillRect(
    LPCRECT lpRect,  
    CBrush* pBrush);
```  
  
### <a name="parameters"></a>参数  
 `lpRect`  
 指向[RECT](../../mfc/reference/rect-structure1.md)结构，其中包含要填充的矩形的逻辑坐标。 您还可以传递[CRect](../../atl-mfc-shared/reference/crect-class.md)为此参数的对象。  
  
 `pBrush`  
 标识用于填充矩形的画笔。  
  
### <a name="remarks"></a>备注  
 该函数填充完成矩形，包括 left 和 top 的边框，但不填满的右侧和底部边界。  
  
 画笔需要为创建使用[CBrush](../../mfc/reference/cbrush-class.md)成员函数[CreateHatchBrush](../../mfc/reference/cbrush-class.md#createhatchbrush)， [CreatePatternBrush](../../mfc/reference/cbrush-class.md#createpatternbrush)，和[CreateSolidBrush](../../mfc/reference/cbrush-class.md#createsolidbrush)，或检索到了`GetStockObject`Windows 函数。  
  
 填充指定的矩形时`FillRect`不包括矩形右侧和底部边。 GDI 达，填充矩形，但不包括右侧列和底部行，而不考虑当前的映射模式。 `FillRect`比较的值**顶部**，**底部**，**左**，和**右侧**指定矩形的成员。 如果**底部**是否小于或等于**顶部**，或者如果**右侧**是否小于或等于**左**，不绘制的矩形。  
  
 `FillRect`类似于[CDC::FillSolidRect](#fillsolidrect); 但是，`FillRect`采用画笔，因此可以用于使用纯色、 抖的色、 阴影的画笔或图案填充一个矩形。 `FillSolidRect`使用纯色 (由**COLORREF**参数)。 `FillRect`通常低于`FillSolidRect`。  
  
##  <a name="a-namefillrgna--cdcfillrgn"></a><a name="fillrgn"></a>CDC::FillRgn  
 填充由指定的区域`pRgn`与由指定的画笔`pBrush`。  
  
```  
BOOL FillRgn(
    CRgn* pRgn,  
    CBrush* pBrush);
```  
  
### <a name="parameters"></a>参数  
 `pRgn`  
 指向要填充的区域的指针。 中的逻辑单元指定给定区域的坐标。  
  
 `pBrush`  
 标识要用于填充该区域的画笔。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 也必须使用创建画笔`CBrush`成员函数`CreateHatchBrush`， `CreatePatternBrush`， `CreateSolidBrush`，也可以通过检索**GetStockObject**。  
  
### <a name="example"></a>示例  
  请参阅示例[CRgn::CreateRoundRectRgn](../../mfc/reference/crgn-class.md#createroundrectrgn)。  
  
##  <a name="a-namefillsolidrecta--cdcfillsolidrect"></a><a name="fillsolidrect"></a>CDC::FillSolidRect  
 调用该成员函数以使用指定的纯色填充给定的矩形。  
  
```  
void FillSolidRect(
    LPCRECT lpRect,  
    COLORREF clr);

 
void FillSolidRect(
    int x,  
    int y,  
    int cx,  
    int cy,  
    COLORREF clr);
```  
  
### <a name="parameters"></a>参数  
 `lpRect`  
 指定的边框 （使用逻辑单位）。 您可以将传递指向的指针[RECT](../../mfc/reference/rect-structure1.md)数据结构或`CRect`为此参数的对象。  
  
 `clr`指定要用于填充矩形的颜色。  
  
 *x*  
 指定的矩形的左上角的逻辑 x 坐标。  
  
 *y*  
 指定目标矩形的左上角的逻辑 y 坐标。  
  
 `cx`  
 指定的矩形的宽度。  
  
 `cy`  
 指定的矩形的高度。  
  
### <a name="remarks"></a>备注  
 `FillSolidRect`非常类似于[CDC::FillRect](#fillrect); 但是，`FillSolidRect`使用纯色 (由**COLORREF**参数)，而`FillRect`采用画笔，因此可以用于使用纯色、 抖的色、 阴影的画笔或图案填充一个矩形。 `FillSolidRect`通常的速度快于`FillRect`。  
  
> [!NOTE]
>  当您调用`FillSolidRect`，以前使用设置背景色[SetBkColor](#setbkcolor)，设置为所指示的颜色`clr`。  
  
##  <a name="a-nameflattenpatha--cdcflattenpath"></a><a name="flattenpath"></a>CDC::FlattenPath  
 转换到当前的设备上下文中，选择的路径中的任何曲线，并将每条曲线转换为行的序列。  
  
```  
BOOL FlattenPath();
```  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
##  <a name="a-namefloodfilla--cdcfloodfill"></a><a name="floodfill"></a>CDC::FloodFill  
 用当前画笔填充显示图面的区域。  
  
```  
BOOL FloodFill(
    int x,  
    int y,  
    COLORREF crColor);
```  
  
### <a name="parameters"></a>参数  
 *x*  
 指定用于填充的开始位置的点的逻辑 x 坐标。  
  
 *y*  
 指定用于填充的开始位置的点的逻辑 y 坐标。  
  
 `crColor`  
 指定边界的颜色。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则非零值否则，则返回 0 给定的点在填充无法完成，如果具有指定的边界颜色`crColor`，或者点之外的剪辑区域。  
  
### <a name="remarks"></a>备注  
 要限制为指定的假定区域`crColor`。 `FloodFill`函数从指定的点处开始*x*和*y*和在到颜色边界所有方向上继续。  
  
 只有内存设备上下文和支持光栅显示技术支持的设备`FloodFill`成员函数。 璝惠**RC_BITBLT**功能，请参阅`GetDeviceCaps`成员函数。  
  
 `ExtFloodFill`函数提供了类似的功能，但更大的灵活性。  
  
##  <a name="a-nameframerecta--cdcframerect"></a><a name="framerect"></a>CDC::FrameRect  
 指定的矩形周围绘制边框`lpRect`。  
  
```  
void FrameRect(
    LPCRECT lpRect,  
    CBrush* pBrush);
```  
  
### <a name="parameters"></a>参数  
 `lpRect`  
 指向[RECT](../../mfc/reference/rect-structure1.md)结构或[CRect](../../atl-mfc-shared/reference/crect-class.md)对象，其中包含矩形的左上角和右下角中的逻辑坐标。 您还可以传递`CRect`为此参数的对象。  
  
 `pBrush`  
 标识要用于组帧矩形的画笔。  
  
### <a name="remarks"></a>备注  
 该函数使用给定的画笔来绘制边框。 宽度和边框的高度始终是 1 的逻辑单元。  
  
 如果该矩形的**底部**坐标值是否小于或等于**顶部**，或者，如果**右侧**是否小于或等于**左**，不绘制的矩形。  
  
 通过绘制的边框`FrameRect`处于相同的位置绘制边框**矩形**成员函数使用相同的坐标 (如果**矩形**使用笔宽 1 逻辑单位)。 由未填充的矩形的内部`FrameRect`。  
  
##  <a name="a-nameframergna--cdcframergn"></a><a name="framergn"></a>CDC::FrameRgn  
 指定的区域周围绘制边框`pRgn`使用由指定的画笔`pBrush`。  
  
```  
BOOL FrameRgn(
    CRgn* pRgn,  
    CBrush* pBrush,  
    int nWidth,  
    int nHeight);
```  
  
### <a name="parameters"></a>参数  
 `pRgn`  
 指向`CRgn`对象，用于标识要括在边框中的区域。 中的逻辑单元指定给定区域的坐标。  
  
 `pBrush`  
 指向`CBrush`对象，用于标识要用于绘制边框的画笔。  
  
 `nWidth`  
 以设备为单位的垂直画笔笔划中指定的边框宽度。  
  
 `nHeight`  
 以设备为单位的水平画笔笔划中指定的边框的高度。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
### <a name="example"></a>示例  
  请参阅示例[CRgn::CombineRgn](../../mfc/reference/crgn-class.md#combinergn)。  
  
##  <a name="a-namefromhandlea--cdcfromhandle"></a><a name="fromhandle"></a>CDC::FromHandle  
 返回一个指向`CDC`对象时提供给设备上下文的句柄。  
  
```  
static CDC* PASCAL FromHandle(HDC hDC);
```  
  
### <a name="parameters"></a>参数  
 `hDC`  
 包含 Windows 设备上下文的句柄。  
  
### <a name="return-value"></a>返回值  
 指针可能是暂时的不应超出立即使用存储。  
  
### <a name="remarks"></a>备注  
 如果 `CDC` 对象未附加到该句柄，则会创建并附加一个临时 `CDC` 对象。  
  
### <a name="example"></a>示例  
  请参阅示例[CPrintDialog::GetPrinterDC](../../mfc/reference/cprintdialog-class.md#getprinterdc)。  
  
##  <a name="a-namegetarcdirectiona--cdcgetarcdirection"></a><a name="getarcdirection"></a>CDC::GetArcDirection  
 返回设备上下文的当前弧方向。  
  
```  
int GetArcDirection() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果成功，则指定当前弧方向。 以下是有效的返回值︰  
  
- **AD_COUNTERCLOCKWISE**弧线和按逆时针方向绘制的矩形。  
  
- **AD_CLOCKWISE**弧线和沿顺时针方向绘制的矩形。  
  
 如果发生错误，则返回值为零。  
  
### <a name="remarks"></a>备注  
 弧线和矩形函数使用弧方向。  
  
##  <a name="a-namegetaspectratiofiltera--cdcgetaspectratiofilter"></a><a name="getaspectratiofilter"></a>CDC::GetAspectRatioFilter  
 检索当前的长宽比筛选器的设置。  
  
```  
CSize GetAspectRatioFilter() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个`CSize`对象，表示当前的纵横比为筛选器使用纵横比。  
  
### <a name="remarks"></a>备注  
 纵横比是由设备的像素宽度和高度的比率。 有关设备的纵横比的信息用于创建、 选择和显示的字体。 Windows 提供了特殊筛选器，纵横比筛选器，来选择用于特定的纵横比从所有可用的字体的字体。 筛选器是使用指定的长宽比`SetMapperFlags`成员函数。  
  
##  <a name="a-namegetbkcolora--cdcgetbkcolor"></a><a name="getbkcolor"></a>CDC::GetBkColor  
 返回当前的背景色。  
  
```  
COLORREF GetBkColor() const;  
```  
  
### <a name="return-value"></a>返回值  
 RGB 颜色值。  
  
### <a name="remarks"></a>备注  
 如果后台模式是**不透明**，则系统使用的背景色来填充样式的行中的间隙，阴影的画笔中行和在字符单元格的背景之间的间隙。 将位图颜色和单色设备上下文之间转换时，系统也使用背景色。  
  
##  <a name="a-namegetbkmodea--cdcgetbkmode"></a><a name="getbkmode"></a>CDC::GetBkMode  
 返回背景模式。  
  
```  
int GetBkMode() const;  
```  
  
### <a name="return-value"></a>返回值  
 当前的后台模式下，可以是**不透明**或**透明**。  
  
### <a name="remarks"></a>备注  
 后台模式定义系统是否绘制文本、 阴影的画笔或笔样式，不是一条实线之前删除现有的背景颜色绘图图面上。  
  
##  <a name="a-namegetboundsrecta--cdcgetboundsrect"></a><a name="getboundsrect"></a>CDC::GetBoundsRect  
 返回指定的设备上下文的当前累计边界矩形。  
  
```  
UINT GetBoundsRect(
    LPRECT lpRectBounds,  
    UINT flags);
```  
  
### <a name="parameters"></a>参数  
 `lpRectBounds`  
 指向将接收的当前边框的缓冲区。 在逻辑坐标中返回该矩形。  
  
 `flags`  
 指定是否返回后要清除的边框。 此参数应为零，或者设置为以下值︰  
  
- **DCB_RESET**强制它返回后要清除的边框。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则指定的边框的当前状态。 它可以是以下值的组合︰  
  
- **DCB_ACCUMULATE**边界矩形累积在进行。  
  
- **DCB_RESET**边框为空。  
  
- **DCB_SET**边框不为空。  
  
- **DCB_ENABLE**边界累积亮起。  
  
- **DCB_DISABLE**边界累积处于关闭状态。  
  
##  <a name="a-namegetbrushorga--cdcgetbrushorg"></a><a name="getbrushorg"></a>CDC::GetBrushOrg  
 检索当前选定的设备上下文的画笔的原点 （以设备为单位）。  
  
```  
CPoint GetBrushOrg() const;  
```  
  
### <a name="return-value"></a>返回值  
 为画笔 （以设备为单位） 的当前原点[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)对象。  
  
### <a name="remarks"></a>备注  
 初始画笔原点位于 (0，0) 的工作区。 返回的值相对于在桌面窗口原点设备单位指定此点。  
  
##  <a name="a-namegetcharacterplacementa--cdcgetcharacterplacement"></a><a name="getcharacterplacement"></a>CDC::GetCharacterPlacement  
 检索各种类型的一个字符的字符串的信息。  
  
```  
DWORD GetCharacterPlacement(
    LPCTSTR lpString,  
    int nCount,  
    int nMaxExtent,  
    LPGCP_RESULTS lpResults,  
    DWORD dwFlags) const;  
  
DWORD GetCharacterPlacement(
    CString& str,  
    int nMaxExtent,  
    LPGCP_RESULTS lpResults,  
    DWORD dwFlags) const;  
```  
  
### <a name="parameters"></a>参数  
 `lpString`  
 指向要处理的字符字符串的指针。  
  
 `nCount`  
 指定字符串的长度。 有关的 ANSI 版本，它为字节数，Unicode 函数是单词计数。 有关详细信息，请参阅[GetCharacterPlacement](http://msdn.microsoft.com/library/windows/desktop/dd144860\(v=vs.85\).aspx)。  
  
 `nMaxExtent`  
 处理字符串指定最大程度 （使用逻辑单位）。 注意，如果处理，将超出此范围内的字符将被忽略。 对于任何所需的排序或标志符号数组的计算仅适用于包含的字符。 使用此参数只有在指定 GCP_MAXEXTENT 值`dwFlags`参数。 随着该函数中处理的输入的字符串，每个字符和其范围被添加到输出、 范围内和其他数组仅当总的扩展盘区未超过最大值。 一旦达到该限制，将停止处理。  
  
 lpResults  
 指向[GCP_Results](http://msdn.microsoft.com/library/windows/desktop/dd144842\(v=vs.85\).aspx)结构，它接收函数的结果。  
  
 `dwFlags`  
 指定如何处理到所需的数组的字符串。 此参数可以为一个或多个值中列出`dwFlags`部分[GetCharacterPlacement](http://msdn.microsoft.com/library/windows/desktop/dd144860\(v=vs.85\).aspx)主题。  
  
 `str`  
 一个指向[CString](../../atl-mfc-shared/reference/cstringt-class.md)对象传递给过程。  
  
### <a name="return-value"></a>返回值  
 如果函数成功，返回值将为宽度和高度的逻辑单元中的字符串。  
  
 如果函数失败，则返回值为零。  
  
### <a name="remarks"></a>备注  
 此成员函数模拟函数的功能[GetCharacterPlacement](http://msdn.microsoft.com/library/windows/desktop/dd144860\(v=vs.85\).aspx)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetcharabcwidthsa--cdcgetcharabcwidths"></a><a name="getcharabcwidths"></a>CDC::GetCharABCWidths  
 从当前的 TrueType 字体中检索指定范围中的连续字符的宽度。  
  
```  
BOOL GetCharABCWidths(
    UINT nFirstChar,  
    UINT nLastChar,  
    LPABC lpabc) const;  
  
BOOL GetCharABCWidths(
    UINT nFirstChar,  
    UINT nLastChar,  
    LPABCFLOAT lpABCF) const;  
```  
  
### <a name="parameters"></a>参数  
 `nFirstChar`  
 从为其返回的字符宽度的当前字体的字符范围中指定的第一个字符。  
  
 `nLastChar`  
 指定从为其返回的字符宽度的当前字体的字符范围中的最后一个字符。  
  
 `lpabc`  
 指向数组的[ABC](../../mfc/reference/abc-structure.md)函数返回时收到的字符宽度的结构。 该数组必须包含至少任意多个**ABC**作为指定的范围中有字符结构`nFirstChar`和`nLastChar`参数。  
  
 *lpABCF*  
 指向一个应用程序提供的缓冲区的数组与[ABCFLOAT](../../mfc/reference/abcfloat-structure.md)结构，以在该函数返回时收到的字符宽度。 此函数返回的宽度均 IEEE 浮点格式。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 逻辑单元将返回宽度。 此函数仅使用 TrueType 字体成功。  
  
 在选定的特定点大小后，TrueType 光栅器提供了"ABC"字符间距。 "A"间距是放置标志符号之前添加到当前位置的距离。 "B"间距是黑色部件的标志符号的宽度。 "C"间距被添加到当前位置，以考虑到标志符号的右侧的空白空间。 高级宽度的总给定由 A + B + c。  
  
 当`GetCharABCWidths`成员函数将检索负"A"或"C"宽度为一个字符，该字符包括空白部分或延伸量。  
  
 要转换为字体设计单位 ABC 宽度，应用程序应创建一种字体的高度 (根据中的指定**lfHeight**的成员[LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037)结构) 中存储的值等于**ntmSizeEM**的成员[NEWTEXTMETRIC](http://msdn.microsoft.com/library/windows/desktop/dd162741)结构。 (值**ntmSizeEM**成员可以通过调用来检索[EnumFontFamilies](http://msdn.microsoft.com/library/windows/desktop/dd162619) Windows 函数。)  
  
 默认字符 ABC 宽度用于当前选定字体的范围之外的字符。  
  
 若要检索的非 TrueType 字体中的字符宽度，应用程序应使用[GetCharWidth](http://msdn.microsoft.com/library/windows/desktop/dd144861) Windows 函数。  
  
##  <a name="a-namegetcharabcwidthsia--cdcgetcharabcwidthsi"></a><a name="getcharabcwidthsi"></a>CDC::GetCharABCWidthsI  
 检索的宽度，以从当前的 TrueType 字体在指定范围中的连续标志符号索引的逻辑单元。  
  
```  
BOOL GetCharABCWidthsI(
    UINT giFirst,  
    UINT cgi,  
    LPWORD pgi,  
    LPABC lpabc) const;  
```  
  
### <a name="parameters"></a>参数  
 `giFirst`  
 从当前字体的连续标志符号索引组中指定的第一个标志符号索引。 此参数才会使用`pgi`参数是**NULL**。  
  
 `cgi`  
 指定标志符号索引的数目。  
  
 `pgi`  
 指向包含标志符号索引数组的指针。 如果值为**NULL**、`giFirst`改为使用参数。 `cgi`参数在此数组中指定的标志符号索引数目。  
  
 `lpabc`  
 指向数组的指针[ABC](http://msdn.microsoft.com/library/windows/desktop/dd162454)接收的字符宽度的结构。 该数组必须包含至少任意多个**ABC**作为有指定的标志符号索引结构`cgi`参数。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 此成员函数模拟函数的功能[GetCharABCWidthsI](http://msdn.microsoft.com/library/windows/desktop/dd144859)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetcharwidtha--cdcgetcharwidth"></a><a name="getcharwidth"></a>CDC::GetCharWidth  
 从当前的字体，检索一组连续的字符中的单个字符的宽度使用`m_hAttribDC`，输入的设备上下文。  
  
```  
BOOL GetCharWidth(
    UINT nFirstChar,  
    UINT nLastChar,  
    LPINT lpBuffer) const;  
  
BOOL GetCharWidth(
    UINT nFirstChar,  
    UINT nLastChar,  
    float* lpFloatBuffer) const;  
```  
  
### <a name="parameters"></a>参数  
 `nFirstChar`  
 指定在一组连续的当前字体中字符的第一个字符。  
  
 `nLastChar`  
 指定一组连续的当前字体中字符的最后一个字符。  
  
 `lpBuffer`  
 指向一个缓冲区，将在当前的字体中收到一组连续的字符的宽度值。  
  
 *lpFloatBuffer*  
 指向用于接收的字符宽度的缓冲区。 返回的宽度是 32 位 IEEE 浮点格式。 （宽度是沿测量基准线的字符。）  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 例如，如果`nFirstChar`标识字母 a 和`nLastChar`标识字母 z 以及函数检索所有小写字符的宽度。  
  
 该函数所指向的缓冲区中存储的值`lpBuffer`。 此缓冲区必须足够大以容纳所有的宽度。 也就是说，必须有至少 26 条目中给出的示例。  
  
 如果特定字体中不存在连续的字符组中的字符，它将分配的默认字符的宽度值。  
  
##  <a name="a-namegetcharwidthia--cdcgetcharwidthi"></a><a name="getcharwidthi"></a>CDC::GetCharWidthI  
 检索的宽度，以逻辑坐标中，从当前的字体在指定范围中的连续标志符号索引。  
  
```  
BOOL GetCharWidthI(
    UINT giFirst,  
    UINT cgi,  
    LPWORD pgi,  
    LPINT lpBuffer) const;  
```  
  
### <a name="parameters"></a>参数  
 `giFirst`  
 从当前字体的连续标志符号索引组中指定的第一个标志符号索引。 此参数才会使用`pgi`参数是**NULL**。  
  
 `cgi`  
 指定标志符号索引的数目。  
  
 `pgi`  
 指向包含标志符号索引数组的指针。 如果值为**NULL**、`giFirst`改为使用参数。 `cgi`参数在此数组中指定的标志符号索引数目。  
  
 `lpBuffer`  
 一个指向用于接收缓冲区的宽度。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 此成员函数模拟函数的功能[GetCharWidthI](http://msdn.microsoft.com/library/windows/desktop/dd144864)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetclipboxa--cdcgetclipbox"></a><a name="getclipbox"></a>CDC::GetClipBox  
 检索当前的剪辑边界周围 tightest 边界的矩形的尺寸。  
  
```  
virtual int GetClipBox(LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>参数  
 `lpRect`  
 指向[RECT](../../mfc/reference/rect-structure1.md)结构或[CRect](../../atl-mfc-shared/reference/crect-class.md)是否要接收的矩形尺寸的对象。  
  
### <a name="return-value"></a>返回值  
 剪辑区域的类型。 它可以是任何以下值︰  
  
- **COMPLEXREGION**剪辑区域有重叠的边框。  
  
- **错误**设备上下文是无效的。  
  
- **NULLREGION**剪辑区域为空。  
  
- **SIMPLEREGION**剪辑区域具有不重叠的边框。  
  
### <a name="remarks"></a>备注  
 复制到缓冲区所指向的维度`lpRect`。  
  
##  <a name="a-namegetcoloradjustmenta--cdcgetcoloradjustment"></a><a name="getcoloradjustment"></a>CDC::GetColorAdjustment  
 检索设备上下文的颜色调整值。  
  
```  
BOOL GetColorAdjustment(LPCOLORADJUSTMENT lpColorAdjust) const;  
```  
  
### <a name="parameters"></a>参数  
 `lpColorAdjust`  
 指向[COLORADJUSTMENT](../../mfc/reference/coloradjustment-structure.md)数据结构，用于接收颜色调整值。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
##  <a name="a-namegetcurrentbitmapa--cdcgetcurrentbitmap"></a><a name="getcurrentbitmap"></a>CDC::GetCurrentBitmap  
 将指针返回到当前所选`CBitmap`对象。  
  
```  
CBitmap* GetCurrentBitmap() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向`CBitmap`对象，如果成功，否则为**NULL**。  
  
### <a name="remarks"></a>备注  
 此成员函数可返回临时对象。  
  
##  <a name="a-namegetcurrentbrusha--cdcgetcurrentbrush"></a><a name="getcurrentbrush"></a>CDC::GetCurrentBrush  
 将指针返回到当前所选`CBrush`对象。  
  
```  
CBrush* GetCurrentBrush() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向`CBrush`对象，如果成功，否则为**NULL**。  
  
### <a name="remarks"></a>备注  
 此成员函数可返回临时对象。  
  
##  <a name="a-namegetcurrentfonta--cdcgetcurrentfont"></a><a name="getcurrentfont"></a>CDC::GetCurrentFont  
 将指针返回到当前所选`CFont`对象。  
  
```  
CFont* GetCurrentFont() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向`CFont`对象，如果成功，否则为**NULL**。  
  
### <a name="remarks"></a>备注  
 此成员函数可返回临时对象。  
  
##  <a name="a-namegetcurrentpalettea--cdcgetcurrentpalette"></a><a name="getcurrentpalette"></a>CDC::GetCurrentPalette  
 将指针返回到当前所选`CPalette`对象。  
  
```  
CPalette* GetCurrentPalette() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向`CPalette`对象，如果成功，否则为**NULL**。  
  
### <a name="remarks"></a>备注  
 此成员函数可返回临时对象。  
  
##  <a name="a-namegetcurrentpena--cdcgetcurrentpen"></a><a name="getcurrentpen"></a>CDC::GetCurrentPen  
 将指针返回到当前所选`CPen`对象。  
  
```  
CPen* GetCurrentPen() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向`CPen`对象，如果成功，否则为**NULL**。  
  
### <a name="remarks"></a>备注  
 此成员函数可返回临时对象。  
  
##  <a name="a-namegetcurrentpositiona--cdcgetcurrentposition"></a><a name="getcurrentposition"></a>CDC::GetCurrentPosition  
 检索当前的位置 （以逻辑坐标表示）。  
  
```  
CPoint GetCurrentPosition() const;  
```  
  
### <a name="return-value"></a>返回值  
 作为当前位置`CPoint`对象。  
  
### <a name="remarks"></a>备注  
 可以用来设置当前位置`MoveTo`成员函数。  
  
##  <a name="a-namegetdcbrushcolora--cdcgetdcbrushcolor"></a><a name="getdcbrushcolor"></a>CDC::GetDCBrushColor  
 检索当前画笔的颜色。  
  
```  
COLORREF GetDCBrushColor() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果函数成功，返回值是[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)当前画笔的颜色值。  
  
 如果函数失败，返回值是**CLR_INVALID**。  
  
### <a name="remarks"></a>备注  
 此成员函数模拟函数的功能[GetDCBrushColor](http://msdn.microsoft.com/library/windows/desktop/dd144872)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetdcpencolora--cdcgetdcpencolor"></a><a name="getdcpencolor"></a>CDC::GetDCPenColor  
 检索当前的钢笔颜色。  
  
```  
COLORREF GetDCPenColor() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果函数成功，返回值是[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)当前的钢笔颜色的值。  
  
 如果函数失败，返回值是**CLR_INVALID**。  
  
### <a name="remarks"></a>备注  
 此成员函数使用 Win32 函数[GetDCPenColor](http://msdn.microsoft.com/library/windows/desktop/dd144875)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetdevicecapsa--cdcgetdevicecaps"></a><a name="getdevicecaps"></a>CDC::GetDeviceCaps  
 检索各种特定于设备的显示设备的信息。  
  
```  
int GetDeviceCaps(int nIndex) const;  
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 指定要返回的信息的类型。 请参阅[GetDeviceCaps](http://msdn.microsoft.com/library/windows/desktop/dd144877)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]有关值的列表。  
  
### <a name="return-value"></a>返回值  
 如果函数运行成功请求的功能的值。  
  
### <a name="example"></a>示例  
  请参阅示例[CPrintDialog::GetDefaults](../../mfc/reference/cprintdialog-class.md#getdefaults)。  
  
##  <a name="a-namegetfontdataa--cdcgetfontdata"></a><a name="getfontdata"></a>CDC::GetFontData  
 从可缩放字体文件检索字体规格信息。  
  
```  
DWORD GetFontData(
    DWORD dwTable,  
    DWORD dwOffset,  
    LPVOID lpData,  
    DWORD cbData) const;  
```  
  
### <a name="parameters"></a>参数  
 `dwTable`  
 指定要返回的度量值表的名称。 此参数可以为其中一个度量值表中发布的 Microsoft Corporation 的 TrueType 字体文件规范所述。 如果此参数为 0，字体文件开头检索的信息。  
  
 `dwOffset`  
 指定从该处开始检索信息的表的开头的偏移量。 如果此参数为 0，将检索的信息从指定的表开头`dwTable`参数。 如果此值为大于或等于的表的大小`GetFontData`，则返回 0。  
  
 `lpData`  
 指向将接收的字体信息的缓冲区。 如果此值为**NULL**，该函数将返回中指定的字体数据所需的缓冲区的大小`dwTable`参数。  
  
 `cbData`  
 指定长度，以字节为单位，要检索的信息。 如果此参数为 0，`GetFontData`返回中指定的数据的大小`dwTable`参数。  
  
### <a name="return-value"></a>返回值  
 指定在所指向的缓冲区中返回的字节数`lpData`如果函数运行成功; 否则为-1。  
  
### <a name="remarks"></a>备注  
 指定的偏移量到字体文件和要返回的信息的长度以标识要检索的信息。  
  
 有时，应用程序可以使用`GetFontData`成员函数以将 TrueType 字体保存的文档。 若要执行此操作，该应用程序确定是否字体可嵌入，，然后检索整个字体文件中，指定 0 表示`dwTable`， `dwOffset`，和`cbData`参数。  
  
 应用程序可以确定是否可以通过检查嵌入字体**otmfsType**的成员[OUTLINETEXTMETRIC](http://msdn.microsoft.com/library/windows/desktop/dd162755)结构。 如果位 1 **otmfsType**设置，嵌入的字体不允许。 如果清除位 1，则可以嵌入字体。 如果设置位 2，将嵌入为只读。  
  
 如果应用程序尝试使用此函数来检索的非 TrueType 字体，信息`GetFontData`成员函数将返回 –&1;。  
  
##  <a name="a-namegetfontlanguageinfoa--cdcgetfontlanguageinfo"></a><a name="getfontlanguageinfo"></a>CDC::GetFontLanguageInfo  
 返回有关指定的显示上下文的当前选定字体的信息。  
  
```  
DWORD GetFontLanguageInfo() const;  
```  
  
### <a name="return-value"></a>返回值  
 返回值确定当前所选的字体特征。 有关可能的值的完整列表，请参阅[GetFontLanguageInfo](http://msdn.microsoft.com/library/windows/desktop/dd144886)。  
  
### <a name="remarks"></a>备注  
 此成员函数模拟函数的功能[GetFontLanguageInfo](http://msdn.microsoft.com/library/windows/desktop/dd144886)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetglyphoutlinea--cdcgetglyphoutline"></a><a name="getglyphoutline"></a>CDC::GetGlyphOutline  
 检索大纲曲线或大纲中的字符的当前字体的位图。  
  
```  
DWORD GetGlyphOutline(
    UINT nChar,  
    UINT nFormat,  
    LPGLYPHMETRICS lpgm,  
    DWORD cbBuffer,  
    LPVOID lpBuffer,  
    const MAT2* lpmat2) const;  
```  
  
### <a name="parameters"></a>参数  
 `nChar`  
 指定将返回信息的字符。  
  
 `nFormat`  
 指定了函数将要返回的信息的格式。 它可以是下列值之一或 0:  
  
|值|含义|  
|-----------|-------------|  
|**GGO_BITMAP**|返回字形位图。 当函数返回时，所指向的缓冲区`lpBuffer`包含其中的行在字边界启动一个 1 位每像素的位图。|  
|**GGO_NATIVE**|返回在光栅化程序的本机格式中使用设备单位数据点的曲线。 在中时指定此值，指定的任何转换`lpmat2`将被忽略。|  
  
 时的值`nFormat`为 0，则该函数将填充[GLYPHMETRICS](http://msdn.microsoft.com/library/windows/desktop/dd144955)结构，但不返回字形轮廓数据。  
  
 *lpgm*  
 指向**GLYPHMETRICS**结构描述中的字符单元格的标志符号的位置。  
  
 `cbBuffer`  
 指定该函数将大纲字符的信息复制到其中的缓冲区的大小。 如果此值为 0 和`nFormat`参数为**GGO_BITMAP**或**GGO_NATIVE**值，该函数将返回所需的缓冲区大小。  
  
 `lpBuffer`  
 指向函数将大纲字符的信息复制到其中的缓冲区。 如果`nFormat`指定**GGO_NATIVE**的窗体中复制值，信息**TTPOLYGONHEADER**和**TTPOLYCURVE**结构。 如果此值为**NULL**和`nFormat`是**GGO_BITMAP**或**GGO_NATIVE**值，该函数将返回所需的缓冲区大小。  
  
 `lpmat2`  
 指向[MAT2](http://msdn.microsoft.com/library/windows/desktop/dd145048)结构，其中包含的字符的转换矩阵。 此参数不能为**NULL**，即使当**GGO_NATIVE**为指定值`nFormat`。  
  
### <a name="return-value"></a>返回值  
 大小 （字节），如果检索到的信息所需的缓冲区`cbBuffer`为 0 或`lpBuffer`是**NULL**。 否则，为正值，如果该函数成功，则返回 –&1; 是否存在错误。  
  
### <a name="remarks"></a>备注  
 应用程序可以旋转以位图格式检索通过指定指向的结构中的 2-2 变换矩阵的字符数`lpmat2`。  
  
 作为一系列的轮廓以降低返回字形轮廓。 通过定义每个轮廓[TTPOLYGONHEADER](http://msdn.microsoft.com/library/windows/desktop/dd145158)结构后跟任意多个**TTPOLYCURVE**结构需要对其进行描述。 作为返回的所有点[POINTFX](http://msdn.microsoft.com/library/windows/desktop/dd162806)结构，表示绝对位置，而不是相对移动。 起始点所提供的**pfxStart**的成员[TTPOLYGONHEADER](http://msdn.microsoft.com/library/windows/desktop/dd145158)结构是轮廓线的轮廓开始处的点。 [TTPOLYCURVE](http://msdn.microsoft.com/library/windows/desktop/dd145157)遵循的结构很折线记录或样条记录。 折线记录是一系列点;在点之间绘制的直线描述的字符的轮廓。 样条记录表示二次曲线使用 TrueType （即，二次 b 样条）。  
  
##  <a name="a-namegetgraphicsmodea--cdcgetgraphicsmode"></a><a name="getgraphicsmode"></a>CDC::GetGraphicsMode  
 检索指定的设备上下文的当前图形模式。  
  
```  
int GetGraphicsMode() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果成功返回当前图形模式。 此方法可以返回的值的列表，请参阅[GetGraphicsMode](http://msdn.microsoft.com/library/windows/desktop/dd144892)。  
  
 失败时返回 0。  
  
 若要获得扩展错误信息，请调用[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)。  
  
### <a name="remarks"></a>备注  
 此方法将包装 Windows GDI 函数[GetGraphicsMode](http://msdn.microsoft.com/library/windows/desktop/dd144892)。  
  
##  <a name="a-namegethalftonebrusha--cdcgethalftonebrush"></a><a name="gethalftonebrush"></a>CDC::GetHalftoneBrush  
 调用此成员函数以检索半色调画笔。  
  
```  
static CBrush* PASCAL GetHalftoneBrush();
```  
  
### <a name="return-value"></a>返回值  
 一个指向`CBrush`对象成功，否则为如果**NULL**。  
  
### <a name="remarks"></a>备注  
 半色调画笔显示或者若要创建的抖动的模式的前景色和背景颜色的像素。 下面是举例说明如何创建通过半色调画笔的抖动模式。  
  
 ![抖动的钢笔笔画详细信息](../../mfc/reference/media/vc318s1.gif "vc318s1")  
  
##  <a name="a-namegetkerningpairsa--cdcgetkerningpairs"></a><a name="getkerningpairs"></a>CDC::GetKerningPairs  
 检索字距调整对指定的设备上下文中当前选定的字体的字符。  
  
```  
int GetKerningPairs(
    int nPairs,  
    LPKERNINGPAIR lpkrnpair) const;  
```  
  
### <a name="parameters"></a>参数  
 `nPairs`  
 指定的数[KERNINGPAIR](http://msdn.microsoft.com/library/windows/desktop/dd145024)指向结构`lpkrnpair`。 该函数将不会复制与所指定的更多的字距调整对`nPairs`。  
  
 `lpkrnpair`  
 指向数组的**KERNINGPAIR**接收字距调整的结构对函数返回时。 该数组必须包含由指定的数至少与结构`nPairs`。 如果此参数为**NULL**，该函数返回的字距调整对字体的总数。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，请指定字距调整对检索的数目或字距调整在字体对的总次数。 如果函数失败或没有字距调整对字体，则返回零。  
  
##  <a name="a-namegetlayouta--cdcgetlayout"></a><a name="getlayout"></a>CDC::GetLayout  
 调用此成员函数可确定文本和图形设备上下文，如打印机或图元文件的布局。  
  
```  
DWORD GetLayout() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果成功，布局会标记为当前的设备上下文。 否则为**GDI_ERROR**。 对于扩展的错误的信息，请调用[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)。 布局标志的列表，请参阅[CDC::SetLayout](#setlayout)。  
  
### <a name="remarks"></a>备注  
 默认的布局是从左到右。  
  
##  <a name="a-namegetmapmodea--cdcgetmapmode"></a><a name="getmapmode"></a>CDC::GetMapMode  
 检索当前的映射模式。  
  
```  
int GetMapMode() const;  
```  
  
### <a name="return-value"></a>返回值  
 映射模式中。  
  
### <a name="remarks"></a>备注  
 有关映射模式的说明，请参阅`SetMapMode`成员函数。  
  
> [!NOTE]
>  如果调用[SetLayout](#setlayout)若要为从右到左布局，更改 DC **SetLayout**会自动更改到的映射模式`MM_ISOTROPIC`。 因此，对任何后续调用`GetMapMode`将返回`MM_ISOTROPIC`。  
  
##  <a name="a-namegetmiterlimita--cdcgetmiterlimit"></a><a name="getmiterlimit"></a>CDC::GetMiterLimit  
 返回设备上下文的斜角限制。  
  
```  
float GetMiterLimit() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 在绘制的几何线条具有斜接联接时，则使用斜角限制。  
  
##  <a name="a-namegetnearestcolora--cdcgetnearestcolor"></a><a name="getnearestcolor"></a>CDC::GetNearestColor  
 返回与指定的逻辑颜色最匹配的纯色。  
  
```  
COLORREF GetNearestColor(COLORREF crColor) const;  
```  
  
### <a name="parameters"></a>参数  
 `crColor`  
 指定要匹配的颜色。  
  
### <a name="return-value"></a>返回值  
 定义实体的 RGB （红、 绿、 蓝色） 颜色值的颜色最接近`crColor`设备可以表示的值。  
  
### <a name="remarks"></a>备注  
 给定的设备必须能够以表示此颜色。  
  
##  <a name="a-namegetoutlinetextmetricsa--cdcgetoutlinetextmetrics"></a><a name="getoutlinetextmetrics"></a>CDC::GetOutlineTextMetrics  
 检索指标信息的 TrueType 字体。  
  
```  
UINT GetOutlineTextMetrics(
    UINT cbData,  
    LPOUTLINETEXTMETRIC lpotm) const;  
```  
  
### <a name="parameters"></a>参数  
 `lpotm`  
 指向数组的[OUTLINETEXTMETRIC](http://msdn.microsoft.com/library/windows/desktop/dd162755)结构。 如果此参数为**NULL**，该函数将返回检索到的指标数据所需的缓冲区的大小。  
  
 `cbData`  
 指定大小，以字节为单位，向其返回信息的缓冲区。  
  
 `lpotm`  
 指向**OUTLINETEXTMETRIC**结构。 如果此参数为**NULL**，该函数将返回检索到的度量值信息所需的缓冲区的大小。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 [OUTLINETEXTMETRIC](http://msdn.microsoft.com/library/windows/desktop/dd162755)结构包含了大部分的字体度量值提供的信息用于 TrueType 格式，包括[TEXTMETRIC](http://msdn.microsoft.com/library/windows/desktop/dd145132)结构。 最后四个成员**OUTLINETEXTMETRIC**结构不是指向字符串的指针。 应用程序应为这些字符串，除了其他成员所需的空间分配空间。 由于没有的字符串的大小没有系统施加限制，因此分配内存的最简单方法是通过指定检索所需的大小**NULL**为`lpotm`中首次调用`GetOutlineTextMetrics`函数。  
  
##  <a name="a-namegetoutputcharwidtha--cdcgetoutputcharwidth"></a><a name="getoutputcharwidth"></a>CDC::GetOutputCharWidth  
 使用输出设备上下文中， `m_hDC`，并从当前字体检索一组连续的字符中的单个字符的宽度。  
  
```  
BOOL GetOutputCharWidth(
    UINT nFirstChar,  
    UINT nLastChar,  
    LPINT lpBuffer) const;  
```  
  
### <a name="parameters"></a>参数  
 `nFirstChar`  
 指定在一组连续的当前字体中字符的第一个字符。  
  
 `nLastChar`  
 指定一组连续的当前字体中字符的最后一个字符。  
  
 `lpBuffer`  
 指向一个缓冲区，将在当前的字体中收到一组连续的字符的宽度值。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 例如，如果`nFirstChar`标识字母 a 和`nLastChar`标识字母 z 以及函数检索所有小写字符的宽度。  
  
 该函数所指向的缓冲区中存储的值`lpBuffer`。 此缓冲区必须大到足以容纳所有的宽度。也就是说，必须有至少 26 条目中给出的示例。  
  
 如果特定字体中不存在连续的字符组中的字符，它将分配的默认字符的宽度值。  
  
##  <a name="a-namegetoutputtabbedtextextenta--cdcgetoutputtabbedtextextent"></a><a name="getoutputtabbedtextextent"></a>CDC::GetOutputTabbedTextExtent  
 调用此成员函数来计算的宽度和高度的字符的字符串使用[m_hDC](#m_hdc)，输出设备上下文。  
  
```  
CSize GetOutputTabbedTextExtent(
    LPCTSTR lpszString,  
    int nCount,  
    int nTabPositions,  
    LPINT lpnTabStopPositions) const;  
  
CSize GetOutputTabbedTextExtent(
    const CString& str,  
    int nTabPositions,  
    LPINT lpnTabStopPositions) const;  
```  
  
### <a name="parameters"></a>参数  
 `lpszString`  
 指向要测量的字符串。 您还可以传递[CString](../../atl-mfc-shared/reference/cstringt-class.md)为此参数的对象。  
  
 `nCount`  
 指定字符串中的字符数。 如果`nCount`为 –&1;，长度进行计算。  
  
 `nTabPositions`  
 指定指向数组中的制表位位置数`lpnTabStopPositions`。  
  
 `lpnTabStopPositions`  
 指向包含的逻辑单元中的制表位位置的整数的数组。 必须按递增顺序; 排序的制表位最小的 x 值应为数组中的第一项。 不允许向后制表位。  
  
 `str`  
 一个`CString`对象，其中包含要测量的指定的字符。  
  
### <a name="return-value"></a>返回值  
 中的字符串 （使用逻辑单位） 的维度[CSize](../../atl-mfc-shared/reference/csize-class.md)对象。  
  
### <a name="remarks"></a>备注  
 如果该字符串包含一个或多个选项卡上的字符，将字符串的宽度取决于所指定的制表位`lpnTabStopPositions`。 该函数使用当前所选的字体来计算字符串的尺寸。  
  
 为当前剪辑区域的宽度和高度返回不偏移量`GetOutputTabbedTextExtent`函数。  
  
 由于某些设备不要将字符放在常规单元格数组中 （也就是说，它们对大于字距调整字符），字符串中字符的扩展盘区的总和可能不等于字符串的扩展盘区。  
  
 如果`nTabPositions`为 0 和`lpnTabStopPositions`是**NULL**，选项卡扩展到八个的平均字符宽度。 如果`nTabPositions`为 1，将用到的数组中的第一个值所指定的距离分隔的制表位`lpnTabStopPositions`磅为单位。 如果`lpnTabStopPositions`到多个单个值的点，制表位设置为每个值在数组中，最多指定的数量`nTabPositions`。  
  
##  <a name="a-namegetoutputtextextenta--cdcgetoutputtextextent"></a><a name="getoutputtextextent"></a>CDC::GetOutputTextExtent  
 调用此成员函数以使用输出设备上下文中， [m_hDC](#m_hdc)，计算使用当前字体的文本行的高度和宽度。  
  
```  
CSize GetOutputTextExtent(
    LPCTSTR lpszString,  
    int nCount) const;  
  
CSize GetOutputTextExtent(const CString& str) const;  
```  
  
### <a name="parameters"></a>参数  
 `lpszString`  
 指向字符的字符串。 您还可以传递[CString](../../atl-mfc-shared/reference/cstringt-class.md)为此参数的对象。  
  
 `nCount`  
 指定字符串中的字符数。 如果`nCount`为 –&1;，长度进行计算。  
  
 `str`  
 一个`CString`对象，其中包含要测量的指定的字符。  
  
### <a name="return-value"></a>返回值  
 （使用逻辑单位） 的字符串中返回的尺寸[CSize](../../atl-mfc-shared/reference/csize-class.md)对象。  
  
### <a name="remarks"></a>备注  
 宽度和高度返回为当前剪辑区域不会影响`GetOutputTextExtent`。  
  
 由于某些设备不要将字符放在常规单元格数组中 （也就是说，它们执行字距调整），请在字符串中字符的扩展盘区的总和可能不等于字符串的扩展盘区。  
  
##  <a name="a-namegetoutputtextmetricsa--cdcgetoutputtextmetrics"></a><a name="getoutputtextmetrics"></a>CDC::GetOutputTextMetrics  
 检索当前的字体使用的度量值`m_hDC`，输出设备上下文。  
  
```  
BOOL GetOutputTextMetrics(LPTEXTMETRIC lpMetrics) const;  
```  
  
### <a name="parameters"></a>参数  
 `lpMetrics`  
 指向[TEXTMETRIC](http://msdn.microsoft.com/library/windows/desktop/dd145132)接收度量值的结构。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
##  <a name="a-namegetpatha--cdcgetpath"></a><a name="getpath"></a>CDC::GetPath  
 检索定义的终结点的直线和曲线路径选入设备上下文中找到的控点的坐标。  
  
```  
int GetPath(
    LPPOINT lpPoints,  
    LPBYTE lpTypes,  
    int nCount) const;  
```  
  
### <a name="parameters"></a>参数  
 `lpPoints`  
 指向数组的[点](../../mfc/reference/point-structure1.md)数据结构或`CPoint`放置的对象，其中行终结点和曲线的控制点。  
  
 `lpTypes`  
 指向的顶点类型放置的位置的字节数组。 值为以下项之一︰  
  
- **PT_MOVETO**中相应的点的指定`lpPoints`开始不相互连接的图形。  
  
- **PT_LINETO**采用以前的点和相应的点的指定`lpPoints`是一条线的终结点。  
  
- **PT_BEZIERTO**中相应的点的指定`lpPoints`控点或 Bzier 曲线的结束点。  
  
 **PT_BEZIERTO**始终出现在的三个组中的类型。 在紧靠前的路径中的点定义 Bzier 曲线的起始点。 前两个**PT_BEZIERTO**了点，控点，并且第三个**PT_BEZIERTO**点是终结点 (如果硬编码)。  
  
     一个**PT_LINETO**或**PT_BEZIERTO**类型可能与以下标志结合 (通过使用按位运算符`OR`) 以指示对应的点是在图中的最后一个点，应关闭图︰  
  
- **PT_CLOSEFIGURE**在相应的行之后自动关闭图或曲线绘制的指定。 通过从直线或曲线终结点到点相对应的最后一个绘制的线闭合图形**PT_MOVETO**。  
  
 `nCount`  
 指定的总数[点](../../mfc/reference/point-structure1.md)数据结构，并可能被放在`lpPoints`数组。 此值必须与将会放入的字节数相同`lpTypes`数组。  
  
### <a name="return-value"></a>返回值  
 如果`nCount`参数不为零，点枚举数。 如果`nCount`为 0，在路径中的点的总数 (和`GetPath`向缓冲区写入任何内容)。 如果`nCount`为非零且小于的点的数量在路径中，则返回值为-1。  
  
### <a name="remarks"></a>备注  
 设备上下文必须包含封闭的路径。 在逻辑坐标中返回的路径点。 因此点存储在设备坐标的路径中`GetPath`变为点设备坐标从逻辑坐标表示通过使用当前转换的反向。 `FlattenPath`可能之前调用成员函数`GetPath`、 要将所有路径中的曲线都转换为直线线段。  
  
### <a name="example"></a>示例  
  请参阅示例[cdc:: beginpath](#beginpath)。  
  
##  <a name="a-namegetpixela--cdcgetpixel"></a><a name="getpixel"></a>CDC::GetPixel  
 检索由指定的点处的像素的 RGB 颜色值*x*和*y*。  
  
```  
COLORREF GetPixel(
    int x,  
    int y) const;  
  
COLORREF GetPixel(POINT point) const;  
```  
  
### <a name="parameters"></a>参数  
 *x*  
 指定要检查的点的逻辑 x 坐标。  
  
 *y*  
 指定要检查的点的逻辑 y 坐标。  
  
 `point`  
 指定逻辑 x 坐标和 y 坐标的点以进行检查。  
  
### <a name="return-value"></a>返回值  
 两个版本的函数，给定的点的颜色的 RGB 颜色值。 如果坐标不在的剪辑区域指定一个点，则为-1。  
  
### <a name="remarks"></a>备注  
 该点必须位于的剪辑区域。 如果该点不在的剪辑区域，该函数将不起作用，并返回 –&1;。  
  
 并非所有设备都支持**GetPixel**函数。 有关详细信息，请参阅**RC_BITBLT**光栅功能下的[GetDeviceCaps](#getdevicecaps)成员函数。  
  
 **GetPixel**成员函数有两种形式。 第一个采用两个坐标的值;第二个接受[点](../../mfc/reference/point-structure1.md)结构或[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)对象。  
  
##  <a name="a-namegetpolyfillmodea--cdcgetpolyfillmode"></a><a name="getpolyfillmode"></a>CDC::GetPolyFillMode  
 检索当前的多边形填充模式。  
  
```  
int GetPolyFillMode() const;  
```  
  
### <a name="return-value"></a>返回值  
 当前的多边形填充模式中，**备用**或**缠绕**，如果函数运行成功。  
  
### <a name="remarks"></a>备注  
 请参阅`SetPolyFillMode`成员函数，多边形填充模式的说明。  
  
##  <a name="a-namegetrop2a--cdcgetrop2"></a><a name="getrop2"></a>CDC::GetROP2  
 检索当前绘图模式。  
  
```  
int GetROP2() const;  
```  
  
### <a name="return-value"></a>返回值  
 绘制模式。 绘图模式值的列表，请参阅`SetROP2`成员函数。  
  
### <a name="remarks"></a>备注  
 绘图模式指定笔的颜色和实心对象的内部进行组合的方式与已在显示图面上的颜色。  
  
##  <a name="a-namegetsafehdca--cdcgetsafehdc"></a><a name="getsafehdc"></a>CDC::GetSafeHdc  
 调用此成员函数可获取[m_hDC](#m_hdc)，输出设备上下文。  
  
```  
HDC GetSafeHdc() const;  
```  
  
### <a name="return-value"></a>返回值  
 设备上下文句柄。  
  
### <a name="remarks"></a>备注  
 此成员函数也可使用 null 指针。  
  
##  <a name="a-namegetstretchbltmodea--cdcgetstretchbltmode"></a><a name="getstretchbltmode"></a>CDC::GetStretchBltMode  
 检索当前的位图拉伸模式。  
  
```  
int GetStretchBltMode() const;  
```  
  
### <a name="return-value"></a>返回值  
 返回值将指定当前位图拉伸模式 — **STRETCH_ANDSCANS**， **STRETCH_DELETESCANS**，或**STRETCH_ORSCANS** — 如果函数运行成功。  
  
### <a name="remarks"></a>备注  
 位图拉伸模式定义如何从拉伸或压缩来压缩的位图中删除信息`StretchBlt`成员函数。  
  
 **STRETCH_ANDSCANS**和**STRETCH_ORSCANS**模式通常用于保留单色位图中的前景色像素。 **STRETCH_DELETESCANS**模式通常用于保留彩色位图中的颜色。  
  
##  <a name="a-namegettabbedtextextenta--cdcgettabbedtextextent"></a><a name="gettabbedtextextent"></a>CDC::GetTabbedTextExtent  
 调用此成员函数来计算的宽度和高度的字符的字符串使用[m_hAttribDC](#m_hattribdc)，属性的设备上下文。  
  
```  
CSize GetTabbedTextExtent(
    LPCTSTR lpszString,  
    int nCount,  
    int nTabPositions,  
    LPINT lpnTabStopPositions) const;  
  
CSize GetTabbedTextExtent(
    const CString& str,  
    int nTabPositions,  
    LPINT lpnTabStopPositions) const;  
```  
  
### <a name="parameters"></a>参数  
 `lpszString`  
 指向一个字符的字符串。 您还可以传递[CString](../../atl-mfc-shared/reference/cstringt-class.md)为此参数的对象。  
  
 `nCount`  
 指定字符串中的字符数。 如果`nCount`为 –&1;，长度进行计算。  
  
 `nTabPositions`  
 指定指向数组中的制表位位置数`lpnTabStopPositions`。  
  
 `lpnTabStopPositions`  
 指向包含的逻辑单元中的制表位位置的整数的数组。 必须按递增顺序; 排序的制表位最小的 x 值应为数组中的第一项。 不允许向后制表位。  
  
 `str`  
 一个`CString`对象，其中包含要绘制的指定的字符。  
  
### <a name="return-value"></a>返回值  
 中的字符串 （使用逻辑单位） 的维度[CSize](../../atl-mfc-shared/reference/csize-class.md)对象。  
  
### <a name="remarks"></a>备注  
 如果该字符串包含一个或多个选项卡上的字符，将字符串的宽度取决于所指定的制表位`lpnTabStopPositions`。 该函数使用当前所选的字体来计算字符串的尺寸。  
  
 为当前剪辑区域的宽度和高度返回不偏移量`GetTabbedTextExtent`函数。  
  
 由于某些设备不要将字符放在常规单元格数组中 （也就是说，它们对大于字距调整字符），字符串中字符的扩展盘区的总和可能不等于字符串的扩展盘区。  
  
 如果`nTabPositions`为 0 和`lpnTabStopPositions`是**NULL**，选项卡扩展到八次平均字符宽度。 如果`nTabPositions`为 1，将用到的数组中的第一个值所指定的距离分隔的制表位`lpnTabStopPositions`磅为单位。 如果`lpnTabStopPositions`到多个单个值的点，制表位设置为每个值在数组中，最多指定的数量`nTabPositions`。  
  
##  <a name="a-namegettextaligna--cdcgettextalign"></a><a name="gettextalign"></a>CDC::GetTextAlign  
 检索设备上下文的文本对齐方式标志的状态。  
  
```  
UINT GetTextAlign() const;  
```  
  
### <a name="return-value"></a>返回值  
 文本对齐方式标志的状态。 返回值是一个或多个下列值︰  
  
- **TA_BASELINE**指定 x 轴的对齐方式和所选字体中的边框内的基线。  
  
- **TA_BOTTOM**指定对齐方式的 x 轴和底部的边框。  
  
- **TA_CENTER**指定 y 轴的对齐方式和边界的矩形的中心。  
  
- **TA_LEFT**指定对齐方式的 y 轴，边界矩形的左侧。  
  
- **TA_NOUPDATECP**指定不更新当前位置。  
  
- **TA_RIGHT**指定 y 轴的对齐方式和右端的绑定矩形。  
  
- **TA_TOP**指定 x 轴和边界的矩形的顶部对齐方式。  
  
- **TA_UPDATECP**指定当前位置被更新。  
  
### <a name="remarks"></a>备注  
 文本对齐方式标志确定如何`TextOut`和`ExtTextOut`成员函数对齐文本与字符串的起始点的一个字符串。 文本对齐方式标志不一定是一位标志，并且可能等于 0。 若要测试是否设置一个标志，应用程序应执行以下步骤︰  
  
1.  适用于该标志和其相关的标志，分组，如下所示的按位 OR 运算符︰  
  
    - **TA_LEFT**， **TA_CENTER**，和**TA_RIGHT**  
  
    - **TA_BASELINE**， **TA_BOTTOM**，和**TA_TOP**  
  
    - **TA_NOUPDATECP**和**TA_UPDATECP**  
  
2.  应用按位-和运算符的结果并返回值为`GetTextAlign`。  
  
3.  此结果和标志相等性测试。  
  
##  <a name="a-namegettextcharacterextraa--cdcgettextcharacterextra"></a><a name="gettextcharacterextra"></a>CDC::GetTextCharacterExtra  
 检索已 intercharacter 间距量的当前设置。  
  
```  
int GetTextCharacterExtra() const;  
```  
  
### <a name="return-value"></a>返回值  
 Intercharacter 间距量。  
  
### <a name="remarks"></a>备注  
 GDI 将此空间添加到每个字符，包括向设备上下文中写入文本行中断符。  
  
 Intercharacter 间距量的默认值为 0。  
  
##  <a name="a-namegettextcolora--cdcgettextcolor"></a><a name="gettextcolor"></a>CDC::GetTextColor  
 检索当前的文本颜色。  
  
```  
COLORREF GetTextColor() const;  
```  
  
### <a name="return-value"></a>返回值  
 当前为 RGB 颜色值的文本颜色。  
  
### <a name="remarks"></a>备注  
 文本颜色是使用 GDI 的文本输出成员函数绘制的字符的前景色[TextOut](#textout)， [ExtTextOut](#exttextout)，和[TabbedTextOut](#tabbedtextout)。  
  
##  <a name="a-namegettextextenta--cdcgettextextent"></a><a name="gettextextent"></a>CDC::GetTextExtent  
 调用此成员函数来计算的宽度和高度使用当前的字体来确定维度的文本行。  
  
```  
CSize GetTextExtent(
    LPCTSTR lpszString,  
    int nCount) const;  
  
CSize GetTextExtent(const CString& str) const;  
```  
  
### <a name="parameters"></a>参数  
 `lpszString`  
 指向字符的字符串。 您还可以传递[CString](../../atl-mfc-shared/reference/cstringt-class.md)为此参数的对象。  
  
 `nCount`  
 指定字符串中的字符数。  
  
 `str`  
 一个`CString`对象，其中包含指定的字符。  
  
### <a name="return-value"></a>返回值  
 中的字符串 （使用逻辑单位） 的维度[CSize](../../atl-mfc-shared/reference/csize-class.md)对象。  
  
### <a name="remarks"></a>备注  
 从检索的信息[m_hAttribDC](#m_hattribdc)，属性的设备上下文。  
  
 默认情况下，`GetTextExtent`假定它将检索该维度的文本设置沿着一条横线 （即，escapement 为 0）。 如果您创建指定非零值 escapement 字体，必须转换文本显式地获取字符串的尺寸的角度。  
  
 宽度和高度返回为当前剪辑区域不会影响`GetTextExtent`。  
  
 由于某些设备不要将字符放在常规单元格数组中 （也就是说，它们执行字距调整），请在字符串中字符的扩展盘区的总和可能不等于字符串的扩展盘区。  
  
##  <a name="a-namegettextextentexpointia--cdcgettextextentexpointi"></a><a name="gettextextentexpointi"></a>CDC::GetTextExtentExPointI  
 检索指定字符串将使其容纳在指定的空间，这些字符的每个文本范围与填充数组中的字符数。  
  
```  
BOOL GetTextExtentExPointI(
    LPWORD pgiIn,  
    int cgi,  
    int nMaxExtent,  
    LPINT lpnFit,  
    LPINT alpDx,  
    LPSIZE lpSize) const;  
```  
  
### <a name="parameters"></a>参数  
 `pgiIn`  
 指向的标志符号的扩展盘区为要检索的索引数组的指针。  
  
 `cgi`  
 指向数组中指定的标志符号数`pgiIn`。  
  
 `nMaxExtent`  
 使用逻辑单位，格式的字符串的指定最大允许的宽度。  
  
 `lpnFit`  
 指向接收的最大所指定的空间可容纳的字符数的计数的整数的指针`nMaxExtent`。 当`lpnFit`是**NULL**，`nMaxExtent`将被忽略。  
  
 *alpDx*  
 指向接收部分标志符号的扩展盘区的整数数组的指针。 数组中的每个元素提供了使用逻辑单位，标志符号索引数组的起始值和一个适合所指定的空间大小的标志符号之间的距离`nMaxExtent`。 尽管此数组应具有与指定的标志符号索引至少尽可能多的元素`cgi`，该函数填充的数组仅对任意多个标志符号索引为指定的扩展盘区`lpnFit`。 如果*lpnDx*是**NULL**，该函数不会计算部分字符串的宽度。  
  
 `lpSize`  
 指向[大小](http://msdn.microsoft.com/library/windows/desktop/dd145106)结构，它接收数组维度的标志符号的索引，使用逻辑单位。 此值不能为**NULL**。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 此成员函数模拟函数的功能[GetTextExtentExPointI](http://msdn.microsoft.com/library/windows/desktop/dd144936)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegettextextentpointia--cdcgettextextentpointi"></a><a name="gettextextentpointi"></a>CDC::GetTextExtentPointI  
 检索的宽度和高度指定的标志符号索引数组。  
  
```  
BOOL GetTextExtentPointI(
    LPWORD pgiIn,  
    int cgi,  
    LPSIZE lpSize) const;  
```  
  
### <a name="parameters"></a>参数  
 `pgiIn`  
 指向的标志符号的扩展盘区为要检索的索引数组的指针。  
  
 `cgi`  
 指向数组中指定的标志符号数`pgiIn`。  
  
 `lpSize`  
 指向[大小](http://msdn.microsoft.com/library/windows/desktop/dd145106)结构，它接收数组维度的标志符号的索引，使用逻辑单位。 此值不能为**NULL**。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 此成员函数模拟函数的功能[GetTextExtentPointI](http://msdn.microsoft.com/library/windows/desktop/dd144939)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegettextfacea--cdcgettextface"></a><a name="gettextface"></a>CDC::GetTextFace  
 调用此成员函数要复制到缓冲区的当前字体的字体名称。  
  
```  
int GetTextFace(
    int nCount,  
    LPTSTR lpszFacename) const;  
  
int GetTextFace(CString& rString) const;  
```  
  
### <a name="parameters"></a>参数  
 `nCount`  
 指定缓冲区的大小 （以字节为单位）。 如果超过此参数指定的字节数的字体名称，名称被截断。  
  
 *lpszFacename*  
 指向字体名称的缓冲区。  
  
 `rString`  
 对引用[CString](../../atl-mfc-shared/reference/cstringt-class.md)对象。  
  
### <a name="return-value"></a>返回值  
 将复制到缓冲区，不包括终止 null 字符的字节数。 如果发生错误，则为 0。  
  
### <a name="remarks"></a>备注  
 字体名称被复制为以 null 结尾的字符串。  
  
##  <a name="a-namegettextmetricsa--cdcgettextmetrics"></a><a name="gettextmetrics"></a>CDC::GetTextMetrics  
 检索使用属性的设备上下文的当前字体的度量值。  
  
```  
BOOL GetTextMetrics(LPTEXTMETRIC lpMetrics) const;  
```  
  
### <a name="parameters"></a>参数  
 `lpMetrics`  
 指向[TEXTMETRIC](http://msdn.microsoft.com/library/windows/desktop/dd145132)接收度量值的结构。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
##  <a name="a-namegetviewportexta--cdcgetviewportext"></a><a name="getviewportext"></a>CDC::GetViewportExt  
 检索 x-和 y 的扩展盘区的设备上下文的视区。  
  
```  
CSize GetViewportExt() const;  
```  
  
### <a name="return-value"></a>返回值  
 X-和 y 的范围 （以设备为单位） 为`CSize`对象。  
  
##  <a name="a-namegetviewportorga--cdcgetviewportorg"></a><a name="getviewportorg"></a>CDC::GetViewportOrg  
 检索与设备上下文相关联的视区原点 x 和 y 坐标。  
  
```  
CPoint GetViewportOrg() const;  
```  
  
### <a name="return-value"></a>返回值  
 （在设备坐标中） 作为在视区原点`CPoint`对象。  
  
##  <a name="a-namegetwindowa--cdcgetwindow"></a><a name="getwindow"></a>CDC::GetWindow  
 返回与显示设备上下文关联的窗口。  
  
```  
CWnd* GetWindow() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向`CWnd`对象成功，否则为如果**NULL**。  
  
### <a name="remarks"></a>备注  
 这是一项高级的功能。 例如，此成员函数可能返回视图窗口在打印时或在打印预览中。 它始终返回与输出关联的窗口。 使用给定的 DC 的输出函数将在绘制到此窗口。  
  
##  <a name="a-namegetwindowexta--cdcgetwindowext"></a><a name="getwindowext"></a>CDC::GetWindowExt  
 检索 x-和 y 的扩展盘区的设备上下文与关联的窗口。  
  
```  
CSize GetWindowExt() const;  
```  
  
### <a name="return-value"></a>返回值  
 X-和 y 的范围内 （使用逻辑单位） 为`CSize`对象。  
  
##  <a name="a-namegetwindoworga--cdcgetwindoworg"></a><a name="getwindoworg"></a>CDC::GetWindowOrg  
 检索的源设备上下文与关联的窗口的 x 和 y 坐标。  
  
```  
CPoint GetWindowOrg() const;  
```  
  
### <a name="return-value"></a>返回值  
 （以逻辑坐标表示） 窗口中，根据原点`CPoint`对象。  
  
##  <a name="a-namegetworldtransforma--cdcgetworldtransform"></a><a name="getworldtransform"></a>CDC::GetWorldTransform  
 检索页面空间转换到的当前世界空间。  
  
```  
BOOL GetWorldTransform(XFORM& rXform) const;  
```  
  
### <a name="parameters"></a>参数  
 `rXform`  
 引用[XFORM](http://msdn.microsoft.com/library/windows/desktop/dd145228)结构，它接收到页面空间转换的当前世界空间。  
  
### <a name="return-value"></a>返回值  
 如果成功返回非零值。  
  
 失败时返回 0。  
  
 若要获得扩展错误信息，请调用[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)。  
  
### <a name="remarks"></a>备注  
 此方法将包装 Windows GDI 函数[GetWorldTransform](http://msdn.microsoft.com/library/windows/desktop/dd144953)。  
  
##  <a name="a-namegradientfilla--cdcgradientfill"></a><a name="gradientfill"></a>CDC::GradientFill  
 调用该成员函数以用到另一侧顺利淡出的颜色填充矩形和三角形结构。  
  
```  
BOOL GradientFill(
    TRIVERTEX* pVertices,  
    ULONG nVertices,  
    void* pMesh,  
    ULONG nMeshElements,  
    DWORD dwMode);
```  
  
### <a name="parameters"></a>参数  
 *pVertices*  
 指向数组的指针[TRIVERTEX](http://msdn.microsoft.com/library/windows/desktop/dd145142)结构，因为每个定义三角形的顶点。  
  
 *nVertices*  
 顶点的数目。  
  
 `pMesh`  
 数组[GRADIENT_TRIANGLE](http://msdn.microsoft.com/library/windows/desktop/dd144959)三角形模式中或数组中的结构[GRADIENT_RECT](http://msdn.microsoft.com/library/windows/desktop/dd144958)矩形模式中的结构。  
  
 *nMeshElements*  
 中的元素数 （三角形或矩形） `pMesh`。  
  
 `dwMode`  
 指定渐变填充模式。 有关可能的值的列表，请参阅[GradientFill](http://msdn.microsoft.com/library/windows/desktop/dd144957)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="return-value"></a>返回值  
 **TRUE**如果成功，否则为**FALSE**。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅`GradientFill`中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegraystringa--cdcgraystring"></a><a name="graystring"></a>Cdc:: graystring  
 绘制由内存位图中写入文本、 变暗在位图中，，然后将该位图复制到显示变灰 （灰色） 中的给定位置的文本。  
  
```  
virtual BOOL GrayString(
    CBrush* pBrush,  
    BOOL (CALLBACK* lpfnOutput)(
    HDC,
    LPARAM,
    int),  
    LPARAM lpData,  
    int nCount,  
    int x,  
    int y,  
    int nWidth,  
    int nHeight);
```  
  
### <a name="parameters"></a>参数  
 `pBrush`  
 标识要用于变暗 （灰） 的画笔。  
  
 `lpfnOutput`  
 指定将绘制字符串的应用程序提供的回调函数的过程实例地址。 有关详细信息，请参阅 Windows 的说明**OutputFunc** [回调函数](../../mfc/reference/callback-function-for-cdc-graystring.md)。 如果此参数为**NULL**，系统将使用 Windows`TextOut`函数来绘制字符串，并`lpData`被假定为指向要输出的字符字符串的长指针。  
  
 `lpData`  
 指定到数据以传递到输出函数的远指针。 如果`lpfnOutput`是**NULL**，`lpData`必须是指向要输出的字符串的长指针。  
  
 `nCount`  
 指定要输出的字符数。 如果此参数为 0，`GrayString`计算字符串的长度 (假定`lpData`是指向字符串的指针)。 如果`nCount`为 – 1 和指向函数`lpfnOutput`返回 0 时，该图像时显示，但未变暗。  
  
 *x*  
 指定包含该字符串的矩形的起始位置的逻辑 x 坐标。  
  
 *y*  
 指定包含该字符串的矩形的起始位置的逻辑 y 坐标。  
  
 `nWidth`  
 指定包含该字符串的矩形的宽度 （以逻辑单位）。 如果`nWidth`为 0，`GrayString`计算的宽度区域中，假定`lpData`是指向字符串的指针。  
  
 `nHeight`  
 指定包含该字符串的矩形的高度 （以逻辑单位）。 如果`nHeight`为 0，`GrayString`计算区域的高度假定`lpData`是指向字符串的指针。  
  
### <a name="return-value"></a>返回值  
 如果绘制字符串时，则为非或 0，如果任一`TextOut`函数或应用程序提供的输出函数返回 0，或如果没有足够的内存来创建内存位图变暗。  
  
### <a name="remarks"></a>备注  
 该函数会使无论选择的画笔和背景的文本变暗。 `GrayString`成员函数使用当前选定的字体。 `MM_TEXT`使用此函数之前，必须选择映射模式。  
  
 应用程序可以在支持纯灰颜色而不调用的设备上绘制为灰色 （灰色） 字符串`GrayString`成员函数。 系统颜色**COLOR_GRAYTEXT**为用来绘制禁用的文本的实线灰色系统颜色。 应用程序可以调用**GetSysColor** Windows 函数以检索的颜色值**COLOR_GRAYTEXT**。 如果颜色不为 0 （黑色），应用程序可以调用`SetTextColor`成员函数以将文本颜色设置为颜色值，然后直接绘制字符串。 如果检索到的颜色为黑色，应用程序必须调用`GrayString`变暗 （灰色） 文本。  
  
 如果`lpfnOutput`是**NULL**，GDI 使用 Windows [TextOut](http://msdn.microsoft.com/library/windows/desktop/dd145133)函数，和`lpData`被假定为指向要输出的字符的远指针。 如果要输出的字符不能由`TextOut`成员函数 （例如，字符串将存储为位图），该应用程序必须提供其自己的输出的函数。  
  
 另请注意所有的回调函数必须捕获返回到 Windows 帐户，因为不能跨回调边界引发异常之前的 Microsoft 基础异常。 关于异常的详细信息，请参阅文章[异常](../../mfc/exception-handling-in-mfc.md)。  
  
 回调函数传递给`GrayString`必须使用`__stdcall`调用约定，并且必须使用导出`__declspec`。  
  
 框架在处于预览模式时，调用`GrayString`成员函数将转换为`TextOut`不调用调用，回调函数。  
  
##  <a name="a-namehimetrictodpa--cdchimetrictodp"></a><a name="himetrictodp"></a>CDC::HIMETRICtoDP  
 使用此函数将转换时**HIMETRIC**大小从 OLE 到像素为单位。  
  
```  
void HIMETRICtoDP(LPSIZE lpSize) const;  
```  
  
### <a name="parameters"></a>参数  
 `lpSize`  
 指向[大小](http://msdn.microsoft.com/library/windows/desktop/dd145106)结构或[CSize](../../atl-mfc-shared/reference/csize-class.md)对象。  
  
### <a name="remarks"></a>备注  
 设备上下文对象的映射模式是否`MM_LOENGLISH`， `MM_HIENGLISH`，`MM_LOMETRIC`或`MM_HIMETRIC`，则转换基于中物理英寸的像素数。 如果映射模式是其他非受限模式之一 (例如， `MM_TEXT`)，则转换基于中逻辑英寸的像素数。  
  
##  <a name="a-namehimetrictolpa--cdchimetrictolp"></a><a name="himetrictolp"></a>CDC::HIMETRICtoLP  
 调用此函数将转换**HIMETRIC**分成逻辑单元的单元。  
  
```  
void HIMETRICtoLP(LPSIZE lpSize) const;  
```  
  
### <a name="parameters"></a>参数  
 `lpSize`  
 指向[大小](http://msdn.microsoft.com/library/windows/desktop/dd145106)结构或[CSize](../../atl-mfc-shared/reference/csize-class.md)对象。  
  
### <a name="remarks"></a>备注  
 使用此函数，当您获取**HIMETRIC**大小来自 OLE，并且希望将它们转换为应用程序的自然映射模式。  
  
 转换通过首先将转换**HIMETRIC**单位为像素为单位，然后将这些单元转换为使用设备上下文的当前映射单位的逻辑单元。 请注意的设备的窗口和视区的范围将影响结果。  
  
##  <a name="a-nameintersectcliprecta--cdcintersectcliprect"></a><a name="intersectcliprect"></a>CDC::IntersectClipRect  
 通过为当前区域和指定的矩形的交集创建新的剪辑区域`x1`， `y1`， `x2`，和`y2`。  
  
```  
int IntersectClipRect(
    int x1,  
    int y1,  
    int x2,  
    int y2);  
  
int IntersectClipRect(LPCRECT lpRect);
```  
  
### <a name="parameters"></a>参数  
 `x1`  
 指定的矩形的左上角的逻辑 x 坐标。  
  
 `y1`  
 指定的矩形的左上角的逻辑 y 坐标。  
  
 `x2`  
 指定矩形右下角的逻辑 x 坐标。  
  
 `y2`  
 指定矩形右下角的逻辑 y 坐标。  
  
 `lpRect`  
 指定的矩形。 您可以传递`CRect`对象或指向的指针`RECT`结构为此参数。  
  
### <a name="return-value"></a>返回值  
 新的剪辑区域类型。 它可以是下列值之一︰  
  
- **COMPLEXREGION**新剪辑区域有重叠的边框。  
  
- **错误**设备上下文是无效的。  
  
- **NULLREGION**新剪辑区域为空。  
  
- **SIMPLEREGION**新剪辑区域具有不重叠的边框。  
  
### <a name="remarks"></a>备注  
 GDI 剪辑以适应新的边界内的所有后续输出。 宽度和高度不能超过 32767。  
  
##  <a name="a-nameinvertrecta--cdcinvertrect"></a><a name="invertrect"></a>CDC::InvertRect  
 反转给定矩形的内容。  
  
```  
void InvertRect(LPCRECT lpRect);
```  
  
### <a name="parameters"></a>参数  
 `lpRect`  
 指向`RECT`，其中包含逻辑坐标表示的矩形的反转。 您还可以传递`CRect`为此参数的对象。  
  
### <a name="remarks"></a>备注  
 反转是一个逻辑不操作和翻转的每个像素的位。 单色显示屏上函数使白色像素黑色和黑色像素白色。 在彩色显示屏上显示生成的颜色的方式取决于反转。 调用`InvertRect`两次同一矩形可显示还原到其以前的颜色。  
  
 如果该矩形为空，绘制任何内容。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&36;](../../mfc/codesnippet/cpp/cdc-class_8.cpp)]  
  
##  <a name="a-nameinvertrgna--cdcinvertrgn"></a><a name="invertrgn"></a>CDC::InvertRgn  
 反转中由指定的区域的颜色`pRgn`。  
  
```  
BOOL InvertRgn(CRgn* pRgn);
```  
  
### <a name="parameters"></a>参数  
 `pRgn`  
 标识要进行的区域。 中的逻辑单元指定区域的坐标。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 单色显示屏上函数使白色像素黑色和黑色像素白色。 在彩色显示屏上显示生成颜色的方式取决于反转。  
  
##  <a name="a-nameisprintinga--cdcisprinting"></a><a name="isprinting"></a>CDC::IsPrinting  
 确定是否正在使用的设备上下文进行打印。  
  
```  
BOOL IsPrinting() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果非零`CDC`对象是一台打印机 DC; 否则为 0。  
  
##  <a name="a-namelinetoa--cdclineto"></a><a name="lineto"></a>CDC::LineTo  
 从当前位置到，但不是包括，由指定的点绘制一条线条*x*和*y* (或`point`)。  
  
```  
BOOL LineTo(
    int x,  
    int y);  
  
BOOL LineTo(POINT point);
```  
  
### <a name="parameters"></a>参数  
 *x*  
 指定行的终结点的逻辑 x 坐标。  
  
 *y*  
 指定行的终结点的逻辑 y 坐标。  
  
 `point`  
 指定线条的端点。 您可以传递**点**结构或`CPoint`为此参数的对象。  
  
### <a name="return-value"></a>返回值  
 该线绘制; 如果非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 用所选的钢笔绘制线条。 当前位置设置为*x*， *y*或`point`。  
  
### <a name="example"></a>示例  
  请参阅示例[CRect::CenterPoint](../../atl-mfc-shared/reference/crect-class.md#centerpoint)。  
  
##  <a name="a-namelptodpa--cdclptodp"></a><a name="lptodp"></a>CDC::LPtoDP  
 将设备单位转换为逻辑单元。  
  
```  
void LPtoDP(
    LPPOINT lpPoints,  
    int nCount = 1) const;  
  
void LPtoDP(LPRECT lpRect) const;
void LPtoDP(LPSIZE lpSize) const;  
```  
  
### <a name="parameters"></a>参数  
 `lpPoints`  
 指向的点数组。 数组中的每个点都[点](../../mfc/reference/point-structure1.md)结构或[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)对象。  
  
 `nCount`  
 数组中的点的数目。  
  
 `lpRect`  
 指向[RECT](../../mfc/reference/rect-structure1.md)结构或[CRect](../../atl-mfc-shared/reference/crect-class.md)对象。 此参数用于常见的情况下将映射从逻辑设备单位的矩形。  
  
 `lpSize`  
 指向[大小](http://msdn.microsoft.com/library/windows/desktop/dd145106)结构或[CSize](../../atl-mfc-shared/reference/csize-class.md)对象。  
  
### <a name="remarks"></a>备注  
 该函数将映射每个点的坐标或大小，从 GDI 的到设备坐标系统的逻辑坐标系统的维度。 转换取决于当前的映射模式和来源的设置和设备的窗口和视区的扩展盘区。  
  
 X 坐标和 y 坐标的点是在范围内-32768 到 32767 的 2 字节有符号的整数。 在映射模式会导致值大于这些限制的情况下，系统将值设置为-32768 到 32767，分别。  
  
##  <a name="a-namelptohimetrica--cdclptohimetric"></a><a name="lptohimetric"></a>CDC::LPtoHIMETRIC  
 调用此函数将转换到逻辑单元**HIMETRIC**单位。  
  
```  
void LPtoHIMETRIC(LPSIZE lpSize) const;  
```  
  
### <a name="parameters"></a>参数  
 `lpSize`  
 指向**大小**结构或`CSize`对象。  
  
### <a name="remarks"></a>备注  
 使用此函数在您向提供**HIMETRIC**给 OLE，将从应用程序的自然映射模式转换的大小。 请注意的设备的窗口和视区的范围将影响结果。  
  
 转换通过首先将逻辑单元转换为使用设备上下文的当前映射单位，然后进行转换到这些设备的像素**HIMETRIC**单位。  
  
##  <a name="a-namemhattribdca--cdcmhattribdc"></a><a name="m_hattribdc"></a>CDC::m_hAttribDC  
 此特性设备上下文`CDC`对象。  
  
```  
HDC m_hAttribDC;  
```  
  
### <a name="remarks"></a>备注  
 默认情况下，此设备上下文是否等于`m_hDC`。 一般情况下，`CDC`请求信息从设备上下文的 GDI 调用将被定向到`m_hAttribDC`。 请参阅[CDC](../../mfc/reference/cdc-class.md)类有关的详细信息使用上述两个设备上下文的说明。  
  
##  <a name="a-namemhdca--cdcmhdc"></a><a name="m_hdc"></a>CDC::m_hDC  
 此输出设备上下文`CDC`对象。  
  
```  
HDC m_hDC;  
```  
  
### <a name="remarks"></a>备注  
 默认情况下，`m_hDC`是否等同于`m_hAttribDC`，其他设备上下文由包装`CDC`。 一般情况下， `CDC` GDI 调用创建的输出，请转到`m_hDC`设备上下文。 可以将其初始化`m_hDC`和`m_hAttribDC`以指向不同的设备。 请参阅[CDC](../../mfc/reference/cdc-class.md)类有关的详细信息使用上述两个设备上下文的说明。  
  
##  <a name="a-namemaskblta--cdcmaskblt"></a><a name="maskblt"></a>CDC::MaskBlt  
 将组合使用给定的掩码和光栅操作的源和目标位图的颜色数据。  
  
```  
BOOL MaskBlt(
    int x,  
    int y,  
    int nWidth,  
    int nHeight,  
    CDC* pSrcDC,  
    int xSrc,  
    int ySrc,  
    CBitmap& maskBitmap,  
    int xMask,  
    int yMask,  
    DWORD dwRop);
```  
  
### <a name="parameters"></a>参数  
 *x*  
 指定目标矩形的左上角的逻辑 x 坐标。  
  
 *y*  
 指定目标矩形的左上角的逻辑 y 坐标。  
  
 `nWidth`  
 指定不使用逻辑单位，目标矩形，源位图的宽度。  
  
 `nHeight`  
 指定的高度，以目标矩形，源位图的逻辑单元。  
  
 `pSrcDC`  
 标识是要复制位图的设备上下文。 它必须为零*dwRop*参数指定的光栅操作中不包含源。  
  
 `xSrc`  
 指定的源位图的左上角的逻辑 x 坐标。  
  
 `ySrc`  
 指定的源位图的左上角的逻辑 y 坐标。  
  
 `maskBitmap`  
 标识与源设备上下文中的颜色位图组合的单色屏蔽位图。  
  
 `xMask`  
 指定由指定的掩码位图的像素水平偏移量`maskBitmap`参数。  
  
 `yMask`  
 指定由指定的掩码位图的像素垂直偏移量`maskBitmap`参数。  
  
 *dwRop*  
 指定前景色和背景三元光栅操作代码，该函数使用，以便控制源和目标数据的组合。 背景光栅操作代码存储在此值; 该值的高位字的高字节前景色光栅操作代码存储在此值; 该值的高位字的低位字节此值的低位字将被忽略，并且应为零。 该宏**MAKEROP4**光栅操作代码将创建这种组合的前景色和背景。 请参阅有关的讨论前景色和背景此函数的上下文中的备注部分。 请参阅`BitBlt`常见光栅操作代码的列表的成员函数。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 如果值为 1 中所指定的掩码`maskBitmap`指示指定前景色光栅操作代码*dwRop*应该应用于该位置。 掩码中的 0 值指示指定背景光栅操作代码*dwRop*应该应用于该位置。 光栅操作需要一个源，如果掩码矩形必须包含源矩形。 如果不存在，该功能将失败。 光栅操作不需要一个源，如果掩码矩形必须包含目标矩形。 如果不存在，该功能将失败。  
  
 如果旋转或切变变换，则源设备上下文调用此函数时，就会出错。 但是，允许其他类型的转换。  
  
 如果源、 模式和目标位图的颜色格式不同，此函数将转换模式源格式和 / 或目标的格式相匹配。 如果掩码位图不是单色位图，就会出错。 当记录增强型图元文件时，发生错误 （和该函数返回 0） 如果源设备上下文确定的增强型图元文件设备上下文。 并非所有设备都支持`MaskBlt`。 应用程序应调用`GetDeviceCaps`来确定设备是否支持此函数。 如果提供不使用掩码位图，则此函数的行为完全类似`BitBlt`，使用前景色光栅操作代码。 像素中的偏移量掩码位图映射到点 (0，0) 的源设备上下文位图中。 这对于顺序掩码位图包含一组掩码; 的情况下很有用应用程序可以轻松地应用其中任何一个为掩码平面闪任务通过调整像素偏移量和矩形大小发送到`MaskBlt`。  
  
##  <a name="a-namemodifyworldtransforma--cdcmodifyworldtransform"></a><a name="modifyworldtransform"></a>CDC::ModifyWorldTransform  
 更改为使用指定的模式的设备上下文的世界变换。  
  
```  
BOOL ModifyWorldTransform(
    const XFORM& rXform,  
    DWORD iMode);
```  
  
### <a name="parameters"></a>参数  
 `rXform`  
 引用[XFORM](http://msdn.microsoft.com/library/windows/desktop/dd145228)用于修改给定的设备上下文的世界变换的结构。  
  
 `iMode`  
 指定如何转换数据修改的当前世界变换。 此参数可以采用的值的列表，请参阅[ModifyWorldTransform](http://msdn.microsoft.com/library/windows/desktop/dd145060)。  
  
### <a name="return-value"></a>返回值  
 如果成功返回非零值。  
  
 失败时返回 0。  
  
 若要获得扩展错误信息，请调用[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)。  
  
### <a name="remarks"></a>备注  
 此方法将包装 Windows GDI 函数[ModifyWorldTransform](http://msdn.microsoft.com/library/windows/desktop/dd145060)。  
  
##  <a name="a-namemovetoa--cdcmoveto"></a><a name="moveto"></a>CDC::MoveTo  
 将当前位置移动到指定的点*x*和*y* (或由`point`)。  
  
```  
CPoint MoveTo(
    int x,  
    int y);  
  
CPoint MoveTo(POINT point);
```  
  
### <a name="parameters"></a>参数  
 *x*  
 指定新位置的逻辑 x 坐标。  
  
 *y*  
 指定新位置的逻辑 y 坐标。  
  
 `point`  
 指定新位置。 您可以传递**点**结构或`CPoint`为此参数的对象。  
  
### <a name="return-value"></a>返回值  
 前一个位置作为 x 和 y 坐标`CPoint`对象。  
  
### <a name="example"></a>示例  
  请参阅示例[CRect::CenterPoint](../../atl-mfc-shared/reference/crect-class.md#centerpoint)。  
  
##  <a name="a-nameoffsetcliprgna--cdcoffsetcliprgn"></a><a name="offsetcliprgn"></a>CDC::OffsetClipRgn  
 按指定的偏移量移动设备上下文的剪辑区域。  
  
```  
int OffsetClipRgn(
    int x,  
    int y);  
  
int OffsetClipRgn(SIZE size);
```  
  
### <a name="parameters"></a>参数  
 *x*  
 指定要向左移动或向右的逻辑单元数。  
  
 *y*  
 指定要上移或下移的逻辑单元数。  
  
 `size`  
 指定的偏移量。  
  
### <a name="return-value"></a>返回值  
 新的区域类型。 它可以是下列值之一︰  
  
- **COMPLEXREGION**剪辑区域有重叠的边框。  
  
- **错误**设备上下文是无效的。  
  
- **NULLREGION**剪辑区域为空。  
  
- **SIMPLEREGION**剪辑区域具有不重叠的边框。  
  
### <a name="remarks"></a>备注  
 该函数将移动区域*x*沿 x 轴单位并*y*沿 y 轴的单位。  
  
##  <a name="a-nameoffsetviewportorga--cdcoffsetviewportorg"></a><a name="offsetviewportorg"></a>CDC::OffsetViewportOrg  
 修改视区原点相对于当前视区原点坐标的坐标。  
  
```  
virtual CPoint OffsetViewportOrg(
    int nWidth,  
    int nHeight);
```  
  
### <a name="parameters"></a>参数  
 `nWidth`  
 指定设备将添加到当前原点的 x 坐标的单位数。  
  
 `nHeight`  
 指定设备将添加到当前原点的 y 坐标的单位数。  
  
### <a name="return-value"></a>返回值  
 上一个视区原点 （以设备坐标中） 作为`CPoint`对象。  
  
##  <a name="a-nameoffsetwindoworga--cdcoffsetwindoworg"></a><a name="offsetwindoworg"></a>CDC::OffsetWindowOrg  
 修改的相对于当前窗口原点坐标窗口原点的坐标。  
  
```  
CPoint OffsetWindowOrg(
    int nWidth,  
    int nHeight);
```  
  
### <a name="parameters"></a>参数  
 `nWidth`  
 指定将添加到当前原点的 x 坐标的逻辑单元数。  
  
 `nHeight`  
 指定将添加到当前原点的 y 坐标的逻辑单元数。  
  
### <a name="return-value"></a>返回值  
 （以逻辑坐标表示） 为上一个窗口原点`CPoint`对象。  
  
##  <a name="a-nameoperatorhdca--cdcoperator-hdc"></a><a name="operator_hdc"></a>CDC::operator HDC  
 使用此运算符将检索的设备上下文句柄`CDC`对象。  
  
```  
operator HDC() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果成功，设备上下文对象; 的句柄否则为**NULL**。  
  
### <a name="remarks"></a>备注  
 该句柄可用于直接调用 Windows Api。  
  
##  <a name="a-namepaintrgna--cdcpaintrgn"></a><a name="paintrgn"></a>CDC::PaintRgn  
 填充由指定的区域`pRgn`使用当前画笔。  
  
```  
BOOL PaintRgn(CRgn* pRgn);
```  
  
### <a name="parameters"></a>参数  
 `pRgn`  
 标识要填充的区域。 中的逻辑单元指定给定区域的坐标。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
##  <a name="a-namepatblta--cdcpatblt"></a><a name="patblt"></a>CDC::PatBlt  
 在设备上创建一个位模式。  
  
```  
BOOL PatBlt(
    int x,  
    int y,  
    int nWidth,  
    int nHeight,  
    DWORD dwRop);
```  
  
### <a name="parameters"></a>参数  
 *x*  
 指定要接收模式的矩形的左上角的逻辑 x 坐标。  
  
 *y*  
 指定要接收模式的矩形的左上角的逻辑 y 坐标。  
  
 `nWidth`  
 指定要接收模式的矩形的宽度 （以逻辑单位）。  
  
 `nHeight`  
 指定要接收模式的矩形的高度 （使用逻辑单位）。  
  
 *dwRop*  
 指定的光栅操作代码。 光栅操作代码 (ROPs) 定义 GDI 如何合并涉及当前画笔、 可能的源位图和目标位图的输出操作中的颜色。 此参数可以是下列值之一︰  
  
- **PATCOPY**副本模式与目标位图。  
  
- **PATINVERT**使用模式，即使用布尔 XOR 运算符合并目标位图。  
  
- **DSTINVERT** -反转目标位图。  
  
- **BLACKNESS** -使所有输出黑变。  
  
- **WHITENESS** -使所有输出白色变。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 模式是选择的画笔和已在设备上的模式的组合。 通过指定的光栅操作代码*dwRop*定义这些模式是组合在一起的方式。 列出此函数的光栅操作将完全 256 的三元光栅操作代码; 的受限子网具体而言，不能使用引用的源的光栅操作代码。  
  
 并非所有的设备上下文支持`PatBlt`函数。 若要确定设备上下文是否支持`PatBlt`，调用`GetDeviceCaps`成员函数时**RASTERCAPS**编制索引，并检查返回值**RC_BITBLT**标志。  
  
##  <a name="a-namepiea--cdcpie"></a><a name="pie"></a>CDC::Pie  
 通过绘制椭圆弧按行加入其中心和两个终结点来绘制饼形楔形。  
  
```  
BOOL Pie(
    int x1,  
    int y1,  
    int x2,  
    int y2,  
    int x3,  
    int y3,  
    int x4,  
    int y4);

 
BOOL Pie(
    LPCRECT lpRect,
    POINT ptStart,
    POINT ptEnd);
```  
  
### <a name="parameters"></a>参数  
 `x1`  
 指定 （使用逻辑单位） 的绑定矩形的左上角的 x 坐标。  
  
 `y1`  
 指定 （使用逻辑单位） 的绑定矩形的左上角的 y 坐标。  
  
 `x2`  
 指定的边框 （使用逻辑单位） 的右下角的 x 坐标。  
  
 `y2`  
 指定的边框 （使用逻辑单位） 的右下角的 y 坐标。  
  
 *x3*  
 指定 （使用逻辑单位） 的弧线的起始点的 x 坐标。 此时没有要将其完全置于弧。  
  
 `y3`  
 指定 （使用逻辑单位） 的弧线的起始点的 y 坐标。 此时没有要将其完全置于弧。  
  
 `x4`  
 指定 （使用逻辑单位） 的弧线的终结点的 x 坐标。 此时没有要将其完全置于弧。  
  
 `y4`  
 指定 （使用逻辑单位） 的弧线的终结点的 y 坐标。 此时没有要将其完全置于弧。  
  
 `lpRect`  
 指定的绑定矩形。 您可以传递`CRect`对象或指向的指针`RECT`结构为此参数。  
  
 `ptStart`  
 指定弧线的起始点。 此时没有要将其完全置于弧。 您可以传递[点](../../mfc/reference/point-structure1.md)结构或[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)为此参数的对象。  
  
 `ptEnd`  
 指定弧线的终结点。 此时没有要将其完全置于弧。 您可以传递**点**结构或`CPoint`为此参数的对象。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 圆弧的中心是由指定的绑定矩形的中心`x1`， `y1`， `x2`，和`y2`(或由`lpRect`)。 通过指定起点和终点的圆弧*x3*， `y3`， `x4`，和`y4`(或由`ptStart`和`ptEnd`)。  
  
 以逆时针方向移动所选笔绘制弧。 到弧线的中心，从每个终结点绘制两个其他的线。 饼形区域是用当前画笔填充的。 如果*x3*等于`x4`和`y3`等于`y4`，结果是具有单个行中的椭圆的中心到点的椭圆 ( *x3*， `y3`) 或 ( `x4`， `y4`)。  
  
 此函数绘制图最多扩展，但不包括右边和底边坐标。 这意味着该图的高度是`y2`–`y1`和图形的宽度是`x2`– `x1`。 宽度和边框的高度必须大于 2 个单位和小于 32767 个单位。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&37;](../../mfc/codesnippet/cpp/cdc-class_9.cpp)]  
  
##  <a name="a-nameplaymetafilea--cdcplaymetafile"></a><a name="playmetafile"></a>CDC::PlayMetaFile  
 在设备上下文上播放指定的图元文件的内容。  
  
```  
BOOL PlayMetaFile(HMETAFILE hMF);

 
BOOL PlayMetaFile(
    HENHMETAFILE hEnhMetaFile,  
    LPCRECT lpBounds);
```  
  
### <a name="parameters"></a>参数  
 *hMF*  
 标识要播放的图元文件。  
  
 *hEnhMetaFile*  
 标识增强型图元文件。  
  
 `lpBounds`  
 指向`RECT`结构或`CRect`对象，其中包含用来显示该图片的边框的坐标。 中的逻辑单元指定坐标。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 任意数量的时间就可以播放图元文件。  
  
 第二版`PlayMetaFile`显示存储在给定的增强格式图元文件中的图片。 在应用程序调用第二版`PlayMetaFile`，Windows 图片框中使用增强型图元文件标头映射到指向矩形图片`lpBounds`参数。 (此图片可能剪切或通过设置世界转换中的输出设备，然后才能调用旋转`PlayMetaFile`。)在图片中包含的矩形的边缘点时。 可以通过在增强型图元文件播放之前在输出设备中定义的剪辑区域剪切增强型图元文件图片。  
  
 增强型图元文件中包含可选的调色板，如果应用程序可以通过在调用的第二个版本之前设置调色板，一种输出设备上实现一致的颜色`PlayMetaFile`。 若要检索的可选调色板，请使用**GetEnhMetaFilePaletteEntries** Windows 函数。 增强型图元文件可在新创建增强型图元文件中嵌入的调用的第二个版本`PlayMetaFile`和新播放到设备上下文的源增强型图元文件增强型图元文件。  
  
 此函数将保留输出设备上下文的状态。 此函数将删除任何对象创建，但不是删除在增强型图元文件中。 若要停止此函数，应用程序可以调用**CancelDC** Windows 函数从另一个线程来终止操作。 在这种情况下，该函数将返回零。  
  
##  <a name="a-nameplgblta--cdcplgblt"></a><a name="plgblt"></a>CDC::PlgBlt  
 来自源设备上下文中指定的矩形执行颜色数据的位的位块传输到给定的设备上下文中指定的平行四边形。  
  
```  
BOOL PlgBlt(
    LPPOINT lpPoint,  
    CDC* pSrcDC,  
    int xSrc,  
    int ySrc,  
    int nWidth,  
    int nHeight,  
    CBitmap& maskBitmap,  
    int xMask,  
    int yMask);
```  
  
### <a name="parameters"></a>参数  
 `lpPoint`  
 指向数组中标识目标平行四边形的三个角的逻辑空间三个点。 源矩形的左上角映射到此数组，此数组中的第二个点的右上角，然后向第三个点的左下角的第一个点。 源矩形的右下角映射到在平行四边形中隐式的第四个点。  
  
 `pSrcDC`  
 标识源设备上下文。  
  
 `xSrc`  
 指定使用逻辑单位，源矩形的左上角的 x 坐标。  
  
 `ySrc`  
 指定使用逻辑单位，源矩形的左上角的 y 坐标。  
  
 `nWidth`  
 指定不使用逻辑单位，源矩形的宽度。  
  
 `nHeight`  
 指定使用逻辑单位，源矩形的高度。  
  
 `maskBitmap`  
 标识用于屏蔽一些源矩形的颜色的可选单色位图。  
  
 `xMask`  
 指定的单色位图左上角的 x 坐标。  
  
 `yMask`  
 指定的单色位图左上角的 y 坐标。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 如果给定的位掩码句柄标识有效的单色位图，该函数将使用此位图来掩码的源矩形的颜色数据位。  
  
 平行四边形 (D) 的第四个顶点定义通过将前三个点 （A、 B 和 C） 向量，并计算 D = B + C-a。  
  
 如果存在位掩码，值为 1 掩码中指示源像素颜色应复制到目标。 掩码中的 0 值表示，目标像素颜色是不能更改。  
  
 如果掩码矩形小于源和目标矩形，该函数将复制的掩码模式。  
  
 缩放、 平移和反射转换可以用在源设备上下文;但是，旋转和切变转换不是。 如果掩码位图不是单色位图，就会出错。 目标设备上下文的拉伸模式用于确定如何拉伸或压缩像素为单位，如果这是必需的。 当记录增强型图元文件时，如果源设备上下文确定的增强型图元文件设备上下文，就会出错。  
  
 目标坐标将根据目标设备上下文进行转换；源坐标将根据源设备上下文进行转换。 如果源转换具有旋转或切变，则返回错误。 如果目标和源矩形不具有相同的颜色格式，`PlgBlt`将转换源矩形以匹配目标矩形。 并非所有设备都支持`PlgBlt`。 有关详细信息，请参阅说明**RC_BITBLT**中的光栅功能`CDC::GetDeviceCaps`成员函数。  
  
 如果源和目标设备上下文表示不兼容的设备，`PlgBlt`返回错误。  
  
##  <a name="a-namepolybeziera--cdcpolybezier"></a><a name="polybezier"></a>CDC::PolyBezier  
 绘制一个或多个 Bzier 样条。  
  
```  
BOOL PolyBezier(
    const POINT* lpPoints,  
    int nCount);
```  
  
### <a name="parameters"></a>参数  
 `lpPoints`  
 指向数组的[点](../../mfc/reference/point-structure1.md)包含终结点和控制点 spline(s) 的数据结构。  
  
 `nCount`  
 指定的中点数目`lpPoints`数组。 此值必须为一个要绘制的样条数的三倍以上，由于每个 Bzier 样条要求两个控点和终结点，以及初始样条要求附加的起始点。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 此函数使用的终结点和由指定的控件点绘制立方 Bzier 样条`lpPoints`参数。 第一个样条是绘制从第一个点到四个点使用的第二个和第三个点作为控点。 在序列中的每个后续样条需要完全三个点︰ 以前样条曲线的终点用作起始点、 在序列中的接下来两个点是控点和第三个是终结点。  
  
 当前的位置，既不使用也不由更新`PolyBezier`函数。 不填充该图中。 此函数使用当前的钢笔绘制线条。  
  
##  <a name="a-namepolybeziertoa--cdcpolybezierto"></a><a name="polybezierto"></a>CDC::PolyBezierTo  
 绘制一个或多个 Bzier 样条。  
  
```  
BOOL PolyBezierTo(
    const POINT* lpPoints,  
    int nCount);
```  
  
### <a name="parameters"></a>参数  
 `lpPoints`  
 指向数组的[点](../../mfc/reference/point-structure1.md)点包含的终结点和控件的数据结构。  
  
 `nCount`  
 指定的中点数目`lpPoints`数组。 此值必须是三次样条要绘制的数，因为每个 Bzier 样条需要两个控点和一个终结点。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 此函数通过使用由指定的控件点绘制立方 Bzier 样条`lpPoints`参数。 第一个样条绘制从当前位置到第三个点为控制点使用前两个点。 每个后续样条，该函数需要完全三个点，并作为起始点的上一个样条终结点用于下一步。 `PolyBezierTo`将当前位置移动到最后一个 Bzier 样条曲线的结束点。 不填充该图中。 此函数使用当前的钢笔绘制线条。  
  
### <a name="example"></a>示例  
  请参阅示例[cdc:: beginpath](#beginpath)。  
  
##  <a name="a-namepolydrawa--cdcpolydraw"></a><a name="polydraw"></a>CDC::PolyDraw  
 绘制直线线段和 Bzier 样条的一组。  
  
```  
BOOL PolyDraw(
    const POINT* lpPoints,  
    const BYTE* lpTypes,  
    int nCount);
```  
  
### <a name="parameters"></a>参数  
 `lpPoints`  
 指向数组的[点](../../mfc/reference/point-structure1.md)包含每个终结点的数据结构行段和终结点和控制每个 Bzier 样条曲线的点。  
  
 `lpTypes`  
 数组，它指定每个中的点到点`lpPoints`使用数组。 值可以是以下项之一︰  
  
- **PT_MOVETO**指定该点开始不相互连接图。 此点将变为新的当前位置。  
  
- **PT_LINETO**指定一条线是从当前位置绘制到目前为止，随后将成为新的当前位置。  
  
- **PT_BEZIERTO**指定此点控制点或 Bzier 样条曲线的结束点。  
  
 **PT_BEZIERTO**始终出现在的三个组中的类型。 当前位置定义 Bzier 样条曲线的起始点。 前两个**PT_BEZIERTO**了点，控点，并且第三个**PT_BEZIERTO**点是结束点。 结束点将变为新的当前位置。 如果没有将三个连续**PT_BEZIERTO**点、 产生错误。  
  
     一个**PT_LINETO**或**PT_BEZIERTO**类型可以通过使用按位运算符组合使用以下常量或以指示对应的点是一个数字和图中的最后一点已关闭︰  
  
- **PT_CLOSEFIGURE**后自动关闭该图中的指定**PT_LINETO**或**PT_BEZIERTO**完成此点的类型。 到最新版本从该点绘制一条线**PT_MOVETO**或`MoveTo`点。  
  
     此标志结合**PT_LINETO**类型对于线条，或与**PT_BEZIERTO**的结束点 Bzier 样条，通过使用按位类型`OR`运算符。 当前位置设置为结束行的结束点。  
  
 `nCount`  
 指定的中点总数`lpPoints`，数组中的字节数相同`lpTypes`数组。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 此函数可用于绘制代替连续调用不相互连接图`CDC::MoveTo`， `CDC::LineTo`，和`CDC::PolyBezierTo`成员函数。 使用当前笔绘制的直线和曲线样条和图未被填充。 如果没有活动路径通过调用启动`CDC::BeginPath`成员函数，`PolyDraw`将添加到路径。 中包含的点`lpPoints`数组并在`lpTypes`指示每个点是否属于`CDC::MoveTo`、 `CDC::LineTo`，或**CDC::BezierTo**操作。 还有可能要关闭图。 此函数更新当前位置。  
  
### <a name="example"></a>示例  
  请参阅示例[cdc:: beginpath](#beginpath)。  
  
##  <a name="a-namepolygona--cdcpolygon"></a><a name="polygon"></a>CDC::Polygon  
 绘制一个包含两个或多个连接的点 （顶点） 线路，使用当前笔的多边形。  
  
```  
BOOL Polygon(
    LPPOINT lpPoints,  
    int nCount);
```  
  
### <a name="parameters"></a>参数  
 `lpPoints`  
 指向数组指定的多边形顶点的点。 数组中的每个点都**点**结构或`CPoint`对象。  
  
 `nCount`  
 指定数组中的顶点数。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 系统多边形将自动关闭，如有必要，通过从最后一个顶点与第一个绘制的线。  
  
 可以检索或设置通过使用当前的多边形填充模式`GetPolyFillMode`和`SetPolyFillMode`成员函数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&38;](../../mfc/codesnippet/cpp/cdc-class_10.cpp)]  
  
##  <a name="a-namepolylinea--cdcpolyline"></a><a name="polyline"></a>CDC::Polyline  
 绘制的直线线段连接由指定的点的一组`lpPoints`。  
  
```  
BOOL Polyline(
    LPPOINT lpPoints,  
    int nCount);
```  
  
### <a name="parameters"></a>参数  
 `lpPoints`  
 指向数组的**点**结构或`CPoint`要连接的对象。  
  
 `nCount`  
 数组中指定的点的数量。 此值必须至少为 2。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 从通过使用当前笔的后续点的第一个点绘制线条。 与不同`LineTo`成员函数，`Polyline`函数既不使用也不更新当前位置。  
  
 有关详细信息，请参阅[折线](http://msdn.microsoft.com/library/windows/desktop/dd162815)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namepolylinetoa--cdcpolylineto"></a><a name="polylineto"></a>CDC::PolylineTo  
 绘制一个或多个直线。  
  
```  
BOOL PolylineTo(
    const POINT* lpPoints,  
    int nCount);
```  
  
### <a name="parameters"></a>参数  
 `lpPoints`  
 指向数组的[点](../../mfc/reference/point-structure1.md)包含行的顶点数据结构。  
  
 `nCount`  
 数组中指定的点的数量。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 绘制一条线是从当前位置到由指定的第一个点`lpPoints`通过使用当前笔的参数。 为每个其他行，则该函数绘制从前一行的行的结束点到由指定的下一步点`lpPoints`。 `PolylineTo`将当前位置移到最后一行的结束点。 如果此函数绘制的直线线段构成闭合的图形，该图中未填写。  
  
##  <a name="a-namepolypolygona--cdcpolypolygon"></a><a name="polypolygon"></a>CDC::PolyPolygon  
 创建两个或多个使用当前的多边形填充模式填充的多边形。  
  
```  
BOOL PolyPolygon(
    LPPOINT lpPoints,  
    LPINT lpPolyCounts,  
    int nCount);
```  
  
### <a name="parameters"></a>参数  
 `lpPoints`  
 指向数组的**点**结构或`CPoint`定义多边形顶点的对象。  
  
 `lpPolyCounts`  
 指向整数的数组，其中每个中的多边形之一中指定的点的数量`lpPoints`数组。  
  
 `nCount`  
 中的项数`lpPolyCounts`数组。 此数字指定要绘制的多边形的数量。 此值必须至少为 2。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 多边形可能是不相互连接或重叠。  
  
 对调用中指定每个多边形`PolyPolygon`函数必须关闭。 与多边形创建的不同**多边形**成员函数，通过创建的多边形`PolyPolygon`不会自行关闭。  
  
 该函数将创建两个或多个多边形。 若要创建单个多边形，应用程序应使用**多边形**成员函数。  
  
 可以检索或设置通过使用当前的多边形填充模式`GetPolyFillMode`和`SetPolyFillMode`成员函数。  
  
##  <a name="a-namepolypolylinea--cdcpolypolyline"></a><a name="polypolyline"></a>CDC::PolyPolyline  
 绘制多个系列相连的线段。  
  
```  
BOOL PolyPolyline(
    const POINT* lpPoints,  
    const DWORD* lpPolyPoints,  
    int nCount);
```  
  
### <a name="parameters"></a>参数  
 `lpPoints`  
 指向包含折线的顶点的结构的数组。 折线是连续指定的。  
  
 `lpPolyPoints`  
 指向数组的变量指定的中点的数量`lpPoints`数组中相应的多边形。 每个条目必须大于或等于 2。  
  
 `nCount`  
 指定的总数中的计数`lpPolyPoints`数组。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 使用当前笔进行绘制的直线线段。 不填充由的段格式的数字。 当前的位置不使用也不更新此函数。  
  
##  <a name="a-nameptvisiblea--cdcptvisible"></a><a name="ptvisible"></a>CDC::PtVisible  
 确定给定的点是否在设备上下文的剪辑区域内。  
  
```  
virtual BOOL PtVisible(
    int x,  
    int y) const;  
  
BOOL PtVisible(POINT point) const;  
```  
  
### <a name="parameters"></a>参数  
 *x*  
 指定的点的逻辑 x 坐标。  
  
 *y*  
 指定的点的逻辑 y 坐标。  
  
 `point`  
 指定要检查以逻辑坐标表示的点。 您可以传递**点**结构或`CPoint`为此参数的对象。  
  
### <a name="return-value"></a>返回值  
 非零值指定的点是否位于的剪辑区域;否则为 0。  
  
##  <a name="a-namequeryaborta--cdcqueryabort"></a><a name="queryabort"></a>CDC::QueryAbort  
 调用 abort 函数由安装[SetAbortProc](#setabortproc)成员用于打印的应用程序和查询是否应终止打印的功能。  
  
```  
BOOL QueryAbort() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果应继续打印或无中止过程返回的值不为零。 如果应终止打印作业，则为 0。 Abort 函数提供返回值。  
  
##  <a name="a-namerealizepalettea--cdcrealizepalette"></a><a name="realizepalette"></a>CDC::RealizePalette  
 将映射到系统调色板条目来自当前逻辑调色板。  
  
```  
UINT RealizePalette();
```  
  
### <a name="return-value"></a>返回值  
 表示逻辑调色板中的多个条目已映射到不同系统调色板中的条目。 这表示此函数重新映射，以适应系统调色板中的更改，因为上一次实现逻辑调色板的条目数。  
  
### <a name="remarks"></a>备注  
 逻辑调色板充当了缓冲区之间颜色密集型应用程序和系统，以便应用程序使用多根据需要而不会干扰具有自己的颜色显示颜色或与其他窗口所显示颜色。  
  
 当窗口具有输入的焦点并调用`RealizePalette`，Windows 可确保窗口将显示所有请求的颜色，最大的数在屏幕上同时可用。 Windows 还将显示在窗口的调色板中未找到通过将它们与可用的颜色匹配的颜色。  
  
 此外，Windows 请求的可用颜色到尽可能真实地调用该函数的非活动窗口的颜色相匹配。 这极大地减少了不必要的更改，在非活动窗口中显示的颜色。  
  
##  <a name="a-namerectanglea--cdcrectangle"></a><a name="rectangle"></a>CDC::Rectangle  
 绘制一个矩形使用当前笔。  
  
```  
BOOL Rectangle(
    int x1,  
    int y1,  
    int x2,  
    int y2);  
  
BOOL Rectangle(LPCRECT lpRect);
```  
  
### <a name="parameters"></a>参数  
 `x1`  
 指定 （使用逻辑单位） 的矩形的左上角的 x 坐标。  
  
 `y1`  
 指定 （使用逻辑单位） 的矩形的左上角的 y 坐标。  
  
 `x2`  
 指定的矩形 （使用逻辑单位） 的右下角的 x 坐标。  
  
 `y2`  
 指定的矩形 （使用逻辑单位） 的右下角的 y 坐标。  
  
 `lpRect`  
 使用逻辑单位指定的矩形。 您可以传递`CRect`对象或指向的指针`RECT`结构为此参数。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 使用当前画笔填充的矩形的内部。  
  
 该矩形将扩展最多，但不包括右边和底边坐标。 这意味着的矩形的高度是`y2`–`y1`的矩形的宽度为`x2`– `x1`。 宽度和一个矩形的高度必须大于 2 个单位和小于 32767 个单位。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&39;](../../mfc/codesnippet/cpp/cdc-class_11.cpp)]  
  
##  <a name="a-namerectvisiblea--cdcrectvisible"></a><a name="rectvisible"></a>CDC::RectVisible  
 确定是否显示上下文的剪辑区域内存在于给定的任何的矩形部分。  
  
```  
virtual BOOL RectVisible(LPCRECT lpRect) const;  
```  
  
### <a name="parameters"></a>参数  
 `lpRect`  
 指向`RECT`结构或`CRect`对象，其中包含指定的矩形的逻辑坐标。  
  
### <a name="return-value"></a>返回值  
 非零，如果给定的任何的矩形一部分之内的剪辑区域;否则为 0。  
  
##  <a name="a-namereleaseattribdca--cdcreleaseattribdc"></a><a name="releaseattribdc"></a>CDC::ReleaseAttribDC  
 调用此成员函数以设置`m_hAttribDC`到**NULL**。  
  
```  
virtual void ReleaseAttribDC();
```  
  
### <a name="remarks"></a>备注  
 这不会导致**分离**发生。 只输出设备上下文附加到`CDC`对象，并且它仅可以分离。  
  
##  <a name="a-namereleaseoutputdca--cdcreleaseoutputdc"></a><a name="releaseoutputdc"></a>CDC::ReleaseOutputDC  
 调用此成员函数以设置`m_hDC`成员**NULL**。  
  
```  
virtual void ReleaseOutputDC();
```  
  
### <a name="remarks"></a>备注  
 不能调用此成员函数，当输出设备上下文附加到`CDC`对象。 使用**分离**成员函数以分离输出设备上下文。  
  
##  <a name="a-nameresetdca--cdcresetdc"></a><a name="resetdc"></a>CDC::ResetDC  
 调用此成员函数以更新设备上下文由包装`CDC`对象。  
  
```  
BOOL ResetDC(const DEVMODE* lpDevMode);
```  
  
### <a name="parameters"></a>参数  
 *lpDevMode*  
 一个指向 Windows`DEVMODE`结构。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 从 Windows 中指定的信息更新的设备上下文`DEVMODE`结构。 此成员函数仅重置属性的设备上下文。  
  
 应用程序通常将使用`ResetDC`成员函数，当一个窗口处理`WM_DEVMODECHANGE`消息。 此成员函数还可用于在打印文档时更改纸张方向或纸张的箱中。  
  
 此成员函数不能用于更改驱动程序名称、 设备名称，或输出端口。 当用户更改端口连接或设备名称时，必须删除原始的设备上下文，然后使用新的信息创建新的设备上下文。  
  
 调用此成员函数之前，必须确保已选入设备上下文的所有对象 （而不是常用的对象） 具有出所都选。  
  
##  <a name="a-namerestoredca--cdcrestoredc"></a><a name="restoredc"></a>CDC::RestoreDC  
 将设备上下文恢复到以前的状态由标识`nSavedDC`。  
  
```  
virtual BOOL RestoreDC(int nSavedDC);
```  
  
### <a name="parameters"></a>参数  
 `nSavedDC`  
 指定要还原的设备上下文。 它可以返回先前值`SaveDC`函数调用。 如果`nSavedDC`为 –&1;，最近保存设备上下文将得以还原。  
  
### <a name="return-value"></a>返回值  
 如果指定的上下文还原; 非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 `RestoreDC`将设备上下文的状态信息从创建到以前的调用堆栈中弹出还原`SaveDC`成员函数。  
  
 堆栈可以包含多个设备上下文的状态信息。 如果上下文由`nSavedDC`不在堆栈上，顶部`RestoreDC`删除由指定的设备上下文之间的所有状态信息`nSavedDC`和堆栈的顶部。 已删除的信息将丢失。  
  
##  <a name="a-nameroundrecta--cdcroundrect"></a><a name="roundrect"></a>CDC::RoundRect  
 使用当前笔的圆角绘制一个矩形。  
  
```  
BOOL RoundRect(
    int x1,  
    int y1,  
    int x2,  
    int y2,  
    int x3,  
    int y3);

 
BOOL RoundRect(
    LPCRECT lpRect,
    POINT point);
```  
  
### <a name="parameters"></a>参数  
 `x1`  
 指定 （使用逻辑单位） 的矩形的左上角的 x 坐标。  
  
 `y1`  
 指定 （使用逻辑单位） 的矩形的左上角的 y 坐标。  
  
 `x2`  
 指定的矩形 （使用逻辑单位） 的右下角的 x 坐标。  
  
 `y2`  
 指定的矩形 （使用逻辑单位） 的右下角的 y 坐标。  
  
 *x3*  
 指定用于绘制圆的角 （以逻辑单位） 的椭圆的宽度。  
  
 `y3`  
 指定用于绘制圆的角 （以逻辑单位） 的椭圆的高度。  
  
 `lpRect`  
 使用逻辑单位指定的绑定矩形。 您可以传递`CRect`对象或指向的指针`RECT`结构为此参数。  
  
 `point`  
 X 坐标`point`指定要绘制圆的角 （以逻辑单位） 的椭圆的宽度。 Y 坐标`point`指定要绘制圆的角 （以逻辑单位） 的椭圆的高度。 您可以传递**点**结构或`CPoint`为此参数的对象。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 使用当前画笔填充的矩形的内部。  
  
 此函数绘制的图最多扩展，但不包括右边和底边坐标。 这意味着该图的高度是`y2`–`y1`和图形的宽度是`x2`– `x1`。 高度和边框宽度必须大于 2 个单位和小于 32767 个单位。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&40;](../../mfc/codesnippet/cpp/cdc-class_12.cpp)]  
  
##  <a name="a-namesavedca--cdcsavedc"></a><a name="savedc"></a>CDC::SaveDC  
 将通过复制状态信息 （如剪辑区域、 所选的对象和映射模式） 的设备上下文的当前状态保存到上下文堆栈由 Windows 维护中。  
  
```  
virtual int SaveDC();
```  
  
### <a name="return-value"></a>返回值  
 一个整数，它标识的已保存的设备上下文。 如果发生错误，则为 0。 该返回值可以用于还原的设备上下文调用`RestoreDC`。  
  
### <a name="remarks"></a>备注  
 更高版本可以通过使用还原的已保存的设备上下文`RestoreDC`。  
  
 `SaveDC`可以是任意次数的用于保存任意数量的设备上下文状态。  
  
##  <a name="a-namescaleviewportexta--cdcscaleviewportext"></a><a name="scaleviewportext"></a>CDC::ScaleViewportExt  
 修改视区范围相对于当前值。  
  
```  
virtual CSize ScaleViewportExt(
    int xNum,  
    int xDenom,  
    int yNum,  
    int yDenom);
```  
  
### <a name="parameters"></a>参数  
 `xNum`  
 指定用来乘当前 x 范围内的量。  
  
 `xDenom`  
 指定被除数的值相乘当前 x 范围内的结果量`xNum`参数。  
  
 `yNum`  
 指定用来乘当前 y-区量。  
  
 `yDenom`  
 指定被除数的值相乘当前 y-区的结果量`yNum`参数。  
  
### <a name="return-value"></a>返回值  
 上一个视区范围 （以设备为单位） 为`CSize`对象。  
  
### <a name="remarks"></a>备注  
 公式是编写，如下所示︰  
  
 `xNewVE = ( xOldVE * xNum ) / xDenom`  
  
 `yNewVE = ( yOldVE * yNum ) / yDenom`  
  
 新的视区范围被计算当前的扩展盘区乘以给定分子，然后除以给定分母的。  
  
##  <a name="a-namescalewindowexta--cdcscalewindowext"></a><a name="scalewindowext"></a>CDC::ScaleWindowExt  
 修改范围相对于当前值，该窗口。  
  
```  
virtual CSize ScaleWindowExt(
    int xNum,  
    int xDenom,  
    int yNum,  
    int yDenom);
```  
  
### <a name="parameters"></a>参数  
 `xNum`  
 指定用来乘当前 x 范围内的量。  
  
 `xDenom`  
 指定被除数的值相乘当前 x 范围内的结果量`xNum`参数。  
  
 `yNum`  
 指定用来乘当前 y-区量。  
  
 `yDenom`  
 指定被除数的值相乘当前 y-区的结果量`yNum`参数。  
  
### <a name="return-value"></a>返回值  
 上一个窗口的扩展盘区 （使用逻辑单位） 为`CSize`对象。  
  
### <a name="remarks"></a>备注  
 公式是编写，如下所示︰  
  
 `xNewWE = ( xOldWE * xNum ) / xDenom`  
  
 `yNewWE = ( yOldWE * yNum ) / yDenom`  
  
 当前的扩展盘区乘以给定分子，然后除以给定分母来计算新的窗口范围。  
  
##  <a name="a-namescrolldca--cdcscrolldc"></a><a name="scrolldc"></a>CDC::ScrollDC  
 水平和垂直滚动的矩形的位数。  
  
```  
BOOL ScrollDC(
    int dx,  
    int dy,  
    LPCRECT lpRectScroll,  
    LPCRECT lpRectClip,  
    CRgn* pRgnUpdate,  
    LPRECT lpRectUpdate);
```  
  
### <a name="parameters"></a>参数  
 `dx`  
 指定水平滚动单元的数。  
  
 *dy*  
 指定垂直滚动单位数。  
  
 `lpRectScroll`  
 指向`RECT`结构或`CRect`对象，它包含滚动矩形的坐标。  
  
 `lpRectClip`  
 指向`RECT`结构或`CRect`对象，其中包含的剪辑矩形的坐标。 当此矩形小于一个指向的原始`lpRectScroll`，仅在较小的矩形中会发生滚动。  
  
 `pRgnUpdate`  
 标识由滚动过程发现的区域。 `ScrollDC`函数定义该区域; 它不一定是一个矩形。  
  
 `lpRectUpdate`  
 指向`RECT`结构或`CRect`接收限定滚动更新区域的矩形的坐标的对象。 这是需要重新绘制的最大矩形区域。 在结构或对象时该函数将返回的值是在客户端坐标中，而不考虑给定的设备上下文映射模式。  
  
### <a name="return-value"></a>返回值  
 非零，如果在执行滚动;否则为 0。  
  
### <a name="remarks"></a>备注  
 如果`lpRectUpdate`是**NULL**，Windows 不会计算更新矩形。 如果两个`pRgnUpdate`和`lpRectUpdate`是**NULL**，Windows 不会计算的更新区域。 如果`pRgnUpdate`不是**NULL**，Windows 会假定它包含指向滚动进程由发现的区域的有效指针 (由定义`ScrollDC`成员函数)。 更新区域中返回`lpRectUpdate`可以传递给`CWnd::InvalidateRgn`必要。  
  
 应用程序应使用`ScrollWindow`类的成员函数`CWnd`必要滚动窗口的整个客户端区域时。 否则，它应使用`ScrollDC`。  
  
##  <a name="a-nameselectclippatha--cdcselectclippath"></a><a name="selectclippath"></a>CDC::SelectClipPath  
 选择作为设备上下文中，使用指定的模式来组合具有任何现有的剪辑区域的新区域的剪辑区域的当前路径。  
  
```  
BOOL SelectClipPath(int nMode);
```  
  
### <a name="parameters"></a>参数  
 `nMode`  
 指定要使用的路径的方式。 可以为下列值︰  
  
- **RGN_AND**的新的剪辑区域包含为当前剪辑区域与当前的路径 （重叠区域） 的交集。  
  
- **RGN_COPY**的新的剪辑区域为当前路径。  
  
- **RGN_DIFF**的新的剪辑区域包括为当前剪辑区域，区域以及那些当前路径中排除。  
  
- **RGN_OR**新剪辑区域中包括的为当前剪辑区域与当前路径的并集 （组合区域）。  
  
- **RGN_XOR**联合的当前剪辑区域和当前的路径，但并没有重叠区域中的新的剪辑区域。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 标识的设备上下文必须包含封闭的路径。  
  
##  <a name="a-nameselectcliprgna--cdcselectcliprgn"></a><a name="selectcliprgn"></a>CDC::SelectClipRgn  
 选择给定的区域作为设备上下文的当前剪辑区域。  
  
```  
int SelectClipRgn(CRgn* pRgn);

 
int SelectClipRgn(
    CRgn* pRgn,  
    int nMode);
```  
  
### <a name="parameters"></a>参数  
 `pRgn`  
 标识要选择的区域。  
  
-   此函数中，如果此值的第一个版本**NULL**、 整个客户端区域处于选中状态和输出仍剪辑到窗口。  
  
-   有关此函数的第二个版本，可以是此句柄**NULL**仅当**RGN_COPY**指定模式。  
  
 `nMode`  
 指定要执行的操作。 它必须是下列值之一︰  
  
- **RGN_AND**的新的剪辑区域将组合为当前剪辑区域和区域由标识的重叠区域`pRgn`。  
  
- **RGN_COPY**的新的剪辑区域是由标识该区域的副本`pRgn`。 这是功能等同的第一个版本于`SelectClipRgn`。 如果该区域由`pRgn`是**NULL**，新的剪辑区域变得默认剪辑区域 （null 区域）。  
  
- **RGN_DIFF**的新的剪辑区域将组合为当前剪辑区域与从由标识区域中排除的那些区域的区域`pRgn`。  
  
- **RGN_OR**的新的剪辑区域将组合为当前剪辑区域和区域由标识`pRgn`。  
  
- **RGN_XOR**的新的剪辑区域将组合为当前剪辑区域和区域由标识`pRgn`但不包括任何重叠区域。  
  
### <a name="return-value"></a>返回值  
 区域的类型。 它可以是任何以下值︰  
  
- **COMPLEXREGION**新剪辑区域有重叠的边框。  
  
- **错误**设备上下文或地区无效。  
  
- **NULLREGION**新剪辑区域为空。  
  
- **SIMPLEREGION**新剪辑区域具有不重叠的边框。  
  
### <a name="remarks"></a>备注  
 使用仅选定的区域的副本。 可以为任意数量的其他设备上下文中，选择该区域本身或可在其后删除。  
  
 该函数假定给定区域的坐标以设备为单位指定。 某些打印机设备支持以保留 express 文本规格所需的精度比图形输出以高分辨率的文本输出。 这些设备报告的更高分辨率的设备单位，即文本单位。 然后，这些设备缩放图形的坐标，以便多个报告设备单元映射到只有 1 个图形单位。 应始终调用`SelectClipRgn`函数使用文本单位。  
  
 必须采取的缩放的图形对象的 GDI 中的应用程序可以使用**GETSCALINGFACTOR**打印机转义符，以确定缩放系数。 这个缩放比例影响剪辑。 如果某一区域使用剪辑图形，GDI 将坐标除以比例因子。 如果该区域用于剪切文本，GDI 会做任何缩放调整。 缩放因子为 1 会导致坐标除以 2;扩展因子为 2 会导致坐标除以 4;等等。  
  
##  <a name="a-nameselectobjecta--cdcselectobject"></a><a name="selectobject"></a>CDC::SelectObject  
 选择到设备上下文对象。  
  
```  
CPen* SelectObject(CPen* pPen);  
CBrush* SelectObject(CBrush* pBrush);  
virtual CFont* SelectObject(CFont* pFont);  
CBitmap* SelectObject(CBitmap* pBitmap);  
int SelectObject(CRgn* pRgn);  
CGdiObject* SelectObject(CGdiObject* pObject);
```  
  
### <a name="parameters"></a>参数  
 *pPen*  
 一个指向[CPen](../../mfc/reference/cpen-class.md)要选择的对象。  
  
 `pBrush`  
 一个指向[CBrush](../../mfc/reference/cbrush-class.md)要选择的对象。  
  
 `pFont`  
 一个指向[CFont](../../mfc/reference/cfont-class.md)要选择的对象。  
  
 `pBitmap`  
 一个指向[CBitmap](../../mfc/reference/cbitmap-class.md)要选择的对象。  
  
 `pRgn`  
 一个指向[CRgn](../../mfc/reference/crgn-class.md)要选择的对象。  
  
 `pObject`  
 一个指向[CGdiObject](../../mfc/reference/cgdiobject-class.md)要选择的对象。  
  
### <a name="return-value"></a>返回值  
 指向要替换的对象的指针。 这是指向派生自的类之一的对象的指针`CGdiObject`，如`CPen`，取决于使用哪一版本的函数。 返回值是**NULL**是否存在错误。 此函数可返回一个指针，到临时对象。 在一个 Windows 消息处理过程，该临时对象才有效。 有关详细信息，请参阅`CGdiObject::FromHandle`。  
  
 使用区域参数的成员函数的版本执行相同的任务作为`SelectClipRgn`成员函数。 它的返回值可以是以下任一情况︰  
  
- **COMPLEXREGION**新剪辑区域有重叠的边框。  
  
- **错误**设备上下文或地区无效。  
  
- **NULLREGION**新剪辑区域为空。  
  
- **SIMPLEREGION**新剪辑区域具有不重叠的边框。  
  
### <a name="remarks"></a>备注  
 类`CDC`提供了五个版本专用于特定种类的 GDI 对象，其中包括钢笔、 画笔、 字体、 位图和区域。 新选定的对象将替换上一个相同类型的对象。 例如，如果`pObject`的常见形式的`SelectObject`指向[CPen](../../mfc/reference/cpen-class.md)对象，该函数用指定的笔替换当前笔`pObject`。  
  
 应用程序可以选择一个位图到内存设备上下文仅和到只有一个内存设备上下文中一次。 位图的格式必须是单色或兼容的设备上下文;如果未列出，`SelectObject`返回错误。  
  
 对于 Windows 3.1 和更高版本，`SelectObject`函数是否使用了它在图元文件中不返回相同的值。 在以前版本的 Windows，`SelectObject`时在图元文件中将其用于返回一个非零值表示成功，0 表示失败。  
  
##  <a name="a-nameselectpalettea--cdcselectpalette"></a><a name="selectpalette"></a>CDC::SelectPalette  
 选择由指定的逻辑调色板`pPalette`作为设备上下文的所选的调色板对象。  
  
```  
CPalette* SelectPalette(
    CPalette* pPalette,  
    BOOL bForceBackground);
```  
  
### <a name="parameters"></a>参数  
 `pPalette`  
 标识要选择的逻辑调色板。 该调色板必须已经与创建`CPalette`成员函数[CreatePalette](../../mfc/reference/cpalette-class.md#createpalette)。  
  
 `bForceBackground`  
 指定是否强制逻辑调色板是背景调色板。 如果`bForceBackground`为非零值，并选择的调色板总是背景调色板，而不考虑窗口是否具有输入的焦点。 如果`bForceBackground`为 0 和设备上下文附加到窗口，则逻辑调色板窗口具有输入的焦点时前景调色板。  
  
### <a name="return-value"></a>返回值  
 一个指向`CPalette`标识逻辑替换为指定的调色板的调色板的对象的`pPalette`。 它是**NULL**是否存在错误。  
  
### <a name="remarks"></a>备注  
 新的调色板将成为用于通过 GDI 中的设备上下文显示控制颜色的调色板对象，并替换以前的调色板。  
  
 应用程序可以选择逻辑调色板到多个设备上下文。 但是，对逻辑调色板的更改会影响为其选择的所有设备上下文。 如果应用程序选择调色板到多个设备上下文中，设备上下文必须都属于同一个物理设备。  
  
##  <a name="a-nameselectstockobjecta--cdcselectstockobject"></a><a name="selectstockobject"></a>CDC::SelectStockObject  
 选择[CGdiObject](../../mfc/reference/cgdiobject-class.md)值对应于一个预定义的股票钢笔、 画笔或字体的对象。  
  
```  
virtual CGdiObject* SelectStockObject(int nIndex);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 指定所需的常用对象的类型。 它可以是下列值之一︰  
  
- **BLACK_BRUSH**黑色画笔。  
  
- **DKGRAY_BRUSH**暗灰色的画笔。  
  
- **GRAY_BRUSH** Gray 画笔。  
  
- **HOLLOW_BRUSH**空心画笔。  
  
- **LTGRAY_BRUSH**浅灰色的画笔。  
  
- **NULL_BRUSH**画笔，则为 Null。  
  
- **WHITE_BRUSH**白色画笔。  
  
- **BLACK_PEN**黑色钢笔。  
  
- **NULL_PEN** Null 笔。  
  
- **WHITE_PEN**白色画笔。  
  
- **ANSI_FIXED_FONT** ANSI 固定的系统字体。  
  
- **ANSI_VAR_FONT** ANSI 变量系统字体。  
  
- **DEVICE_DEFAULT_FONT**依赖于设备的字体。  
  
- **OEM_FIXED_FONT** OEM 依赖于固定字体。  
  
- **SYSTEM_FONT**系统字体。 默认情况下，Windows 使用系统字体绘制菜单、 对话框控件和其他文本。 它是最好的但是，不依赖于 SYSTEM_FONT 以获取使用对话框和窗口的字体。 请改用`SystemParametersInfo`SPI_GETNONCLIENTMETRICS 参数来检索当前字体函数。 `SystemParametersInfo`考虑到当前主题，并提供的标题、 菜单和消息对话框字体信息。  
  
- **SYSTEM_FIXED_FONT**版本 3.0 之前在 Windows 中使用的固定宽度系统字体。 此对象是可用于与 Windows 的早期版本的兼容性。  
  
- **DEFAULT_PALETTE**默认调色板。 该调色板包含系统调色板中的 20 静态颜色。  
  
### <a name="return-value"></a>返回值  
 一个指向`CGdiObject`如果函数运行成功被替换的对象。 指向了实际对象是[CPen](../../mfc/reference/cpen-class.md)， [CBrush](../../mfc/reference/cbrush-class.md)，或[CFont](../../mfc/reference/cfont-class.md)对象。 如果调用不会成功，返回值是**NULL**。  
  
##  <a name="a-namesetabortproca--cdcsetabortproc"></a><a name="setabortproc"></a>Cdc:: setabortproc  
 安装打印作业的中止过程。  
  
```  
int SetAbortProc(BOOL (CALLBACK* lpfn)(HDC, int));
```  
  
### <a name="parameters"></a>参数  
 `lpfn`  
 指向要将安装为中止过程的中止函数的指针。 有关详细信息的回调函数，请参阅[cdc:: setabortproc 的回调函数](../../mfc/reference/callback-function-for-cdc-setabortproc.md)。  
  
### <a name="return-value"></a>返回值  
 指定结果的`SetAbortProc`函数。 以下值一些比其他，更有可能发生，但所有都是可行。  
  
- **SP_ERROR**时出现常规错误。  
  
- **SP_OUTOFDISK**用于后台打印，目前没有足够的磁盘空间并无更多空间将变为可用。  
  
- **SP_OUTOFMEMORY**没有足够的内存可用于后台打印。  
  
- **SP_USERABORT**用户结束通过打印管理器作业。  
  
### <a name="remarks"></a>备注  
 如果应用程序，以允许在后台处理过程中取消打印作业打印作业启动与之前，它必须设置中止函数[StartDoc](#startdoc)成员函数。 打印管理器在后台处理，以允许应用程序能够取消该打印作业或处理的磁盘空间不足条件调用终止函数。 如果设置中止函数，打印作业将失败，如果没有足够的磁盘空间用于后台打印。  
  
 请注意 Microsoft Visual c + + 的功能简化传递给回调函数的创建`SetAbortProc`。 地址传递给`EnumObjects`成员函数是指向与导出的函数的指针**__declspec （dllexport)**和`__stdcall`调用约定。  
  
 您还不需要导出中的函数名称**导出**应用程序的模块定义文件中的语句。 你可以改用**导出**函数修饰符，如下所示  
  
 **BOOL 回调导出**AFunction ( **HDC**， `int` **);**  
  
 若要使编译器将发出导出的正确导出记录由不带别名名称。 这适用于大多数需求。 对于某些特殊的情况下，例如导出函数的序号比较还是别名导出，仍需要使用**导出**模块定义文件中的语句。  
  
 回调注册接口现在是类型安全的 （必须传递一个指向正确类型的特定的回调函数的函数指针）。  
  
 另请注意所有的回调函数必须捕获返回到 Windows 帐户，因为不能跨回调边界引发异常之前的 Microsoft 基础异常。 关于异常的详细信息，请参阅文章[异常](../../mfc/exception-handling-in-mfc.md)。  
  
##  <a name="a-namesetarcdirectiona--cdcsetarcdirection"></a><a name="setarcdirection"></a>CDC::SetArcDirection  
 绘制将方向设置为用于弧线和矩形功能。  
  
```  
int SetArcDirection(int nArcDirection);
```  
  
### <a name="parameters"></a>参数  
 *nArcDirection*  
 指定新的反方向。 此参数可以是下列值之一︰  
  
- **AD_COUNTERCLOCKWISE**按逆时针方向绘制的图形。  
  
- **AD_CLOCKWISE**沿顺时针方向绘制的图形。  
  
### <a name="return-value"></a>返回值  
 如果成功，则，指定的旧的弧线方向，否则为 0。  
  
### <a name="remarks"></a>备注  
 默认方向是逆时针旋转。 `SetArcDirection`函数指定以下顺序函数绘图的方向︰  
  
|Arc|饼图|  
|---------|---------|  
|`ArcTo`|**矩形**|  
|`Chord`|`RoundRect`|  
|**椭圆**||  
  
##  <a name="a-namesetattribdca--cdcsetattribdc"></a><a name="setattribdc"></a>CDC::SetAttribDC  
 调用此函数可设置属性设备上下文中， `m_hAttribDC`。  
  
```  
virtual void SetAttribDC(HDC hDC);
```  
  
### <a name="parameters"></a>参数  
 `hDC`  
 Windows 设备上下文。  
  
### <a name="remarks"></a>备注  
 此成员函数不会附加到的设备上下文`CDC`对象。 只输出设备上下文附加到`CDC`对象。  
  
##  <a name="a-namesetbkcolora--cdcsetbkcolor"></a><a name="setbkcolor"></a>CDC::SetBkColor  
 将当前的背景色设置为指定的颜色。  
  
```  
virtual COLORREF SetBkColor(COLORREF crColor);
```  
  
### <a name="parameters"></a>参数  
 `crColor`  
 指定新的背景色。  
  
### <a name="return-value"></a>返回值  
 以前的背景色为 RGB 颜色值。 如果发生错误，则返回值是 0x80000000。  
  
### <a name="remarks"></a>备注  
 如果后台模式是**不透明**，则系统使用的背景色来填充样式的行中的间隙，阴影的画笔中行和在字符单元格的背景之间的间隙。 将位图颜色和单色设备上下文之间转换时，系统也使用背景色。  
  
 如果设备无法显示指定的颜色时，系统会将背景色设置为最接近的物理颜色。  
  
##  <a name="a-namesetbkmodea--cdcsetbkmode"></a><a name="setbkmode"></a>CDC::SetBkMode  
 将后台模式设置。  
  
```  
int SetBkMode(int nBkMode);
```  
  
### <a name="parameters"></a>参数  
 *nBkMode*  
 指定要设置的模式。 此参数可以是下列值之一︰  
  
- **不透明**背景填充当前的背景色之前的文本，阴影画笔, 或笔绘制。 这是默认背景模式。  
  
- **透明**背景在绘制之前未发生更改。  
  
### <a name="return-value"></a>返回值  
 以前的背景模式。  
  
### <a name="remarks"></a>备注  
 后台模式定义系统是否绘制文本、 阴影的画笔或笔样式，不是一条实线之前删除现有的背景颜色绘图图面上。  
  
### <a name="example"></a>示例  
  请参阅示例[CWnd::OnCtlColor](../../mfc/reference/cwnd-class.md#onctlcolor)。  
  
##  <a name="a-namesetboundsrecta--cdcsetboundsrect"></a><a name="setboundsrect"></a>CDC::SetBoundsRect  
 控制边界矩形指定的设备上下文的信息的累计。  
  
```  
UINT SetBoundsRect(
    LPCRECT lpRectBounds,  
    UINT flags);
```  
  
### <a name="parameters"></a>参数  
 `lpRectBounds`  
 指向`RECT`结构或`CRect`对象用于设置的边框。 矩形尺寸的单位以逻辑坐标表示。 此参数可以为**NULL**。  
  
 `flags`  
 指定如何新添加的矩形将合并在一起的累计的矩形。 此参数可以是以下值的组合︰  
  
- **DCB_ACCUMULATE**添加指定的矩形`lpRectBounds`到边框 （使用矩形联合操作）。  
  
- **DCB_DISABLE**关闭边界累积。  
  
- **DCB_ENABLE**开启边界累积。 （边界累积的默认设置为禁用）。  
  
### <a name="return-value"></a>返回值  
 如果函数运行成功的绑定矩形当前状态。 如`flags`，则返回值可以是组合的**DCB_**值︰  
  
- **DCB_ACCUMULATE**的边框不为空。 此值将始终设置。  
  
- **DCB_DISABLE**边界累积处于关闭状态。  
  
- **DCB_ENABLE**边界累积亮起。  
  
### <a name="remarks"></a>备注  
 Windows 可以维护所有绘图操作的绑定矩形。 可以查询此矩形，并将其重置应用程序。 绘制边界可用于使位图缓存失效。  
  
##  <a name="a-namesetbrushorga--cdcsetbrushorg"></a><a name="setbrushorg"></a>CDC::SetBrushOrg  
 指定的 GDI 会将分配给该应用程序将选择到设备上下文的下一步画笔的原点。  
  
```  
CPoint SetBrushOrg(
    int x,  
    int y);  
  
CPoint SetBrushOrg(POINT point);
```  
  
### <a name="parameters"></a>参数  
 *x*  
 指定的 x 坐标 （以设备为单位） 的新的原点。 此值必须在范围 0 – 7。  
  
 *y*  
 指定的 y 坐标 （以设备为单位） 的新的原点。 此值必须在范围 0 – 7。  
  
 `point`  
 指定新的原点 x 和 y 坐标。 每个值必须在范围 0 – 7。 您可以传递**点**结构或`CPoint`为此参数的对象。  
  
### <a name="return-value"></a>返回值  
 以前设备单位画笔的原点。  
  
### <a name="remarks"></a>备注  
 默认值的画笔的原点的坐标为 （0，0）。 若要更改画笔的原点，调用`UnrealizeObject`函数`CBrush`对象，请调用`SetBrushOrg`，然后调用`SelectObject`成员函数以在设备上下文中选择的画笔。  
  
 请不要使用`SetBrushOrg`与库存`CBrush`对象。  
  
##  <a name="a-namesetcoloradjustmenta--cdcsetcoloradjustment"></a><a name="setcoloradjustment"></a>CDC::SetColorAdjustment  
 设置使用指定的值的设备上下文的颜色调整值。  
  
```  
BOOL SetColorAdjustment(const COLORADJUSTMENT* lpColorAdjust);
```  
  
### <a name="parameters"></a>参数  
 `lpColorAdjust`  
 指向[COLORADJUSTMENT](../../mfc/reference/coloradjustment-structure.md)数据结构，它包含颜色调整值。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 颜色调整值被用来调整对调用的源位图的输入的颜色`CDC::StretchBlt`成员函数时**半色调**模式设置。  
  
##  <a name="a-namesetdcbrushcolora--cdcsetdcbrushcolor"></a><a name="setdcbrushcolor"></a>CDC::SetDCBrushColor  
 将当前设备上下文 (DC) 画笔的颜色设置为指定的颜色值。  
  
```  
COLORREF SetDCBrushColor(COLORREF crColor);
```  
  
### <a name="parameters"></a>参数  
 `crColor`  
 指定新的画笔颜色。  
  
### <a name="return-value"></a>返回值  
 如果函数成功，则返回值指定为以前的 DC 画笔颜色`COLORREF`值。  
  
 如果函数失败，返回值是`CLR_INVALID`。  
  
### <a name="remarks"></a>备注  
 此方法模拟该函数的功能[SetDCBrushColor](http://msdn.microsoft.com/library/windows/desktop/dd162969)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namesetdcpencolora--cdcsetdcpencolor"></a><a name="setdcpencolor"></a>CDC::SetDCPenColor  
 将当前的设备上下文 (DC) 钢笔颜色设置为指定的颜色值。  
  
```  
COLORREF SetDCPenColor(COLORREF crColor);
```  
  
### <a name="parameters"></a>参数  
 `crColor`  
 指定新的钢笔颜色。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 此成员函数使用 Win32 函数[SetDCPenColor](http://msdn.microsoft.com/library/windows/desktop/dd162970)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namesetgraphicsmodea--cdcsetgraphicsmode"></a><a name="setgraphicsmode"></a>CDC::SetGraphicsMode  
 设置指定的设备上下文的图形模式。  
  
```  
int SetGraphicsMode(int iMode);
```  
  
### <a name="parameters"></a>参数  
 `iMode`  
 指定的图形模式。 此参数可以采用的值的列表，请参阅[SetGraphicsMode](http://msdn.microsoft.com/library/windows/desktop/dd162977)。  
  
### <a name="return-value"></a>返回值  
 如果成功返回旧图形模式。  
  
 失败时返回 0。 若要获得扩展错误信息，请调用[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)。  
  
### <a name="remarks"></a>备注  
 此方法将包装 Windows GDI 函数[SetGraphicsMode](http://msdn.microsoft.com/library/windows/desktop/dd162977)。  
  
##  <a name="a-namesetlayouta--cdcsetlayout"></a><a name="setlayout"></a>CDC::SetLayout  
 调用该成员函数以将文本和图形设备上下文的布局更改为从右向左的区域性，如阿拉伯语和希伯来语的标准布局。  
  
```  
DWORD SetLayout(DWORD dwLayout);
```  
  
### <a name="parameters"></a>参数  
 `dwLayout`  
 设备上下文布局和位图控制标志。 它可以是以下值的组合。  
  
|值|含义|  
|-----------|-------------|  
|LAYOUT_BITMAPORIENTATIONPRESERVED|禁用对调用任何反射[CDC::BitBlt](#bitblt)和[CDC::StretchBlt](#stretchblt)。|  
|LAYOUT_RTL|设置默认水平布局是从右到左。|  
|LAYOUT_LTR|设置默认布局，以从左到右。|  
  
### <a name="return-value"></a>返回值  
 如果成功，以前的设备上下文的布局。  
  
 如果不成功， **GDI_ERROR**。 若要获得扩展错误信息，请调用[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)。  
  
### <a name="remarks"></a>备注  
 通常情况下，不会调用**SetLayout**窗口。 相反，通过设置控制在窗口中的从右到左布局[扩展窗口样式](../../mfc/reference/extended-window-styles.md)如**WS_EX_RTLREADING**。 设备上下文，如打印机或图元文件，不会继承该布局中。 为从右到左布局是通过调用设置的设备上下文的唯一办法**SetLayout**。  
  
 如果调用**SetLayout (LAYOUT_RTL** )， **SetLayout**会自动更改到的映射模式`MM_ISOTROPIC`。 因此，后续调用[GetMapMode](#getmapmode)将返回**MM_ISOTROPIC**而不是`MM_TEXT`。  
  
 在某些情况下，如使用许多位图，您可能想要保留从左到右布局。 在这些情况下，通过调用呈现图像`BitBlt`或`StretchBlt`，然后将设置为位图的控件标记`dwLayout`到**LAYOUT_BITMAPORIENTATIONPRESERVED**。  
  
 一旦您更改与布局**LAYOUT_RTL**标记通常指定权限的标志或左进行了互换。 为避免混淆，可能想要定义标准的标志的替代名称。 建议的替代标志名称的列表，请参阅[SetLayout](http://msdn.microsoft.com/library/windows/desktop/dd162979)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namesetmapmodea--cdcsetmapmode"></a><a name="setmapmode"></a>CDC::SetMapMode  
 设置的映射模式。  
  
```  
virtual int SetMapMode(int nMapMode);
```  
  
### <a name="parameters"></a>参数  
 `nMapMode`  
 指定新的映射模式。 它可以是下列值之一︰  
  
- `MM_ANISOTROPIC`与任意缩放轴，逻辑单元将转换为任意单位。 映射模式设置为`MM_ANISOTROPIC`不会更改当前的窗口或视区设置。 若要更改的单位，方向和缩放，调用[SetWindowExt](#setwindowext)和[SetViewportExt](#setviewportext)成员函数。  
  
- `MM_HIENGLISH`每个逻辑单元将转换为 0.001 英寸。 正 x 是向右;正 y 是最多。  
  
- `MM_HIMETRIC`每个逻辑单元会转换为 0.01 毫米。 正 x 是向右;正 y 是最多。  
  
- `MM_ISOTROPIC`逻辑单元将转换为任意单位与同样缩放轴;也就是说，沿 x 轴 1 个单位相当于 1 个单位沿 y 轴。 使用`SetWindowExt`和`SetViewportExt`成员函数以指定所需的单位和轴的方向。 GDI，可以根据需要进行调整以确保 x 和 y 单元保持同样的大小。  
  
- `MM_LOENGLISH`每个逻辑单元会转换为 0.01 英寸。 正 x 是向右;正 y 是最多。  
  
- `MM_LOMETRIC`每个逻辑单元会转换为 0.1 毫米。 正 x 是向右;正 y 是最多。  
  
- `MM_TEXT`每个逻辑单元将转换为 1 台设备像素。 正 x 是向右;正 y 已关闭。  
  
- `MM_TWIPS`每个逻辑单元会转换为 1/20 的点。 （由于点 1/72 英寸，缇是 1/1440年英寸）。正 x 是向右;正 y 是最多。  
  
### <a name="return-value"></a>返回值  
 以前的映射模式。  
  
### <a name="remarks"></a>备注  
 映射模式定义用于将逻辑单元转换为设备单位; 的度量的单位它还定义了设备的 x 轴和 y 轴的方向。 GDI 使用映射模式将逻辑坐标转换为适当的设备坐标。 `MM_TEXT`模式允许应用程序能够以设备像素为单位，其中 1 个单位是等于 1 个像素。 一个像素的物理大小各不相同设备到设备。  
  
 `MM_HIENGLISH`， `MM_HIMETRIC`， `MM_LOENGLISH`， `MM_LOMETRIC`，和`MM_TWIPS`模式非常有用的应用程序必须在物理上有意义的单元 （如英寸或毫米） 中进行绘制。 `MM_ISOTROPIC`模式可确保 1:1 纵横比，一定要记住的图像的确切形状时，这非常有用。 `MM_ANISOTROPIC`模式允许 x 坐标和 y 坐标来独立地进行调整。  
  
> [!NOTE]
>  如果调用[SetLayout](#setlayout) DC （设备上下文） 改为从右到左布局**SetLayout**会自动更改到的映射模式`MM_ISOTROPIC`。  
  
### <a name="example"></a>示例  
  请参阅示例[CView::OnPrepareDC](../../mfc/reference/cview-class.md#onpreparedc)。  
  
##  <a name="a-namesetmapperflagsa--cdcsetmapperflags"></a><a name="setmapperflags"></a>CDC::SetMapperFlags  
 更改时它将转换为一个逻辑字体物理字体使用的字体映射程序的方法。  
  
```  
DWORD SetMapperFlags(DWORD dwFlag);
```  
  
### <a name="parameters"></a>参数  
 `dwFlag`  
 指定字体映射器尝试以与字体的方面高度和宽度与设备匹配。 当此值是**ASPECT_FILTERING**、 映射器中选择唯一字体其 x 方面和与指定的设备，y 方面完全相同。  
  
### <a name="return-value"></a>返回值  
 以前的字体映射器标志值。  
  
### <a name="remarks"></a>备注  
 应用程序可以使用`SetMapperFlags`若要使字体映射器尝试选择仅与指定的设备纵横比完全匹配的物理字体。  
  
 使用仅光栅字体的应用程序可以使用`SetMapperFlags`函数，以确保选定的字体映射器的字体已有吸引力，读取指定的设备上。 通常使用可扩展 (TrueType) 字体的应用程序不使用`SetMapperFlags`。  
  
 如果没有物理字体具有匹配的逻辑字体中的规范纵横比，GDI 选择新的长宽比，并选择一种字体匹配此新的长宽比。  
  
##  <a name="a-namesetmiterlimita--cdcsetmiterlimit"></a><a name="setmiterlimit"></a>CDC::SetMiterLimit  
 设置的设备上下文的斜接联接的长度的限制。  
  
```  
BOOL SetMiterLimit(float fMiterLimit);
```  
  
### <a name="parameters"></a>参数  
 *fMiterLimit*  
 指定设备上下文的新斜角限制。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 斜接长度被指从线壁在联接的内侧的交集的联接外侧行墙的交集的距离。 斜角限制是为线条宽度的斜接长度最大允许的比率。 默认斜角限制为 10.0。  
  
##  <a name="a-namesetoutputdca--cdcsetoutputdc"></a><a name="setoutputdc"></a>CDC::SetOutputDC  
 调用此成员函数来设置输出设备上下文中， `m_hDC`。  
  
```  
virtual void SetOutputDC(HDC hDC);
```  
  
### <a name="parameters"></a>参数  
 `hDC`  
 Windows 设备上下文。  
  
### <a name="remarks"></a>备注  
 设备上下文未附加到时，才可以调用该成员函数`CDC`对象。 此成员函数将设置`m_hDC`但不会附加到的设备上下文`CDC`对象。  
  
##  <a name="a-namesetpixela--cdcsetpixel"></a><a name="setpixel"></a>CDC::SetPixel  
 设置由指定的颜色最接近的近似到指定的点处的像素`crColor`。  
  
```  
COLORREF SetPixel(
    int x,  
    int y,  
    COLORREF crColor);

 
COLORREF SetPixel(
    POINT point,  
    COLORREF crColor);
```  
  
### <a name="parameters"></a>参数  
 *x*  
 指定要设置的点的逻辑 x 坐标。  
  
 *y*  
 指定要设置的点的逻辑 y 坐标。  
  
 `crColor`  
 一个**COLORREF** RGB 值，该值指定用来绘制点的颜色。 请参阅[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]有关此值的说明。  
  
 `point`  
 指定逻辑 x 坐标和 y 坐标的点来进行设置。 您可以传递**点**结构或`CPoint`为此参数的对象。  
  
### <a name="return-value"></a>返回值  
 实际绘制点的颜色 RGB 值。 此值可为不同于指定的`crColor`如果使用该颜色的近似值。 如果函数失败 （如果剪切区域外部的点），则返回值为 –&1;。  
  
### <a name="remarks"></a>备注  
 该点必须位于的剪辑区域。 如果该点不在的剪辑区域，该函数将没有任何影响。  
  
 不是所有的设备都支持 `SetPixel` 函数。 若要确定设备是否支持`SetPixel`，调用`GetDeviceCaps`成员函数时**RASTERCAPS**编制索引，并检查返回值**RC_BITBLT**标志。  
  
##  <a name="a-namesetpixelva--cdcsetpixelv"></a><a name="setpixelv"></a>CDC::SetPixelV  
 在指定坐标对指定的颜色最接近的近似设置像素。  
  
```  
BOOL SetPixelV(
    int x,  
    int y,  
    COLORREF crColor);

 
BOOL SetPixelV(
    POINT point,  
    COLORREF crColor);
```  
  
### <a name="parameters"></a>参数  
 *x*  
 使用逻辑单位，点要设置的指定 x 坐标。  
  
 *y*  
 指定使用逻辑单位，要设置的点的 y 轴坐标。  
  
 `crColor`  
 指定要用于绘制点的颜色。  
  
 `point`  
 指定逻辑 x 坐标和 y 坐标的点来进行设置。 您可以传递[点](../../mfc/reference/point-structure1.md)数据结构或[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)为此参数的对象。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 点必须在剪辑区域和设备表面的可见部分。 并非所有设备都支持的成员函数。 有关详细信息，请参阅**RC_BITBLT**中的功能`CDC::GetDeviceCaps`成员函数。 `SetPixelV`快于`SetPixel`因为它不需要返回实际绘制的点的颜色值。  
  
##  <a name="a-namesetpolyfillmodea--cdcsetpolyfillmode"></a><a name="setpolyfillmode"></a>CDC::SetPolyFillMode  
 将多边形的填充模式设置。  
  
```  
int SetPolyFillMode(int nPolyFillMode);
```  
  
### <a name="parameters"></a>参数  
 `nPolyFillMode`  
 指定新的填充模式。 此值可能**备用**或**缠绕**。 在 Windows 中设置的默认模式是**备用**。  
  
### <a name="return-value"></a>返回值  
 如果成功，则之前填充模式否则为 0。  
  
### <a name="remarks"></a>备注  
 多边形填充模式时**备用**，系统填充奇和偶数个多边形的边，每个扫描线上之间的区域。 也就是说，系统填充的区域之间的第一个和第二个一侧，之间的第三个和第四个端，依次类推。 这种模式是默认设置。  
  
 多边形填充模式时**缠绕**，系统将使用一个数字绘制来确定是否填充的区域的方向。 将以顺时针或逆时针方向绘制多边形内的每个直线线段。 每当从封闭区域到图的外部绘制的虚线通过顺时针方向的直线线段时，计数将递增。 当在行通过逆时针旋转直线线段时，计数会递减。 如果计数不为零的曲线到达图外部时，填充区域。  
  
##  <a name="a-namesetrop2a--cdcsetrop2"></a><a name="setrop2"></a>CDC::SetROP2  
 设置当前绘图模式。  
  
```  
int SetROP2(int nDrawMode);
```  
  
### <a name="parameters"></a>参数  
 `nDrawMode`  
 指定新的绘图模式。 它可以是任何以下值︰  
  
- **R2_BLACK**像素始终为黑色。  
  
- **R2_WHITE**像素始终为白色。  
  
- **R2_NOP**像素保持不变。  
  
- **R2_NOT**是屏幕颜色的反向操作像素。  
  
- **R2_COPYPEN**像素的钢笔颜色。  
  
- **R2_NOTCOPYPEN**是钢笔颜色的反向操作像素。  
  
- **R2_MERGEPENNOT**像素都是和屏幕颜色的逆的钢笔颜色组合 (最终像素 = （不屏幕像素） 或笔)。  
  
- **R2_MASKPENNOT**像素是屏幕的逆和普遍适用于笔的颜色的组合 (最终像素 = （不屏幕像素） 和笔)。  
  
- **R2_MERGENOTPEN**像素是钢笔颜色的逆和屏幕颜色的组合 (最终像素 = （不笔） 或屏幕像素)。  
  
- **R2_MASKNOTPEN**像素都是普遍适用于屏幕颜色组合和笔的反转 (最终像素 = （不笔） 和屏幕像素)。  
  
- **R2_MERGEPEN**像素的钢笔颜色和屏幕颜色的组合 (最终像素 = 笔或屏幕像素)。  
  
- **R2_NOTMERGEPEN**像素都是函数的反函数**R2_MERGEPEN**颜色 (最终像素 = 不 （笔或屏幕像素）)。  
  
- **R2_MASKPEN**像素都是通用的笔和屏幕颜色的组合 (最终像素 = 笔 AND 屏幕像素)。  
  
- **R2_NOTMASKPEN**像素都是函数的反函数**R2_MASKPEN**颜色 (最终像素 = 不 （笔 AND 屏幕像素）)。  
  
- **R2_XORPEN**像素是笔或在屏幕中，而不在两者的颜色的组合 (最终像素 = 笔异或屏幕像素)。  
  
- **R2_NOTXORPEN**像素都是函数的反函数**R2_XORPEN**颜色 (最终像素 = 不 （笔异或屏幕像素）)。  
  
### <a name="return-value"></a>返回值  
 以前的绘制模式。  
  
 它可以是任何中提供的值[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="remarks"></a>备注  
 绘图模式指定笔的颜色和实心对象的内部进行组合的方式与已在显示图面上的颜色。  
  
 绘图模式是仅适用于光栅设备;它不适用于向量设备。 绘图模式是表示所有可能的布尔组合两个变量，不使用二元运算符 AND、 OR 和 XOR （异或） 和一元运算的二进制光栅操作代码。  
  
##  <a name="a-namesetstretchbltmodea--cdcsetstretchbltmode"></a><a name="setstretchbltmode"></a>CDC::SetStretchBltMode  
 设置的位图拉伸模式`StretchBlt`成员函数。  
  
```  
int SetStretchBltMode(int nStretchMode);
```  
  
### <a name="parameters"></a>参数  
 *nStretchMode*  
 指定的拉伸模式。 它可以是任何以下值︰  
  
|值|说明|  
|-----------|-----------------|  
|**BLACKONWHITE**|执行布尔 AND 操作使用的已清除的和现有的像素的颜色值。 如果位图是单色位图，此模式会保留代价白色像素是黑色像素。|  
|**COLORONCOLOR**|删除像素。 在此模式下删除所有无的像素行数而不尝试保留他们的信息。|  
|**半色调**|将源矩形的像素映射到目标矩形中的像素的块。 通过目标块的像素为单位的平均颜色总数接近于源像素的颜色。|  
||在设置后**半色调**拉伸模式下，应用程序必须调用 Win32 函数[SetBrushOrgEx](http://msdn.microsoft.com/library/windows/desktop/dd162967)若要设置的画笔的原点。 如果无法这样做，则发生画笔不齐。|  
|**STRETCH_ANDSCANS**|**Windows 95/98**︰ 相同**BLACKONWHITE**|  
|**STRETCH_DELETESCANS**|**Windows 95/98**︰ 相同**COLORONCOLOR**|  
|**STRETCH_HALFTONE**|**Windows 95/98**︰ 相同**半色调**。|  
|**STRETCH_ORSCANS**|**Windows 95/98**︰ 相同**WHITEONBLACK**|  
|**WHITEONBLACK**|执行布尔值或操作使用的已清除的和现有的像素的颜色值。 如果位图是单色位图，此模式会保留对应的代价是黑色像素的白色像素。|  
  
### <a name="return-value"></a>返回值  
 以前的拉伸模式。 它可以是**STRETCH_ANDSCANS**， **STRETCH_DELETESCANS**，或**STRETCH_ORSCANS**。  
  
### <a name="remarks"></a>备注  
 位图拉伸模式定义如何从使用该函数来压缩的位图中删除信息。  
  
 **BLACKONWHITE** ( **STRETCH_ANDSCANS**) 和**WHITEONBLACK** ( **STRETCH_ORSCANS**) 模式通常用于保留单色位图中的前景色像素。 **COLORONCOLOR** ( **STRETCH_DELETESCANS**) 模式通常用于保留彩色位图中的颜色。  
  
 **半色调**模式需要更多的源映像比其他三种模式的处理的; 它要比其他慢但产生更高质量的图像。 另请注意， **SetBrushOrgEx**设置后，必须调用**半色调**模式，以避免画笔不齐。  
  
 其他的拉伸模式可能会有根据设备驱动程序的功能。  
  
##  <a name="a-namesettextaligna--cdcsettextalign"></a><a name="settextalign"></a>CDC::SetTextAlign  
 设置文本对齐方式的标志。  
  
```  
UINT SetTextAlign(UINT nFlags);
```  
  
### <a name="parameters"></a>参数  
 `nFlags`  
 指定文本对齐方式的标志。 这些标志指定一个点和限定文本的矩形之间的关系。 点可以是当前位置或按文本输出函数指定的坐标。 限定文本的矩形的相邻字符单元格中的文本字符串由定义。 `nFlags`参数可以是以下三个类别中的一个或多个标志。 选择每个类别中只有一个标志。 第一个类别将影响在 x 方向的文本对齐方式︰  
  
- **TA_CENTER**对齐边界矩形与水平中心的点。  
  
- **TA_LEFT**对齐边界矩形的左侧的点。 此为默认设置。  
  
- **TA_RIGHT**对齐边界矩形的右边的点。  
  
 第二个类别会影响在 y 方向的文本对齐方式︰  
  
- **TA_BASELINE**对齐基准线的所选字体的点。  
  
- **TA_BOTTOM**对齐边界矩形的底部的点。  
  
- **TA_TOP**将的点与边界的矩形的顶部对齐。 此为默认设置。  
  
 第三个类别确定写入文本时是否更新当前的位置︰  
  
- **TA_NOUPDATECP**不会在每次调用的文本输出函数后更新当前位置。 此为默认设置。  
  
- **TA_UPDATECP**后每次调用的文本输出函数将更新当前的 x 位置。 新的位置是边框的在文本的右侧。 如果设置此标志，对的调用中指定的坐标`TextOut`成员函数将被忽略。  
  
### <a name="return-value"></a>返回值  
 以前文本对齐方式的设置，如果操作成功。 低位字节包含水平设置和高位字节包含的垂直设置;否则为 0。  
  
### <a name="remarks"></a>备注  
 `TextOut`和`ExtTextOut`成员函数使用这些标志来定位的显示或设备上的文本字符串时。 这些标志指定的特定点和限定文本的矩形之间的关系。 此点的坐标作为参数传递给`TextOut`成员函数。 文本字符串中的相邻字符单元格的格式，则限定文本的矩形。  
  
##  <a name="a-namesettextcharacterextraa--cdcsettextcharacterextra"></a><a name="settextcharacterextra"></a>CDC::SetTextCharacterExtra  
 设置 intercharacter 间距的大小。  
  
```  
int SetTextCharacterExtra(int nCharExtra);
```  
  
### <a name="parameters"></a>参数  
 `nCharExtra`  
 指定 （使用逻辑单位） 的额外空间的量添加到每个字符。 如果不是当前的映射模式`MM_TEXT`，`nCharExtra`转换和舍入到最近的像素。  
  
### <a name="return-value"></a>返回值  
 以前的 intercharacter 间距大小。  
  
### <a name="remarks"></a>备注  
 GDI 将此空间添加到每个字符，包括向设备上下文中写入文本行中断符。 Intercharacter 间距量的默认值为 0。  
  
##  <a name="a-namesettextcolora--cdcsettextcolor"></a><a name="settextcolor"></a>CDC::SetTextColor  
 将文本颜色设置为指定的颜色。  
  
```  
virtual COLORREF SetTextColor(COLORREF crColor);
```  
  
### <a name="parameters"></a>参数  
 `crColor`  
 指定文本的颜色为 RGB 颜色值。  
  
### <a name="return-value"></a>返回值  
 以前的文本颜色 RGB 值。  
  
### <a name="remarks"></a>备注  
 将文本写入此设备上下文以及之间的转换位图的颜色和单色设备上下文时，系统将使用此文本颜色。  
  
 如果设备不能表示指定的颜色，系统会将文本颜色设置为最接近的物理颜色。 指定一个字符的背景色`SetBkColor`和`SetBkMode`成员函数。  
  
### <a name="example"></a>示例  
  请参阅示例[CWnd::OnCtlColor](../../mfc/reference/cwnd-class.md#onctlcolor)。  
  
##  <a name="a-namesettextjustificationa--cdcsettextjustification"></a><a name="settextjustification"></a>CDC::SetTextJustification  
 将空间添加到字符串中的中断字符。  
  
```  
int SetTextJustification(
    int nBreakExtra,  
    int nBreakCount);
```  
  
### <a name="parameters"></a>参数  
 `nBreakExtra`  
 指定要添加到的 （使用逻辑单位） 的文本行的总的额外空间。 如果不是当前的映射模式`MM_TEXT`，给定此参数的值转换为当前的映射模式，并舍入为最接近的设备单位。  
  
 *nBreakCount*  
 指定的行中的中断字符数。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则，一个否则为 0。  
  
### <a name="remarks"></a>备注  
 应用程序可以使用`GetTextMetrics`成员函数以检索字体的中断字符。  
  
 之后`SetTextJustification`调用成员函数时，对文本输出函数的调用 (如`TextOut`) 分布在指定数目的分页符字符之间平均指定额外的空间。 换行符字符通常是空格字符 (ASCII 32)，但可能按某些其他字符作为一种字体定义。  
  
 成员函数`GetTextExtent`通常用于`SetTextJustification`。 `GetTextExtent`计算对齐前一个给定行的宽度。 应用程序可以确定要在中指定的空间`nBreakExtra`通过返回的值中减去参数`GetTextExtent`对齐后的字符串的宽度。  
  
 `SetTextJustification`函数可以用于对齐一行，其中包含在不同的字体中的多个运行。 在这种情况下，行必须段落创建通过对齐并单独编写每次运行。  
  
 因为舍入误差可能会发生对齐方式，系统将保持一个正在运行的错误术语，它定义当前错误。 对齐一行，其中包含多个运行时`GetTextExtent`会自动使用该错误术语时，它将计算下一次运行的程度。 这允许要结合到新的运行的错误的文本输出函数。  
  
 对齐每一行后，必须清除该错误术语，以防止它合并到下一行。 可以通过调用清除术语`SetTextJustification`与`nBreakExtra`设置为 0。  
  
##  <a name="a-namesetviewportexta--cdcsetviewportext"></a><a name="setviewportext"></a>CDC::SetViewportExt  
 设置 x-和 y 的扩展盘区的设备上下文的视区。  
  
```  
virtual CSize SetViewportExt(
    int cx,  
    int cy);  
  
CSize SetViewportExt(SIZE size);
```  
  
### <a name="parameters"></a>参数  
 `cx`  
 指定 （以设备为单位） 的视区的 x 范围。  
  
 `cy`  
 指定 （以设备为单位） 的视区的 y 范围。  
  
 `size`  
 指定 x-和 y 的范围内的视区 （以设备为单位）。  
  
### <a name="return-value"></a>返回值  
 为视区的上一个扩展盘区[CSize](../../atl-mfc-shared/reference/csize-class.md)对象。 当错误发生时，x 坐标和 y 坐标则返回的`CSize`对象都设置为 0。  
  
### <a name="remarks"></a>备注  
 视区，设备上下文窗口中，以及定义 GDI 如何映射到实际设备的点的坐标系统中的逻辑坐标系统中的点。 换而言之，他们会定义 GDI 如何将逻辑坐标转换设备坐标。  
  
 下面的映射模式设置后，调用`SetWindowExt`和`SetViewportExt`将被忽略︰  
  
|MM_HIENGLISH|MM_LOMETRIC|  
|-------------------|------------------|  
|`MM_HIMETRIC`|`MM_TEXT`|  
|`MM_LOENGLISH`|`MM_TWIPS`|  
  
 当`MM_ISOTROPIC`模式设置，应用程序必须调用`SetWindowExt`成员函数调用之前`SetViewportExt`。  
  
### <a name="example"></a>示例  
  请参阅示例[CView::OnPrepareDC](../../mfc/reference/cview-class.md#onpreparedc)。  
  
##  <a name="a-namesetviewportorga--cdcsetviewportorg"></a><a name="setviewportorg"></a>CDC::SetViewportOrg  
 设置设备上下文的视区原点。  
  
```  
virtual CPoint SetViewportOrg(
    int x,  
    int y);  
  
CPoint SetViewportOrg(POINT point);
```  
  
### <a name="parameters"></a>参数  
 *x*  
 指定的 x 坐标 （以设备为单位） 的视区原点。 值必须在设备坐标系统的范围内。  
  
 *y*  
 指定的 y 坐标 （以设备为单位） 的视区原点。 值必须在设备坐标系统的范围内。  
  
 `point`  
 指定视区的来源。 值必须在设备坐标系统范围内。 您可以传递**点**结构或`CPoint`为此参数的对象。  
  
### <a name="return-value"></a>返回值  
 以前 （在设备坐标中） 作为的视区原点`CPoint`对象。  
  
### <a name="remarks"></a>备注  
 视区，设备上下文窗口中，以及定义 GDI 如何映射到实际设备的点的坐标系统中的逻辑坐标系统中的点。 换而言之，他们会定义 GDI 如何将逻辑坐标转换设备坐标。  
  
 视区原点标记在设备坐标系统 GDI 映射窗口原点，由指定的逻辑坐标系统中的点到点**SetWindowOrg**成员函数。 通过映射到视区原点的窗口原点需按照同一过程，GDI 映射所有其他点。 例如，在窗口原点的点为圆心中的所有点都将处于圆心在视区原点的点。 同样，通过窗口原点的行中的所有点都将通过视区原点的行中。  
  
### <a name="example"></a>示例  
  请参阅示例[CView::OnPrepareDC](../../mfc/reference/cview-class.md#onpreparedc)。  
  
##  <a name="a-namesetwindowexta--cdcsetwindowext"></a><a name="setwindowext"></a>CDC::SetWindowExt  
 设置 x-和 y 的扩展盘区的设备上下文与关联的窗口。  
  
```  
virtual CSize SetWindowExt(
    int cx,  
    int cy);  
  
CSize SetWindowExt(SIZE size);
```  
  
### <a name="parameters"></a>参数  
 `cx`  
 指定的 x 的范围 （以逻辑单位） 的窗口中。  
  
 `cy`  
 指定的 y 的范围 （以逻辑单位） 的窗口中。  
  
 `size`  
 指定 x-和 y 的 （使用逻辑单位） 窗口范围。  
  
### <a name="return-value"></a>返回值  
 （使用逻辑单位） 为窗口的上一个扩展盘区`CSize`对象。 如果发生错误，x 坐标和 y 坐标则返回的`CSize`对象都设置为 0。  
  
### <a name="remarks"></a>备注  
 窗口中的，设备上下文视区，以及定义 GDI 如何映射到设备坐标系统中的点的逻辑坐标系统中的点。  
  
 下面的映射模式设置后，调用`SetWindowExt`和`SetViewportExt`函数将被忽略︰  
  
- `MM_HIENGLISH`  
  
- `MM_HIMETRIC`  
  
- `MM_LOENGLISH`  
  
- `MM_LOMETRIC`  
  
- `MM_TEXT`  
  
- `MM_TWIPS`  
  
 当`MM_ISOTROPIC`模式设置，应用程序必须调用`SetWindowExt`成员函数之前调用`SetViewportExt`。  
  
### <a name="example"></a>示例  
  请参阅示例[CView::OnPrepareDC](../../mfc/reference/cview-class.md#onpreparedc)。  
  
##  <a name="a-namesetwindoworga--cdcsetwindoworg"></a><a name="setwindoworg"></a>CDC::SetWindowOrg  
 设置设备上下文的窗口原点。  
  
```  
CPoint SetWindowOrg(
    int x,  
    int y);  
  
CPoint SetWindowOrg(POINT point);
```  
  
### <a name="parameters"></a>参数  
 *x*  
 指定窗口的新起点的逻辑 x 坐标。  
  
 *y*  
 指定窗口的新起点的逻辑 y 坐标。  
  
 `point`  
 指定的逻辑坐标的新窗口的原点。 您可以传递**点**结构或`CPoint`为此参数的对象。  
  
### <a name="return-value"></a>返回值  
 窗口中，根据以前原点`CPoint`对象。  
  
### <a name="remarks"></a>备注  
 窗口中的，设备上下文视区，以及定义 GDI 如何映射到设备坐标系统中的点的逻辑坐标系统中的点。  
  
 窗口原点标记从中 GDI 映射视区原点，由指定的设备坐标系统中的点的逻辑坐标系统中的点**SetWindowOrg**函数。 通过映射到视区原点的窗口原点需按照同一过程，GDI 映射所有其他点。 例如，在窗口原点的点为圆心中的所有点都将处于圆心在视区原点的点。 同样，通过窗口原点的行中的所有点都将通过视区原点的行中。  
  
##  <a name="a-namesetworldtransforma--cdcsetworldtransform"></a><a name="setworldtransform"></a>CDC::SetWorldTransform  
 设置全局空间和指定的设备上下文的页面空间之间的二维线性转换。 此转换可用于缩放、 旋转、 倾斜对象，或将图形输出的转换。  
  
```  
BOOL SetWorldTransform(const XFORM& rXform);
```  
  
### <a name="parameters"></a>参数  
 `rXform`  
 引用[XFORM](http://msdn.microsoft.com/library/windows/desktop/dd145228)结构，其中包含转换数据。  
  
### <a name="return-value"></a>返回值  
 如果成功返回非零值。  
  
 失败时返回 0。  
  
 若要获得扩展错误信息，请调用[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)。  
  
### <a name="remarks"></a>备注  
 此方法将包装 Windows GDI 函数[SetWorldTransform](http://msdn.microsoft.com/library/windows/desktop/dd145104)。  
  
##  <a name="a-namestartdoca--cdcstartdoc"></a><a name="startdoc"></a>CDC::StartDoc  
 通知的设备驱动程序启动新的打印作业，所有后续`StartPage`和`EndPage`调用应假脱机保存在同一个作业之前`EndDoc`调用为止。  
  
```  
int StartDoc(LPDOCINFO lpDocInfo);  
int StartDoc(LPCTSTR lpszDocName);
```  
  
### <a name="parameters"></a>参数  
 *lpDocInfo*  
 指向[DOCINFO](http://msdn.microsoft.com/library/windows/desktop/dd183574)结构，它包含文档文件的名称和输出文件的名称。  
  
 *lpszDocName*  
 包含文档文件的名称的字符串的指针。  
  
### <a name="return-value"></a>返回值  
 如果函数成功，则返回值是大于零。 此值是文档的打印作业标识符。  
  
 如果函数失败，返回的值小于或等于零。  
  
### <a name="remarks"></a>备注  
 这可确保文档超过一页将不能与其他作业进行分布。  
  
 对于 Windows 3.1 及更高版本，此函数将替换**STARTDOC**打印机转义。 使用此函数可确保与其他打印作业的用户不能交错包含多个页面的文档。  
  
 `StartDoc`不应在图元文件内使用。  
  
### <a name="example"></a>示例  
 此代码片段中获取默认打印机，打开一个打印作业，并会将输出包含"Hello，World ！"个页面 它。 由于打印由下面的代码的文本不缩放到打印机的逻辑单元，因此输出文本可能在这种大小写字母的结果是不可读。 缩放功能，如 CDC `SetMapMode`， `SetViewportOrg`，和`SetWindowExt`，可用于修复的缩放。  
  
 [!code-cpp[NVC_MFCDocView #&41;](../../mfc/codesnippet/cpp/cdc-class_13.cpp)]  
  
##  <a name="a-namestartpagea--cdcstartpage"></a><a name="startpage"></a>CDC::StartPage  
 调用该成员函数以准备打印机驱动程序以接收数据。  
  
```  
int StartPage();
```  
  
### <a name="return-value"></a>返回值  
 大于或等于 0，如果函数运行成功，则为负值是否发生了错误。  
  
### <a name="remarks"></a>备注  
 `StartPage`取代**NEWFRAME**和**BANDINFO**进行转义。  
  
 打印调用的顺序的概述，请参阅[StartDoc](#startdoc)成员函数。  
  
 系统禁用`ResetDC`之间调用成员函数`StartPage`和`EndPage`。  
  
### <a name="example"></a>示例  
  请参阅示例[CDC::StartDoc](#startdoc)。  
  
##  <a name="a-namestretchblta--cdcstretchblt"></a><a name="stretchblt"></a>CDC::StretchBlt  
 将位图从源矩形复制到目标矩形，必要时可拉伸或压缩位图以符合目标矩形的尺寸。  
  
```  
BOOL StretchBlt(
    int x,  
    int y,  
    int nWidth,  
    int nHeight,  
    CDC* pSrcDC,  
    int xSrc,  
    int ySrc,  
    int nSrcWidth,  
    int nSrcHeight,  
    DWORD dwRop);
```  
  
### <a name="parameters"></a>参数  
 *x*  
 指定目标矩形左上角的 x 坐标（使用逻辑单位）。  
  
 *y*  
 指定目标矩形左上角的 y 坐标（使用逻辑单位）。  
  
 `nWidth`  
 指定目标矩形的宽度（使用逻辑单位）。  
  
 `nHeight`  
 指定目标矩形的高度（使用逻辑单位）。  
  
 `pSrcDC`  
 指定源设备上下文。  
  
 `xSrc`  
 指定源矩形左上角的 x 坐标（使用逻辑单位）。  
  
 `ySrc`  
 指定源矩形左上角的 y 坐标（使用逻辑单位）。  
  
 `nSrcWidth`  
 指定源矩形的宽度（使用逻辑单位）。  
  
 `nSrcHeight`  
 指定源矩形的高度（使用逻辑单位）。  
  
 *dwRop*  
 指定要执行的光栅操作。 光栅操作代码定义 GDI 如何合并涉及当前画笔、可能的源位图和目标位图的输出操作中的颜色。 该参数可能是下列值之一：  
  
- **BLACKNESS** -使所有输出黑变。  
  
- **DSTINVERT** -反转目标位图。  
  
- **MERGECOPY** -合并模式使用布尔 AND 运算符的源位图。  
  
- **MERGEPAINT** -合并反转的源位图与目标位图，并使用布尔 OR 运算符。  
  
- **NOTSRCCOPY**将反转的源位图复制到目标。  
  
- **NOTSRCERASE** -反转目标位图与源位图使用布尔 OR 运算符组合的结果。  
  
- **PATCOPY**将模式复制到目标位图。  
  
- **PATINVERT** -合并目标位图与模式，即使用布尔 XOR 运算符。  
  
- **PATPAINT** -合并反转的源位图与模式，即使用布尔 OR 运算符。 使用布尔 OR 运算符合并该操作的结果与目标位图。  
  
- **SRCAND** -合并使用布尔 AND 运算符的目标和源位图的像素。  
  
- **SRCCOPY**将源位图复制到目标位图。  
  
- **SRCERASE** -反转目标位图并与源位图使用布尔 AND 运算符合并结果。  
  
- **SRCINVERT** -合并使用布尔 XOR 运算符的目标和源位图的像素。  
  
- **SRCPAINT** -合并使用布尔 OR 运算符的目标和源位图的像素。  
  
- **WHITENESS** -使所有输出白色变。  
  
### <a name="return-value"></a>返回值  
 如果绘制出位图，则为非 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 该函数使用目标设备上下文的拉伸模式（由 `SetStretchBltMode` 设置）确定如何拉伸或压缩位图。  
  
 `StretchBlt` 函数将 `pSrcDC` 给定的源设备中的位图移动到其成员函数即将被调用的设备上下文对象所表示的目标设备。 `xSrc`、`ySrc`、`nSrcWidth` 和 `nSrcHeight` 参数定义源矩形的左上角和尺寸。 *X*， *y*， `nWidth`，和`nHeight`参数提供的左上角和目标矩形的尺寸。 通过指定的光栅操作*dwRop*定义如何将源位图和目标设备上已的位组合。  
  
 如果 `StretchBlt` 与 `nSrcWidth` 或 `nWidth` 与 `nSrcHeight` 参数的符号不同，则 `nHeight` 函数将创建位图的镜像。 如果 `nSrcWidth` 与 `nWidth` 符号不同，则该函数将沿 x 轴创建位图的镜像。 如果 `nSrcHeight` 与 `nHeight` 符号不同，则该函数将沿 y 轴创建位图的镜像。  
  
 `StretchBlt` 函数将在内存中拉伸或压缩源位图，然后将结果复制到目标。 如果一个模式将与该结果合并，则合并操作会等到拉伸的源位图复制到目标后执行。 如果使用画笔，则为在目标设备上下文中选择的画笔。 目标坐标将根据目标设备上下文进行转换；源坐标将根据源设备上下文进行转换。  
  
 如果目标位图、源位图和模式位图没有相同的颜色格式，`StretchBlt` 将转换源位图和模式位图，以与目标位图匹配。 在转换中将使用目标设备上下文的前景色和背景色。  
  
 如果 `StretchBlt` 必须将单色位图转换为彩色，则会将白色位 (1) 设置为背景色，黑色位 (0) 设置为前景色。 若要将彩色位图转换为单色，它会将与背景色匹配的像素设置为白色 (1)，其他所有像素设置为黑色 (0)。 在转换中将使用彩色设备上下文的前景色和背景色。  
  
 不是所有的设备都支持 `StretchBlt` 函数。 若要确定设备是否支持`StretchBlt`，调用`GetDeviceCaps`成员函数时**RASTERCAPS**编制索引，并检查返回值**RC_STRETCHBLT**标志。  
  
##  <a name="a-namestrokeandfillpatha--cdcstrokeandfillpath"></a><a name="strokeandfillpath"></a>CDC::StrokeAndFillPath  
 关闭任何打开的图形路径中，通过使用当前笔笔触路径轮廓和通过使用当前画笔填充其内部。  
  
```  
BOOL StrokeAndFillPath();
```  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 设备上下文必须包含封闭的路径。 `StrokeAndFillPath`成员函数具有相同的效果关闭在路径中，所有打开的图形和描边，并分别填充路径，只不过填充的区域不重叠空心的区域即使触笔位于宽。  
  
##  <a name="a-namestrokepatha--cdcstrokepath"></a><a name="strokepath"></a>CDC::StrokePath  
 使用当前笔呈现指定的路径。  
  
```  
BOOL StrokePath();
```  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 设备上下文必须包含封闭的路径。  
  
##  <a name="a-nametabbedtextouta--cdctabbedtextout"></a><a name="tabbedtextout"></a>CDC::TabbedTextOut  
 调用该成员函数以写入的字符字符串中指定的位置，将选项卡扩展到的制表位位置数组中指定的值。  
  
```  
virtual CSize TabbedTextOut(
    int x,  
    int y,  
    LPCTSTR lpszString,  
    int nCount,  
    int nTabPositions,  
    LPINT lpnTabStopPositions,  
    int nTabOrigin);

 
CSize TabbedTextOut(
    int x,  
    int y,  
    const CString& str,  
    int nTabPositions,  
    LPINT lpnTabStopPositions,  
    int nTabOrigin);
```  
  
### <a name="parameters"></a>参数  
 *x*  
 指定字符串的起始点的逻辑 x 坐标。  
  
 *y*  
 指定字符串的起始点的逻辑 y 坐标。  
  
 `lpszString`  
 指向要绘制的字符串。 可以将任一指针传递给一个字符数组或[CString](../../atl-mfc-shared/reference/cstringt-class.md)为此参数的对象。  
  
 `nCount`  
 指定字符串中的字符数。 如果`nCount`为 –&1;，长度进行计算。  
  
 `nTabPositions`  
 制表位位置的数组中指定的值的数目。  
  
 `lpnTabStopPositions`  
 指向数组，其中包含的制表位位置 （使用逻辑单位）。 必须按递增顺序; 排序的制表位最小的 x 值应为数组中的第一项。  
  
 `nTabOrigin`  
 指定从中制表符扩展 （使用逻辑单位） 的起始位置的 x 坐标。  
  
 `str`  
 一个`CString`对象，其中包含指定的字符。  
  
### <a name="return-value"></a>返回值  
 尺寸 （以逻辑单位） 将字符串作为`CSize`对象。  
  
### <a name="remarks"></a>备注  
 文本编写中当前选定的字体。 如果`nTabPositions`为 0 和`lpnTabStopPositions`是**NULL**，选项卡扩展到八次平均字符宽度。  
  
 如果`nTabPositions`为 1，选项卡中的第一个值所指定的距离分隔停止`lpnTabStopPositions`数组。 如果`lpnTabStopPositions`数组包含多个值，为每个值在数组中，最多指定的数量设置制表位`nTabPositions`。 `nTabOrigin`参数允许应用程序调用`TabbedTextOut`几次对于单行的函数。 如果应用程序将调用该函数不止一次与`nTabOrigin`每次设置为相同的值，该函数将扩展相对于指定的位置的所有选项卡`nTabOrigin`。  
  
 默认情况下，函数不使用或更新当前位置。 如果应用程序需要更新当前位置，当调用函数，该应用程序可以调用[SetTextAlign](#settextalign)成员函数时`nFlags`设置为**TA_UPDATECP**。 当设置此标志时，Windows 将忽略*x*和*y*到后续调用的参数`TabbedTextOut`，而使用当前位置。  
  
##  <a name="a-nametextouta--cdctextout"></a><a name="textout"></a>CDC::TextOut  
 使用当前选定的字体在指定位置写入字符串。  
  
```  
virtual BOOL TextOut(
    int x,  
    int y,  
    LPCTSTR lpszString,  
    int nCount);

 
BOOL TextOut(
    int x,
    int y,
    const CString& str);
```  
  
### <a name="parameters"></a>参数  
 *x*  
 指定文本起点的逻辑 x 坐标。  
  
 *y*  
 指定文本起点的逻辑 y 坐标。  
  
 `lpszString`  
 指向要绘制的字符串。  
  
 `nCount`  
 指定字符串中的字符数。  
  
 `str`  
 包含要绘制的字符的 `CString` 对象。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 字符原点位于字符单元格的左上角。 默认情况下，函数不使用或更新当前位置。  
  
 如果应用程序时需要更新当前位置，它调用`TextOut`，应用程序可以调用`SetTextAlign`成员函数时`nFlags`设置为**TA_UPDATECP**。 当设置此标志时，Windows 将忽略*x*和*y*到后续调用的参数`TextOut`，而使用当前位置。  
  
### <a name="example"></a>示例  
  请参阅示例[cdc:: beginpath](#beginpath)。  
  
##  <a name="a-nametransparentblta--cdctransparentblt"></a><a name="transparentblt"></a>CDC::TransparentBlt  
 调用该成员函数以传输到目标设备上下文中指定的源设备上下文中，对应于像素组成的矩形的颜色数据位块。  
  
```  
BOOL TransparentBlt(
    int xDest,  
    int yDest,
    int nDestWidth,
    int nDestHeight,  
    CDC* pSrcDC,  
    int xSrc,  
    int ySrc,  
    int nSrcWidth,  
    int nSrcHeight,  
    UINT clrTransparent);
```  
  
### <a name="parameters"></a>参数  
 `xDest`  
 指定使用逻辑单位，目标矩形的左上角的 x 坐标。  
  
 `yDest`  
 指定使用逻辑单位，目标矩形的左上角的 y 坐标。  
  
 `nDestWidth`  
 指定不使用逻辑单位，目标矩形的宽度。  
  
 `nDestHeight`  
 指定的高度，以目标矩形的逻辑单元。  
  
 `pSrcDC`  
 指向源设备上下文指针。  
  
 `xSrc`  
 指定使用逻辑单位，源矩形的 x 坐标。  
  
 `ySrc`  
 指定使用逻辑单位，源矩形的 y 坐标。  
  
 `nSrcWidth`  
 指定不使用逻辑单位，源矩形的宽度。  
  
 `nSrcHeight`  
 指定使用逻辑单位，源矩形的高度。  
  
 `clrTransparent`  
 中要被视为透明的源位图的 RGB 颜色。  
  
### <a name="return-value"></a>返回值  
 **TRUE**如果成功，否则为**FALSE**。  
  
### <a name="remarks"></a>备注  
 `TransparentBlt`允许为透明;代表 RGB 颜色，即由`clrTransparent`呈现透明传输。  
  
 有关详细信息，请参阅[TransparentBlt](http://msdn.microsoft.com/library/windows/desktop/dd145141)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameupdatecolorsa--cdcupdatecolors"></a><a name="updatecolors"></a>CDC::UpdateColors  
 向系统调色板在逐像素基础上的工作区中更新通过匹配当前的设备上下文的工作区的颜色。  
  
```  
void UpdateColors();
```  
  
### <a name="remarks"></a>备注  
 带有已实现的逻辑调色板的非活动窗口都可以调用`UpdateColors`作为系统调色板发生更改时重绘其工作区的替代方法。  
  
 有关使用调色板的详细信息，请参阅[UpdateColors](http://msdn.microsoft.com/library/windows/desktop/dd145166)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `UpdateColors`成员函数通常比重新绘制区域更快地更新工作区。 但是，因为此函数将执行之前系统调色板更改基于每个像素颜色的颜色转换，每次调用此函数会导致一些颜色准确性丢失。  
  
##  <a name="a-namewidenpatha--cdcwidenpath"></a><a name="widenpath"></a>CDC::WidenPath  
 将当前路径重新定义为将如果该路径已对其应用笔划使用实际选入设备上下文笔进行绘画的区域。  
  
```  
BOOL WidenPath();
```  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 此函数是仅当当前笔是由第二个版本的创建几何笔成功`CreatePen`成员函数，或如果使用的第一个版本创建笔`CreatePen`和宽度，都以设备为单位，大于 1。 设备上下文必须包含封闭的路径。 在路径中的任何 Bzier 曲线转换为直线，直线逼近加宽的曲线的序列。 在这种情况下，在路径中之后, 保持没有 Bzier 曲线`WidenPath`调用。  
  
## <a name="see-also"></a>另请参阅  
 [CObject 类](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CPaintDC 类](../../mfc/reference/cpaintdc-class.md)   
 [CWindowDC 类](../../mfc/reference/cwindowdc-class.md)   
 [CClientDC 类](../../mfc/reference/cclientdc-class.md)   
 [CMetaFileDC 类](../../mfc/reference/cmetafiledc-class.md)

