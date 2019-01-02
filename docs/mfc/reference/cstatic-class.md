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
ms.openlocfilehash: ab25cad77ee0f11167661bb27b408dd5e92b51f9
ms.sourcegitcommit: 975098222db3e8b297607cecaa1f504570a11799
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2018
ms.locfileid: "53178689"
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

|名称|描述|
|----------|-----------------|
|[CStatic::Create](#create)|创建 Windows 静态控件，并将其附加到`CStatic`对象。|
|[CStatic::DrawItem](#drawitem)|重写以绘制所有者描述的静态控件。|
|[CStatic::GetBitmap](#getbitmap)|检索以前设置的位图的句柄[SetBitmap](#setbitmap)。|
|[CStatic::GetCursor](#getcursor)|检索与以前设置的光标图像句柄[SetCursor](#setcursor)。|
|[CStatic::GetEnhMetaFile](#getenhmetafile)|检索以前设置的增强型图元文件的句柄[SetEnhMetaFile](#setenhmetafile)。|
|[CStatic::GetIcon](#geticon)|检索以前设置的图标的句柄[SetIcon](#seticon)。|
|[CStatic::SetBitmap](#setbitmap)|指定要在静态控件中显示的位图。|
|[CStatic::SetCursor](#setcursor)|指定要在静态控件中显示的光标图像。|
|[CStatic::SetEnhMetaFile](#setenhmetafile)|指定要在静态控件中显示增强型图元文件。|
|[CStatic::SetIcon](#seticon)|指定要在静态控件中显示的图标。|

## <a name="remarks"></a>备注

静态控件显示文本字符串、 框、 矩形、 图标、 光标、 位图或增强图元文件。 它可以用于标签、 框中，或单独的其他控件。 静态控件通常不接受任何输入，并不提供任何输出;但是，它可以通知其父级的鼠标单击，如果它使用调用 SS_NOTIFY 样式创建。

在两个步骤中创建了静态控件。 首先，调用构造函数来构造`CStatic`对象，然后调用[创建](#create)成员函数以创建静态控件并将其附加到`CStatic`对象。

如果您创建`CStatic`（通过对话框资源） 对话框中的对象`CStatic`在用户关闭对话框时自动销毁对象。

如果您创建`CStatic`对象内一个窗口，您可能还需要将其销毁。 一个`CStatic`自动销毁对象的时间段内在堆栈上创建。 如果您创建`CStatic`通过使用堆上的对象**新**函数，必须调用**删除**上要使用它完成后将其销毁的对象。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CStatic`

## <a name="requirements"></a>要求

**标头:** afxwin.h

##  <a name="create"></a>  CStatic::Create

创建 Windows 静态控件，并将其附加到`CStatic`对象。

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
指定要放置在控件中的文本。 如果为 NULL，则没有文本将可见。

*dwStyle*<br/>
指定静态控件的窗口样式。 应用的任意组合[静态控件样式](../../mfc/reference/styles-used-by-mfc.md#static-styles)到控件。

*rect*<br/>
指定的位置和静态控件的大小。 它可以是`RECT`结构或`CRect`对象。

*pParentWnd*<br/>
指定`CStatic`父窗口中，通常`CDialog`对象。 它不能为 NULL。

*nID*<br/>
指定静态控件的控件 id。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

构造`CStatic`两个步骤中的对象。 首先，调用构造函数`CStatic`，然后调用`Create`，它创建 Windows 静态控件并将其附加到`CStatic`对象。

将以下内容应用[的窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)到静态控件：

- WS_CHILD 始终

- WS_VISIBLE 通常

- WS_DISABLED 很少

如果您要在静态控件中显示位图、 光标、 图标或图元文件，您将需要应用以下值之一[静态样式](../../mfc/reference/styles-used-by-mfc.md#static-styles):

- SS_BITMAP 针对位图使用此样式。

- SS_ICON 使用此样式的游标和图标。

- SS_ENHMETAFILE 增强型图元文件中使用此样式。

对于游标、 位图或图标，可能还想要使用的以下样式：

- SS_CENTERIMAGE 使用静态控件中的图像居中。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CStatic#1](../../mfc/reference/codesnippet/cpp/cstatic-class_1.cpp)]

##  <a name="cstatic"></a>  CStatic::CStatic

构造 `CStatic` 对象。

```
CStatic();
```

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CStatic#2](../../mfc/reference/codesnippet/cpp/cstatic-class_2.cpp)]

##  <a name="drawitem"></a>  CStatic::DrawItem

由框架调用以绘制所有者描述的静态控件。

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>参数

*lpDrawItemStruct*<br/>
一个指向[DRAWITEMSTRUCT](/windows/desktop/api/winuser/ns-winuser-tagdrawitemstruct)结构。 该结构包含有关要绘制的项和绘图所需的类型信息。

### <a name="remarks"></a>备注

重写此函数可实现为所有者描述绘制`CStatic`对象 （该控件具有样式 SS_OWNERDRAW）。

##  <a name="getbitmap"></a>  CStatic::GetBitmap

获取与以前设置的位图的句柄[SetBitmap](#setbitmap)，即与关联`CStatic`。

```
HBITMAP GetBitmap() const;
```

### <a name="return-value"></a>返回值

句柄的当前位图或如果没有位图已设置为 NULL。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CStatic#3](../../mfc/reference/codesnippet/cpp/cstatic-class_3.cpp)]

##  <a name="getcursor"></a>  CStatic::GetCursor

获取与之前设置光标的句柄[SetCursor](#setcursor)，即与关联`CStatic`。

```
HCURSOR GetCursor();
```

### <a name="return-value"></a>返回值

句柄的当前光标或如果没有游标已设置为 NULL。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CStatic#4](../../mfc/reference/codesnippet/cpp/cstatic-class_4.cpp)]

##  <a name="getenhmetafile"></a>  CStatic::GetEnhMetaFile

获取增强型图元文件，使用以前设置的句柄[SetEnhMetafile](#setenhmetafile)，即与关联`CStatic`。

```
HENHMETAFILE GetEnhMetaFile() const;
```

### <a name="return-value"></a>返回值

句柄的当前增强型图元文件或如果没有增强型图元文件已设置为 NULL。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CStatic#5](../../mfc/reference/codesnippet/cpp/cstatic-class_5.cpp)]

##  <a name="geticon"></a>  CStatic::GetIcon

获取与以前设置的图标的句柄[SetIcon](#seticon)，即与关联`CStatic`。

```
HICON GetIcon() const;
```

### <a name="return-value"></a>返回值

句柄的当前图标或如果没有图标已设置为 NULL。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CStatic#6](../../mfc/reference/codesnippet/cpp/cstatic-class_6.cpp)]

##  <a name="setbitmap"></a>  CStatic::SetBitmap

将新的位图与静态控件相关联。

```
HBITMAP SetBitmap(HBITMAP hBitmap);
```

### <a name="parameters"></a>参数

*hBitmap*<br/>
要在静态控件中绘制的位图的句柄。

### <a name="return-value"></a>返回值

如果没有位图是与静态控件相关联的以前关联的静态控件或为 NULL 位图的句柄。

### <a name="remarks"></a>备注

将静态控件中自动绘制位图。 默认情况下，它将绘制在左上角中，静态控件的大小将调整为位图的大小。

可以使用各种窗口和静态控件样式，其中包括：

- SS_BITMAP 针对位图始终使用此样式。

- SS_CENTERIMAGE 使用静态控件中的图像居中。 如果图像大于静态控件，它将被裁剪。 如果它小于静态控件，将通过位图左上角中的像素的颜色来填充在图像周围的空白区域。

- MFC 提供的类`CBitmap`，你需要执行更多与位图图像不是只需调用 Win32 函数时可以使用它们`LoadBitmap`。 `CBitmap`其中包含一种类型的 GDI 对象，经常会用与协作`CStatic`，这是`CWnd`类，用于显示作为静态控件的图形对象。

`CImage` 是一个 ATL/MFC 类，使您能够更轻松地使用设备无关位图 (DIB)。 有关详细信息，请参阅[中的 CImage 类](../../atl-mfc-shared/reference/cimage-class.md)。

- 典型用法是为提供`CStatic::SetBitmap`由 HBITMAP 运算符的返回的 GDI 对象`CBitmap`或`CImage`对象。 若要执行此操作的代码类似于以下行。

```
MyStaticControl.SetBitmap(HBITMAP(MyBitmap));
```
下面的示例创建两个`CStatic`堆上的对象。 然后将加载一个具有系统位图使用`CBitmap::LoadOEMBitmap`和从文件使用其他`CImage::Load`。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CStatic#3](../../mfc/reference/codesnippet/cpp/cstatic-class_3.cpp)]

##  <a name="setcursor"></a>  CStatic::SetCursor

将新的光标图像与静态控件相关联。

```
HCURSOR SetCursor(HCURSOR hCursor);
```

### <a name="parameters"></a>参数

*hCursor*<br/>
要在静态控件中绘制的光标的句柄。

### <a name="return-value"></a>返回值

以前如果无游标与静态控件相关联的静态控件或为 NULL 与关联的光标句柄。

### <a name="remarks"></a>备注

将静态控件中自动绘制光标。 默认情况下，它将绘制在左上角中，静态控件将调整为光标的大小。

可以使用各种窗口和静态控件样式，其中包括：

- SS_ICON 光标和图标始终使用此样式。

- SS_CENTERIMAGE 使用静态控件中居中。 如果图像大于静态控件，它将被裁剪。 如果它小于静态控件，将使用静态控件的背景色填充在图像周围的空白区域。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CStatic#4](../../mfc/reference/codesnippet/cpp/cstatic-class_4.cpp)]

##  <a name="setenhmetafile"></a>  CStatic::SetEnhMetaFile

将新的增强型图元文件图像与静态控件相关联。

```
HENHMETAFILE SetEnhMetaFile(HENHMETAFILE hMetaFile);
```

### <a name="parameters"></a>参数

*hMetaFile*<br/>
增强型图元文件绘制静态控件中的句柄。

### <a name="return-value"></a>返回值

增强型图元文件与静态控件或为空的以前关联，如果没有增强型图元文件是与静态控件关联的句柄。

### <a name="remarks"></a>备注

增强型图元文件将自动绘制静态控件中。 增强型图元文件进行缩放以适合静态控件的大小。

可以使用各种窗口和静态控件样式，其中包括：

- SS_ENHMETAFILE 使用此样式始终为增强型图元文件。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CStatic#5](../../mfc/reference/codesnippet/cpp/cstatic-class_5.cpp)]

##  <a name="seticon"></a>  CStatic::SetIcon

将新图标图像与静态控件相关联。

```
HICON SetIcon(HICON hIcon);
```

### <a name="parameters"></a>参数

*hIcon*<br/>
要在静态控件中绘制的图标的句柄。

### <a name="return-value"></a>返回值

以前没有图标是否与静态控件相关联的静态控件或为 NULL 与关联的图标的句柄。

### <a name="remarks"></a>备注

将静态控件中自动绘制图标。 默认情况下，它将绘制在左上角中，静态控件的大小将调整到图标的大小。

可以使用各种窗口和静态控件样式，其中包括：

- SS_ICON 光标和图标始终使用此样式。

- SS_CENTERIMAGE 使用静态控件中居中。 如果图像大于静态控件，它将被裁剪。 如果它小于静态控件，将使用静态控件的背景色填充在图像周围的空白区域。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CStatic#6](../../mfc/reference/codesnippet/cpp/cstatic-class_6.cpp)]

## <a name="see-also"></a>请参阅

[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[CButton 类](../../mfc/reference/cbutton-class.md)<br/>
[CComboBox 类](../../mfc/reference/ccombobox-class.md)<br/>
[CEdit 类](../../mfc/reference/cedit-class.md)<br/>
[CListBox 类](../../mfc/reference/clistbox-class.md)<br/>
[CScrollBar 类](../../mfc/reference/cscrollbar-class.md)<br/>
[CDialog 类](../../mfc/reference/cdialog-class.md)
