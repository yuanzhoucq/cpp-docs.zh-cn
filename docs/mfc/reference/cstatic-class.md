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
ms.openlocfilehash: 1f6aac50b2143a4d5296baac906b1ebd0ef542f5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215954"
---
# <a name="cstatic-class"></a>CStatic 类

提供 Windows 静态控件功能。

## <a name="syntax"></a>语法

```
class CStatic : public CWnd
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CStatic::CStatic](#cstatic)|构造 `CStatic` 对象。|

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|[CStatic：： Create](#create)|创建 Windows 静态控件，并将其附加到 `CStatic` 对象。|
|[CStatic：:D rawItem](#drawitem)|重写以绘制所有者描述的静态控件。|
|[CStatic::GetBitmap](#getbitmap)|检索之前通过[SetBitmap](#setbitmap)设置的位图的句柄。|
|[CStatic::GetCursor](#getcursor)|检索之前通过[SetCursor](#setcursor)设置的游标图像的句柄。|
|[CStatic::GetEnhMetaFile](#getenhmetafile)|检索先前通过[SetEnhMetaFile](#setenhmetafile)设置的增强型图元文件的句柄。|
|[CStatic：： GetIcon](#geticon)|检索之前通过[SetIcon](#seticon)设置的图标的句柄。|
|[CStatic::SetBitmap](#setbitmap)|指定要在静态控件中显示的位图。|
|[CStatic::SetCursor](#setcursor)|指定要在静态控件中显示的游标图像。|
|[CStatic::SetEnhMetaFile](#setenhmetafile)|指定要在静态控件中显示的增强型图元文件。|
|[CStatic::SetIcon](#seticon)|指定要在静态控件中显示的图标。|

## <a name="remarks"></a>备注

静态控件显示文本字符串、框、矩形、图标、光标、位图或增强型图元文件。 它可用于标记、框或分隔其他控件。 静态控件通常不使用输入，不提供输出;不过，如果是用 SS_NOTIFY 样式创建的，则它可以通知其父项的鼠标单击。

通过两个步骤创建一个静态控件。 首先，调用构造函数来构造 `CStatic` 对象，然后调用[create](#create)成员函数以创建静态控件，并将其附加到 `CStatic` 对象。

如果在 `CStatic` 对话框中创建对象（通过对话资源），则 `CStatic` 当用户关闭对话框时，对象会自动销毁。

如果在 `CStatic` 窗口中创建对象，则可能还需要销毁它。 `CStatic`在窗口中的堆栈上创建的对象将自动销毁。 如果 `CStatic` 使用函数在堆上创建对象 **`new`** ，则必须对该对象调用， **`delete`** 以在完成后将其销毁。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CStatic`

## <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="cstaticcreate"></a><a name="create"></a>CStatic：： Create

创建 Windows 静态控件，并将其附加到 `CStatic` 对象。

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
指定要放置在控件中的文本。 如果为 NULL，则不显示文本。

