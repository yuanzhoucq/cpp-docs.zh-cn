---
title: CStatic 类
ms.date: 11/04/2016
f1_keywords:
- CStatic
- AFXWIN/CStatic
- AFXWIN/CStatic::CStatic
- AFXWIN/CStatic::Create
- AFXWIN/CStatic::DrawItem
- AFXWIN/CStatic::GetBitmap
- AFXWIN/CStatic::GetCursor
- AFXWIN/CStatic::GetEnhMetaFile
- AFXWIN/CStatic::GetIcon
- AFXWIN/CStatic::SetBitmap
- AFXWIN/CStatic::SetCursor
- AFXWIN/CStatic::SetEnhMetaFile
- AFXWIN/CStatic::SetIcon
helpviewer_keywords:
- CStatic [MFC], CStatic
- CStatic [MFC], Create
- CStatic [MFC], DrawItem
- CStatic [MFC], GetBitmap
- CStatic [MFC], GetCursor
- CStatic [MFC], GetEnhMetaFile
- CStatic [MFC], GetIcon
- CStatic [MFC], SetBitmap
- CStatic [MFC], SetCursor
- CStatic [MFC], SetEnhMetaFile
- CStatic [MFC], SetIcon
ms.assetid: e7c94cd9-5ebd-428a-aa30-b3e51f8efb95
ms.openlocfilehash: e5c3705c0aa2fd90e73cb54ba5a97c252ed2cf83
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371645"
---
# <a name="cstatic-class"></a>CStatic 类

提供 Windows 静态控件功能。

## <a name="syntax"></a>语法

```
class CStatic : public CWnd
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[静态：：静态](#cstatic)|构造 `CStatic` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[静态：：创建](#create)|创建 Windows 静态控件并将其附加到`CStatic`对象。|
|[静态：:D原始项目](#drawitem)|覆盖以绘制所有者绘制的静态控件。|
|[静态：：获取位图](#getbitmap)|检索以前使用[SetBitmap](#setbitmap)设置的位图的句柄。|
|[静态：：获取光标](#getcursor)|检索以前使用[SetCursor](#setcursor)设置的游标图像的句柄。|
|[静态：：获取EnhMetaFile](#getenhmetafile)|检索以前使用[SetEnhMetaFile](#setenhmetafile)设置的增强元文件的句柄。|
|[静态：：获取图标](#geticon)|检索以前使用[SetIcon](#seticon)设置的图标的句柄。|
|[静态：：设置位图](#setbitmap)|指定要在静态控件中显示的位图。|
|[静态：：设置游标](#setcursor)|指定要在静态控件中显示的光标图像。|
|[静态：：SetEnhMetaFile](#setenhmetafile)|指定要在静态控件中显示的增强元文件。|
|[静态：：设置图标](#seticon)|指定要在静态控件中显示的图标。|

## <a name="remarks"></a>备注

静态控件显示文本字符串、框、矩形、图标、光标、位图或增强的元文件。 它可用于标记、框或分隔其他控件。 静态控件通常不需要输入，并且不提供输出;但是，如果鼠标单击是使用SS_NOTIFY样式创建的，则可以通知其父级鼠标单击。

分两步创建静态控件。 首先，调用构造函数构造`CStatic`对象，然后调用[Create](#create)成员函数以创建静态控件并将其附加到`CStatic`对象。

如果在对话框中创建`CStatic`对象（通过对话框资源），则当用户关闭对话框时，`CStatic`该对象将自动销毁。

如果在窗口中创建`CStatic`对象，则可能需要销毁它。 在`CStatic`窗口内的堆栈上创建的对象将自动销毁。 如果使用**新**函数在`CStatic`堆上创建对象，**则必须调用**delete 对象以在使用该对象时销毁该对象。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CStatic`

## <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="cstaticcreate"></a><a name="create"></a>静态：：创建

创建 Windows 静态控件并将其附加到`CStatic`对象。

```
virtual BOOL Create(
    LPCTSTR lpszText,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID = 0xffff);
```

### <a name="parameters"></a>参数

*lpszText*<br/>
指定要放置在控件中的文本。 如果为 NULL，则看不到任何文本。