*dwStyle*<br/>
指定静态控件的窗口样式。 将任意[静态控件样式](../../mfc/reference/styles-used-by-mfc.md#static-styles)组合应用于控件。

*rect*<br/>
指定静态控件的位置和大小。 它可以是结构， `RECT` 也可以是 `CRect` 对象。

*pParentWnd*<br/>
指定 `CStatic` 父窗口，通常为 `CDialog` 对象。 值不得为 NULL。

*nID*<br/>
指定静态控件的控件 ID。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

`CStatic`按两个步骤构造对象。 首先，调用构造函数 `CStatic` ，然后调用 `Create` ，它创建 Windows 静态控件，并将其附加到 `CStatic` 对象。

将以下[窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)应用于静态控件：

- 始终 WS_CHILD

- WS_VISIBLE 通常

- 很少 WS_DISABLED

如果要在静态控件中显示位图、光标、图标或图元文件，则需要应用以下[静态样式](../../mfc/reference/styles-used-by-mfc.md#static-styles)之一：

- SS_BITMAP 将此样式用于位图。

- SS_ICON 将此样式用于游标和图标。

- SS_ENHMETAFILE 将此样式用于增强型图元文件。

对于游标、位图或图标，还可以使用以下样式：

- SS_CENTERIMAGE 使用来使图像在静态控件中居中。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CStatic#1](../../mfc/reference/codesnippet/cpp/cstatic-class_1.cpp)]

## <a name="cstaticcstatic"></a><a name="cstatic"></a>CStatic::CStatic

构造 `CStatic` 对象。

```
CStatic();
```

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CStatic#2](../../mfc/reference/codesnippet/cpp/cstatic-class_2.cpp)]

## <a name="cstaticdrawitem"></a><a name="drawitem"></a>CStatic：:D rawItem

由框架调用，用于绘制所有者描述的静态控件。

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>参数

*lpDrawItemStruct*<br/>
指向[DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct)结构的指针。 结构包含有关要绘制的项的信息以及所需的绘图类型。

### <a name="remarks"></a>备注

重写此函数可为所有者描述的对象实现绘图 `CStatic` （控件具有样式 SS_OWNERDRAW）。

## <a name="cstaticgetbitmap"></a><a name="getbitmap"></a>CStatic::GetBitmap

获取与关联的、以前设置了[SetBitmap](#setbitmap)的位图的句柄 `CStatic` 。

```
HBITMAP GetBitmap() const;
```

### <a name="return-value"></a>返回值

当前位图的句柄; 如果尚未设置位图，则为 NULL。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CStatic#3](../../mfc/reference/codesnippet/cpp/cstatic-class_3.cpp)]

## <a name="cstaticgetcursor"></a><a name="getcursor"></a>CStatic::GetCursor

获取与关联的、以前设置了[SetCursor](#setcursor)的游标的句柄 `CStatic` 。

```
HCURSOR GetCursor();
```

### <a name="return-value"></a>返回值

当前游标的句柄，如果未设置任何游标，则为 NULL。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CStatic#4](../../mfc/reference/codesnippet/cpp/cstatic-class_4.cpp)]

## <a name="cstaticgetenhmetafile"></a><a name="getenhmetafile"></a>CStatic::GetEnhMetaFile

获取与相关联的增强型图元文件的句柄，它以前设置了[SetEnhMetafile](#setenhmetafile) `CStatic` 。

```
HENHMETAFILE GetEnhMetaFile() const;
```

### <a name="return-value"></a>返回值

当前增强型图元文件的句柄，或者为 NULL （如果未设置增强型图元文件）。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CStatic#5](../../mfc/reference/codesnippet/cpp/cstatic-class_5.cpp)]

## <a name="cstaticgeticon"></a><a name="geticon"></a>CStatic：： GetIcon

获取与关联的图标的句柄，它以前设置了[SetIcon](#seticon) `CStatic` 。

```
HICON GetIcon() const;
```

### <a name="return-value"></a>返回值

当前图标的句柄，如果未设置图标，则为 NULL。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CStatic#6](../../mfc/reference/codesnippet/cpp/cstatic-class_6.cpp)]

## <a name="cstaticsetbitmap"></a><a name="setbitmap"></a>CStatic::SetBitmap

将新位图与静态控件相关联。

```
HBITMAP SetBitmap(HBITMAP hBitmap);
```

### <a name="parameters"></a>参数

*hBitmap*<br/>
要在静态控件中绘制的位图的句柄。

### <a name="return-value"></a>返回值

之前与静态控件关联的位图的句柄; 如果没有与静态控件关联的位图，则为 NULL。

### <a name="remarks"></a>备注

将在静态控件中自动绘制位图。 默认情况下，它将在左上角绘制，静态控件的大小将调整为位图的大小。

您可以使用各种窗口和静态控件样式，包括：

- SS_BITMAP 将此样式始终用于位图。

- SS_CENTERIMAGE 使用来使图像在静态控件中居中。 如果图像大于静态控件，则会将其剪切。 如果它小于静态控件，则该图像周围的空白空间将由位图左上角中的像素颜色填充。

- MFC 提供类 `CBitmap` ，当您必须使用位图图像执行更多操作，而不只是调用 Win32 函数时，可以使用 `LoadBitmap` 。 `CBitmap`，它包含一种 GDI 对象，通常与结合使用 `CStatic` ，后者是 `CWnd` 用于将图形对象显示为静态控件的类。

`CImage`是一个 ATL/MFC 类，使你能够更轻松地使用与设备无关的位图（DIB）。 有关详细信息，请参阅[CImage 类](../../atl-mfc-shared/reference/cimage-class.md)。

- 典型用法是指定 `CStatic::SetBitmap` 由或对象的 HBITMAP 运算符返回的 GDI 对象 `CBitmap` `CImage` 。 用于执行此操作的代码类似于以下行。

```
MyStaticControl.SetBitmap(HBITMAP(MyBitmap));
```

下面的示例在堆上创建两个 `CStatic` 对象。 然后，它使用系统位图加载一个 `CBitmap::LoadOEMBitmap` ，并使用从文件中的另一个进行加载 `CImage::Load` 。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CStatic#3](../../mfc/reference/codesnippet/cpp/cstatic-class_3.cpp)]

## <a name="cstaticsetcursor"></a><a name="setcursor"></a>CStatic::SetCursor

将新的光标图像与静态控件相关联。

```
HCURSOR SetCursor(HCURSOR hCursor);
```

### <a name="parameters"></a>参数

*hCursor*<br/>
要在静态控件中绘制的光标的句柄。

### <a name="return-value"></a>返回值

之前与静态控件关联的游标的句柄; 如果没有与静态控件关联的游标，则为 NULL。

### <a name="remarks"></a>备注

将在静态控件中自动绘制光标。 默认情况下，它将在左上角绘制，静态控件将调整为光标的大小。

您可以使用各种窗口和静态控件样式，包括以下各项：

- SS_ICON 将此样式始终用于游标和图标。

- SS_CENTERIMAGE 使用在静态控件中居中。 如果图像大于静态控件，则会将其剪切。 如果它小于静态控件，则将用静态控件的背景色填充该图像周围的空白空间。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CStatic#4](../../mfc/reference/codesnippet/cpp/cstatic-class_4.cpp)]

## <a name="cstaticsetenhmetafile"></a><a name="setenhmetafile"></a>CStatic::SetEnhMetaFile

将新的增强型图元文件图像与静态控件相关联。

```
HENHMETAFILE SetEnhMetaFile(HENHMETAFILE hMetaFile);
```

### <a name="parameters"></a>参数

*hMetaFile*<br/>
要在静态控件中绘制的增强型图元文件的句柄。

### <a name="return-value"></a>返回值

先前与静态控件关联的增强型图元文件的句柄; 如果没有与该静态控件关联的增强型图元文件，则为 NULL。

### <a name="remarks"></a>备注

增强型图元文件将自动绘制在静态控件中。 增强型图元文件可进行缩放以适应静态控件的大小。

您可以使用各种窗口和静态控件样式，包括以下各项：

- SS_ENHMETAFILE 将此样式始终用于增强型图元文件。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CStatic#5](../../mfc/reference/codesnippet/cpp/cstatic-class_5.cpp)]

## <a name="cstaticseticon"></a><a name="seticon"></a>CStatic::SetIcon

将新的图标图像与静态控件相关联。

```
HICON SetIcon(HICON hIcon);
```

### <a name="parameters"></a>参数

*hIcon*<br/>
要在静态控件中绘制的图标的句柄。

### <a name="return-value"></a>返回值

之前与静态控件关联的图标的句柄; 如果没有与静态控件关联的图标，则为 NULL。

### <a name="remarks"></a>备注

该图标将在静态控件中自动绘制。 默认情况下，它将在左上角绘制，静态控件将调整为图标大小。

您可以使用各种窗口和静态控件样式，包括以下各项：

- SS_ICON 将此样式始终用于游标和图标。

- SS_CENTERIMAGE 使用在静态控件中居中。 如果图像大于静态控件，则会将其剪切。 如果它小于静态控件，则将用静态控件的背景色填充该图像周围的空白空间。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CStatic#6](../../mfc/reference/codesnippet/cpp/cstatic-class_6.cpp)]

## <a name="see-also"></a>另请参阅

[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[CButton 类](../../mfc/reference/cbutton-class.md)<br/>
[CComboBox 类](../../mfc/reference/ccombobox-class.md)<br/>
[CEdit 类](../../mfc/reference/cedit-class.md)<br/>
[CListBox 类](../../mfc/reference/clistbox-class.md)<br/>
[CScrollBar 类](../../mfc/reference/cscrollbar-class.md)<br/>
[CDialog 类](../../mfc/reference/cdialog-class.md)