*dwStyle*<br/>
指定静态控件的窗口样式。 将[静态控件样式](../../mfc/reference/styles-used-by-mfc.md#static-styles)的任意组合应用于控件。

*矩形*<br/>
指定静态控件的位置和大小。 它可以是`RECT`结构或`CRect`对象。

*pparentwnd*<br/>
指定`CStatic`父窗口，通常是`CDialog`对象。 值不得为 NULL。

*nID*<br/>
指定静态控件的控制 ID。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

分两`CStatic`步构造对象。 首先调用构造函数`CStatic`，然后调用`Create`，这将创建 Windows 静态控件并将其附加到`CStatic`对象。

将以下[窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)应用于静态控件：

- WS_CHILD始终

- WS_VISIBLE 通常

- WS_DISABLED很少

如果要在静态控件中显示位图、光标、图标或元文件，则需要应用以下[静态样式](../../mfc/reference/styles-used-by-mfc.md#static-styles)之一：

- SS_BITMAP 此样式用于位图。

- SS_ICON 此样式用于光标和图标。

- SS_ENHMETAFILE使用此样式增强元文件。

对于光标、位图或图标，您可能还需要使用以下样式：

- SS_CENTERIMAGE 用于将图像居中居于静态控件中。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CStatic#1](../../mfc/reference/codesnippet/cpp/cstatic-class_1.cpp)]

## <a name="cstaticcstatic"></a><a name="cstatic"></a>静态：：静态

构造 `CStatic` 对象。

```
CStatic();
```

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CStatic#2](../../mfc/reference/codesnippet/cpp/cstatic-class_2.cpp)]

## <a name="cstaticdrawitem"></a><a name="drawitem"></a>静态：:D原始项目

由框架调用以绘制所有者绘制的静态控件。

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>参数

*lpDraw 项目已结*<br/>
指向[DRAWITEMSTRUCT 结构的](/windows/win32/api/winuser/ns-winuser-drawitemstruct)指针。 结构包含有关要绘制的项和所需绘图类型的信息。

### <a name="remarks"></a>备注

重写此函数以实现所有者绘制`CStatic`的对象的绘图（控件具有样式SS_OWNERDRAW）。

## <a name="cstaticgetbitmap"></a><a name="getbitmap"></a>静态：：获取位图

获取位图的句柄，以前使用[SetBitmap](#setbitmap)设置，该句柄与`CStatic`相关联。

```
HBITMAP GetBitmap() const;
```

### <a name="return-value"></a>返回值

当前位图的句柄，如果未设置位图，则为 NULL。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CStatic#3](../../mfc/reference/codesnippet/cpp/cstatic-class_3.cpp)]

## <a name="cstaticgetcursor"></a><a name="getcursor"></a>静态：：获取光标

获取以前使用[SetCursor](#setcursor)设置的与`CStatic`关联的游标的句柄。

```
HCURSOR GetCursor();
```

### <a name="return-value"></a>返回值

当前游标的句柄，如果未设置游标，则为 NULL。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CStatic#4](../../mfc/reference/codesnippet/cpp/cstatic-class_4.cpp)]

## <a name="cstaticgetenhmetafile"></a><a name="getenhmetafile"></a>静态：：获取EnhMetaFile

获取增强型元文件的句柄，以前使用[SetEnhMetafile](#setenhmetafile)设置，该文件与`CStatic`相关联。

```
HENHMETAFILE GetEnhMetaFile() const;
```

### <a name="return-value"></a>返回值

当前增强的元文件句柄，如果未设置增强的元文件，则为 NULL。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CStatic#5](../../mfc/reference/codesnippet/cpp/cstatic-class_5.cpp)]

## <a name="cstaticgeticon"></a><a name="geticon"></a>静态：：获取图标

获取以前使用[SetIcon](#seticon)设置的图标的句柄，该句柄与`CStatic`相关联。

```
HICON GetIcon() const;
```

### <a name="return-value"></a>返回值

当前图标的句柄，如果未设置图标，则为 NULL。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CStatic#6](../../mfc/reference/codesnippet/cpp/cstatic-class_6.cpp)]

## <a name="cstaticsetbitmap"></a><a name="setbitmap"></a>静态：：设置位图

将新的位图与静态控件关联。

```
HBITMAP SetBitmap(HBITMAP hBitmap);
```

### <a name="parameters"></a>参数

*hBitmap*<br/>
要在静态控件中绘制的位图的句柄。

### <a name="return-value"></a>返回值

以前与静态控件关联的位图的句柄，如果没有位图与静态控件关联的则 NULL 的句柄。

### <a name="remarks"></a>备注

位图将自动在静态控件中绘制。 默认情况下，它将在左上角绘制，静态控件将调整为位图的大小。

您可以使用各种窗口和静态控件样式，包括：

- SS_BITMAP 始终使用此样式进行位图。

- SS_CENTERIMAGE 用于将图像居中居于静态控件中。 如果图像大于静态控件，则将剪切它。 如果小于静态控件，则图像周围的空白空间将由位图左上角的像素颜色填充。

- MFC 提供类`CBitmap`，当您必须对位图图像执行更多操作时，可以使用该类，而不仅仅是调用 Win32`LoadBitmap`函数。 `CBitmap`包含一种 GDI 对象，通常与`CStatic`配合使用，该`CWnd`对象用于将图形对象显示为静态控件。

`CImage`是 ATL/MFC 类，可让您更轻松地使用设备独立位图 （DIB）。 有关详细信息，请参阅[CImage 类](../../atl-mfc-shared/reference/cimage-class.md)。

- 典型用法是提供`CStatic::SetBitmap``CBitmap`由 或`CImage`对象的 HBITMAP 运算符返回的 GDI 对象。 执行此操作的代码类似于以下行。

```
MyStaticControl.SetBitmap(HBITMAP(MyBitmap));
```

下面的示例在堆上`CStatic`创建两个对象。 然后，它使用`CBitmap::LoadOEMBitmap`系统位图加载一个，从 使用`CImage::Load`的文件加载另一个。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CStatic#3](../../mfc/reference/codesnippet/cpp/cstatic-class_3.cpp)]

## <a name="cstaticsetcursor"></a><a name="setcursor"></a>静态：：设置游标

将新的光标图像与静态控件关联。

```
HCURSOR SetCursor(HCURSOR hCursor);
```

### <a name="parameters"></a>参数

*h光标*<br/>
要在静态控件中绘制的光标的句柄。

### <a name="return-value"></a>返回值

以前与静态控件关联的游标的句柄，如果没有与静态控件关联的游标，则为 NULL。

### <a name="remarks"></a>备注

光标将自动在静态控件中绘制。 默认情况下，它将在左上角绘制，静态控件将调整为光标的大小。

您可以使用各种窗口和静态控件样式，包括：

- SS_ICON 始终使用此样式用于游标和图标。

- SS_CENTERIMAGE 用于在静态控件中居中。 如果图像大于静态控件，则将剪切它。 如果小于静态控件，则图像周围的空白空间将填充静态控件的背景颜色。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CStatic#4](../../mfc/reference/codesnippet/cpp/cstatic-class_4.cpp)]

## <a name="cstaticsetenhmetafile"></a><a name="setenhmetafile"></a>静态：：SetEnhMetaFile

将新的增强元文件映像与静态控件关联。

```
HENHMETAFILE SetEnhMetaFile(HENHMETAFILE hMetaFile);
```

### <a name="parameters"></a>参数

*hMetaFile*<br/>
要在静态控件中绘制的增强元文件的句柄。

### <a name="return-value"></a>返回值

以前与静态控件关联的增强元文件的句柄，如果没有与静态控件关联的增强元文件，则 NULL 的句柄。

### <a name="remarks"></a>备注

增强的元文件将自动在静态控件中绘制。 增强的元文件将缩放以适合静态控件的大小。

您可以使用各种窗口和静态控件样式，包括：

- SS_ENHMETAFILE 始终使用此样式进行增强的元文件。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CStatic#5](../../mfc/reference/codesnippet/cpp/cstatic-class_5.cpp)]

## <a name="cstaticseticon"></a><a name="seticon"></a>静态：：设置图标

将新的图标图像与静态控件关联。

```
HICON SetIcon(HICON hIcon);
```

### <a name="parameters"></a>参数

*hIcon*<br/>
要在静态控件中绘制的图标的句柄。

### <a name="return-value"></a>返回值

以前与静态控件关联的图标的句柄，如果没有与静态控件关联的图标，则为 NULL。

### <a name="remarks"></a>备注

图标将自动在静态控件中绘制。 默认情况下，它将在左上角绘制，静态控件将调整为图标的大小。

您可以使用各种窗口和静态控件样式，包括：

- SS_ICON 始终使用此样式用于游标和图标。

- SS_CENTERIMAGE 用于在静态控件中居中。 如果图像大于静态控件，则将剪切它。 如果小于静态控件，则图像周围的空白空间将填充静态控件的背景颜色。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CStatic#6](../../mfc/reference/codesnippet/cpp/cstatic-class_6.cpp)]

## <a name="see-also"></a>另请参阅

[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[C按钮类](../../mfc/reference/cbutton-class.md)<br/>
[CComboBox 类](../../mfc/reference/ccombobox-class.md)<br/>
[CEdit Class](../../mfc/reference/cedit-class.md)<br/>
[CListBox 类](../../mfc/reference/clistbox-class.md)<br/>
[CScrollBar 类](../../mfc/reference/cscrollbar-class.md)<br/>
[CDialog 类](../../mfc/reference/cdialog-class.md)
