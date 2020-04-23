---
title: CImageList 类
ms.date: 11/04/2016
f1_keywords:
- CImageList
- AFXCMN/CImageList
- AFXCMN/CImageList::CImageList
- AFXCMN/CImageList::Add
- AFXCMN/CImageList::Attach
- AFXCMN/CImageList::BeginDrag
- AFXCMN/CImageList::Copy
- AFXCMN/CImageList::Create
- AFXCMN/CImageList::DeleteImageList
- AFXCMN/CImageList::DeleteTempMap
- AFXCMN/CImageList::Detach
- AFXCMN/CImageList::DragEnter
- AFXCMN/CImageList::DragLeave
- AFXCMN/CImageList::DragMove
- AFXCMN/CImageList::DragShowNolock
- AFXCMN/CImageList::Draw
- AFXCMN/CImageList::DrawEx
- AFXCMN/CImageList::DrawIndirect
- AFXCMN/CImageList::EndDrag
- AFXCMN/CImageList::ExtractIcon
- AFXCMN/CImageList::FromHandle
- AFXCMN/CImageList::FromHandlePermanent
- AFXCMN/CImageList::GetBkColor
- AFXCMN/CImageList::GetDragImage
- AFXCMN/CImageList::GetImageCount
- AFXCMN/CImageList::GetImageInfo
- AFXCMN/CImageList::GetSafeHandle
- AFXCMN/CImageList::Read
- AFXCMN/CImageList::Remove
- AFXCMN/CImageList::Replace
- AFXCMN/CImageList::SetBkColor
- AFXCMN/CImageList::SetDragCursorImage
- AFXCMN/CImageList::SetImageCount
- AFXCMN/CImageList::SetOverlayImage
- AFXCMN/CImageList::Write
- AFXCMN/CImageList::m_hImageList
helpviewer_keywords:
- CImageList [MFC], CImageList
- CImageList [MFC], Add
- CImageList [MFC], Attach
- CImageList [MFC], BeginDrag
- CImageList [MFC], Copy
- CImageList [MFC], Create
- CImageList [MFC], DeleteImageList
- CImageList [MFC], DeleteTempMap
- CImageList [MFC], Detach
- CImageList [MFC], DragEnter
- CImageList [MFC], DragLeave
- CImageList [MFC], DragMove
- CImageList [MFC], DragShowNolock
- CImageList [MFC], Draw
- CImageList [MFC], DrawEx
- CImageList [MFC], DrawIndirect
- CImageList [MFC], EndDrag
- CImageList [MFC], ExtractIcon
- CImageList [MFC], FromHandle
- CImageList [MFC], FromHandlePermanent
- CImageList [MFC], GetBkColor
- CImageList [MFC], GetDragImage
- CImageList [MFC], GetImageCount
- CImageList [MFC], GetImageInfo
- CImageList [MFC], GetSafeHandle
- CImageList [MFC], Read
- CImageList [MFC], Remove
- CImageList [MFC], Replace
- CImageList [MFC], SetBkColor
- CImageList [MFC], SetDragCursorImage
- CImageList [MFC], SetImageCount
- CImageList [MFC], SetOverlayImage
- CImageList [MFC], Write
- CImageList [MFC], m_hImageList
ms.assetid: b6d1a704-1c82-4548-8a8f-77972adc98a5
ms.openlocfilehash: 17cd2a94cb397e59e4622aea8ed7bb6fbe1eee43
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752688"
---
# <a name="cimagelist-class"></a>CImageList 类

提供 Windows 公共图像列表控件的功能。

## <a name="syntax"></a>语法

```
class CImageList : public CObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CImageList：CImageList](#cimagelist)|构造 `CImageList` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CImageList：添加](#add)|将图像或图像添加到图像列表。|
|[CImage 列表：：附加](#attach)|将图像列表附加到`CImageList`对象。|
|[CImageList：：开始拖动](#begindrag)|开始拖动图像。|
|[CImageList：复制](#copy)|复制`CImageList`对象中的图像。|
|[CImageList：创建](#create)|初始化图像列表并将其附加到`CImageList`对象。|
|[CImageList：:DeleteImageList](#deleteimagelist)|删除图像列表。|
|[CImageList：:DeleteTempMap](#deletetempmap)|由[CWinApp](../../mfc/reference/cwinapp-class.md)空闲时间处理程序调用以删除 由`CImageList``FromHandle`创建的任何临时对象。|
|[CImageList：:D埃塔奇](#detach)|从`CImageList`对象分离图像列表对象，并将句柄返回到图像列表。|
|[CImageList：:D拉格输入](#dragenter)|锁定拖动操作期间的更新，并在指定位置显示拖动图像。|
|[CImageList：:D拉格叶](#dragleave)|解锁窗口并隐藏拖动图像，以便可以更新窗口。|
|[CImageList：:D拉格移动](#dragmove)|移动拖放操作期间正在拖动的图像。|
|[CImageList：:D拉格秀诺洛克](#dragshownolock)|在拖动操作期间显示或隐藏拖动图像，而不锁定窗口。|
|[CImageList：:D原始](#draw)|绘制拖放操作期间正在拖动的图像。|
|[CImageList：:D原始](#drawex)|在指定的设备上下文中绘制图像列表项。 该函数使用指定的绘图样式，并将图像与指定颜色混合。|
|[CImageList：:D原始间接](#drawindirect)|从图像列表中绘制图像。|
|[CImageList：结束拖动](#enddrag)|结束拖动操作。|
|[CImage列表：：提取图标](#extracticon)|基于图像列表中的图像和蒙版创建图标。|
|[CImageList：从手处理](#fromhandle)|当为图像列表指定`CImageList`句柄时，返回指向对象的指针。 如果 `CImageList` 对象未附加到该句柄，则会创建并附加一个临时 `CImageList` 对象。|
|[CImageList：：从永久处理](#fromhandlepermanent)|当为图像列表指定`CImageList`句柄时，返回指向对象的指针。 如果对象`CImageList`未附加到句柄，则返回 NULL。|
|[CImageList：获取BkColor](#getbkcolor)|检索图像列表的当前背景颜色。|
|[CImage列表：：获取拖动图像](#getdragimage)|获取用于拖动的临时图像列表。|
|[CImage列表：获取图像计数](#getimagecount)|检索图像列表中的图像数。|
|[CImageList：获取图片信息](#getimageinfo)|检索有关图像的信息。|
|[CImageList：：获取安全处理](#getsafehandle)|检索`m_hImageList`。|
|[CImageList：阅读](#read)|从存档中读取图像列表。|
|[CImage 列表：：删除](#remove)|从图像列表中删除图像。|
|[CImageList：替换](#replace)|将图像列表中的图像替换为新图像。|
|[CImageList：SetBkColor](#setbkcolor)|设置图像列表的背景颜色。|
|[CImageList：：设置DragCursor图像](#setdragcursorimage)|创建新的拖动图像。|
|[CImage列表：：设置图像计数](#setimagecount)|重置图像列表中的图像计数。|
|[CImageList：：设置叠加图像](#setoverlayimage)|将图像的零基索引添加到要用作叠加蒙版的图像列表中。|
|[CImageList：写入](#write)|将映像列表写入存档。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CImageList：：操作员HIMAGELIST](#operator_himagelist)|返回附加到 的`CImageList`HIMAGELIST。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CImageList：m_hImageList](#m_himagelist)|包含附加到此对象的图像列表的句柄。|

## <a name="remarks"></a>备注

"图像列表"是相同大小的图像的集合，每个图像都可以由其零基索引引用。 图像列表用于有效地管理大的图标或位图集。 图像列表中的所有图像都包含在单个宽幅位图中，屏幕设备格式为"宽" 图像列表可能包含一个单色位图，该位图包含用于透明地绘制图像的蒙板（图标样式）。 Microsoft Win32 应用程序编程接口 （API） 提供图像列表功能，使您能够绘制图像、创建和销毁图像列表、添加和删除图像、替换图像、合并图像和拖动图像。

此控件（因此该`CImageList`类）仅适用于在 Windows 95/98 和 Windows NT 版本 3.51 及更高版本下运行的程序。

有关 使用`CImageList`的详细信息，请参阅[控件](../../mfc/controls-mfc.md)[和使用 CImageList](../../mfc/using-cimagelist.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CImageList`

## <a name="requirements"></a>要求

**标头：** afxcmn.h

## <a name="cimagelistadd"></a><a name="add"></a>CImageList：添加

调用此函数以向图像列表添加一个或多个图像或图标。

```
int Add(
    CBitmap* pbmImage,
    CBitmap* pbmMask);

int Add(
    CBitmap* pbmImage,
    COLORREF crMask);

int Add(HICON hIcon);
```

### <a name="parameters"></a>参数

*pbmImage*<br/>
指向包含图像或图像的位图的指针。 图像数从位图的宽度推断出来。

*pbmMask*<br/>
指向包含掩码的位图的指针。 如果图像列表不使用掩码，则忽略此参数。

*crMask*<br/>
用于生成蒙版的颜色。 给定位图中此颜色的每个像素都更改为黑色，蒙版中的相应位设置为 1。

*hIcon*<br/>
包含新图像的位图和蒙版的图标的句柄。

### <a name="return-value"></a>返回值

第一个新图像的零基索引（如果成功）;否则 - 1。

### <a name="remarks"></a>备注

完成图标句柄后，您有责任释放它。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CImageList#1](../../mfc/reference/codesnippet/cpp/cimagelist-class_1.cpp)]

## <a name="cimagelistattach"></a><a name="attach"></a>CImage 列表：：附加

调用此函数以将图像列表附加到`CImageList`对象。

```
BOOL Attach(HIMAGELIST hImageList);
```

### <a name="parameters"></a>参数

*h图像列表*<br/>
图像列表对象的句柄。

### <a name="return-value"></a>返回值

附件成功时非零;否则 0。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CImageList#2](../../mfc/reference/codesnippet/cpp/cimagelist-class_2.cpp)]

## <a name="cimagelistbegindrag"></a><a name="begindrag"></a>CImageList：：开始拖动

调用此函数以开始拖动图像。

```
BOOL BeginDrag(
    int nImage,
    CPoint ptHotSpot);
```

### <a name="parameters"></a>参数

*n图像*<br/>
要拖动的图像的零索引。

*点热点*<br/>
起始拖动位置的坐标（通常为光标位置）。 坐标相对于图像的左上角。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

此函数创建用于拖动的临时图像列表。 图像将指定的图像及其蒙版与当前光标合并。 为了响应后续WM_MOUSEMOVE消息，可以使用`DragMove`成员函数移动拖动图像。 要结束拖动操作，可以使用`EndDrag`成员函数。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CImageList#3](../../mfc/reference/codesnippet/cpp/cimagelist-class_3.cpp)]

## <a name="cimagelistcimagelist"></a><a name="cimagelist"></a>CImageList：CImageList

构造 `CImageList` 对象。

```
CImageList();
```

## <a name="cimagelistcopy"></a><a name="copy"></a>CImageList：复制

此成员函数实现 Win32 函数[ImageList_Copy](/windows/win32/api/commctrl/nf-commctrl-imagelist_copy)的行为，如 Windows SDK 中所述。

```
BOOL Copy(
    int iDst,
    int iSrc,
    UINT uFlags = ILCF_MOVE);

BOOL Copy(
    int iDst,
    CImageList* pSrc,
    int iSrc,
    UINT uFlags = ILCF_MOVE);
```

### <a name="parameters"></a>参数

*iDst*<br/>
用作复制操作目标的图像的零基索引。

*伊斯尔克*<br/>
用作复制操作源的图像的零基索引。

*uFlags*<br/>
指定要进行的副本操作类型的位标志值。 此参数可以是以下值之一：

|“值”|含义|
|-----------|-------------|
|ILCF_MOVE|源图像将复制到目标图像的索引。 此操作会导致给定映像的多个实例。 ILCF_MOVE是默认值。|
|ILCF_SWAP|源图像和目标图像交换图像列表中的位置。|

*pSrc*<br/>
指向`CImageList`对象作为复制操作目标的指针。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CImageList#6](../../mfc/reference/codesnippet/cpp/cimagelist-class_4.cpp)]

## <a name="cimagelistcreate"></a><a name="create"></a>CImageList：创建

初始化图像列表并将其附加到[CImageList](../../mfc/reference/cimagelist-class.md)对象。

```
BOOL Create(
    int cx,
    int cy,
    UINT nFlags,
    int nInitial,
    int nGrow);

BOOL Create(
    UINT nBitmapID,
    int cx,
    int nGrow,
    COLORREF crMask);

BOOL Create(
    LPCTSTR lpszBitmapID,
    int cx,
    int nGrow,
    COLORREF crMask);

BOOL Create(
    CImageList& imagelist1,
    int nImage1,
    CImageList& imagelist2,
    int nImage2,
    int dx,
    int dy);

BOOL Create(CImageList* pImageList);
```

### <a name="parameters"></a>参数

*残雪*<br/>
每个图像的尺寸（以像素为单位）。

*cy*<br/>
每个图像的尺寸（以像素为单位）。

*nFlags*<br/>
指定要创建的图像列表的类型。 此参数可以是以下值的组合，但它只能包含其中一个`ILC_COLOR`值。

|“值”|含义|
|-----------|-------------|
|ILC_COLOR|如果未指定其他ILC_COLOR* 标志，则使用默认行为。 通常，默认值为ILC_COLOR4;则为"ILC_COLOR4"但对于较旧的显示驱动程序，默认值为ILC_COLORDDB。|
|ILC_COLOR4|使用 4 位（16 种颜色）与设备无关的位图 （DIB） 部分作为图像列表的位图。|
|ILC_COLOR8|使用 8 位 DIB 部分。 用于颜色表的颜色与半色调调色板的颜色相同。|
|ILC_COLOR16|使用 16 位（32/64k 颜色）DIB 部分。|
|ILC_COLOR24|使用 24 位 DIB 部分。|
|ILC_COLOR32|使用 32 位 DIB 部分。|
|ILC_COLORDDB|使用与设备相关的位图。|
|ILC_MASK|使用掩码。 图像列表包含两个位图，其中一个是用作蒙版的单色位图。 如果未包含此值，则图像列表仅包含一个位图。 有关蒙版图像的其他信息[，请参阅从图像列表中绘制图像](../../mfc/drawing-images-from-an-image-list.md)。|

*n初始*<br/>
图像列表最初包含的图像数。

*n 增长*<br/>
当系统需要调整列表大小以为新图像腾出空间时，图像列表可以增长的图像数。 此参数表示调整大小的图像列表可以包含的新映像数。

*nBitmapID*<br/>
要与图像列表关联的位图的资源指示。

*crMask*<br/>
用于生成蒙版的颜色。 指定位图中此颜色的每个像素都更改为黑色，蒙版中的相应位设置为 1。

*lpszBitmapID*<br/>
包含图像的资源指示的字符串。

*图像列表1*<br/>
对 `CImageList` 对象的引用。

*nImage1*<br/>
第一个现有图像的索引。

*图像列表2*<br/>
对 `CImageList` 对象的引用。

*nImage2*<br/>
第二个现有图像的索引。

*Dx*<br/>
第二个图像的 x 轴与第一个图像（以像素为单位）的偏移。

*Dy*<br/>
第二个图像的 y 轴与第一个图像（以像素为单位）的偏移。

*pImageList*<br/>
一个指向 `CImageList` 对象的指针。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

在两个步骤`CImageList`中构造 一个。 首先调用构造函数，然后调用`Create`，这将创建图像列表并将其附加到`CImageList`对象。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CImageList#7](../../mfc/reference/codesnippet/cpp/cimagelist-class_5.cpp)]

## <a name="cimagelistdeleteimagelist"></a><a name="deleteimagelist"></a>CImageList：:DeleteImageList

调用此函数以删除图像列表。

```
BOOL DeleteImageList();
```

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CImageList#8](../../mfc/reference/codesnippet/cpp/cimagelist-class_6.cpp)]

## <a name="cimagelistdeletetempmap"></a><a name="deletetempmap"></a>CImageList：:DeleteTempMap

由`CWinApp`空闲时间处理程序自动调用`DeleteTempMap`，删除[FromHandle](#fromhandle)创建`CImageList`的任何临时对象，但不会销毁与`ImageList`对象临时关联的任何句柄`hImageList`（）。

```
static void PASCAL DeleteTempMap();
```

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CImageList#9](../../mfc/reference/codesnippet/cpp/cimagelist-class_7.cpp)]

## <a name="cimagelistdetach"></a><a name="detach"></a>CImageList：:D埃塔奇

调用此函数以从`CImageList`对象分离图像列表对象。

```
HIMAGELIST Detach();
```

### <a name="return-value"></a>返回值

图像列表对象的句柄。

### <a name="remarks"></a>备注

此函数返回图像列表对象的句柄。

### <a name="example"></a>示例

  请参阅[CImageList 的示例：：附加](#attach)。

## <a name="cimagelistdragenter"></a><a name="dragenter"></a>CImageList：:D拉格输入

在拖动操作期间，锁定*pWndLock*指定的窗口的更新，并在*点*指定的位置显示拖动图像。

```
static BOOL PASCAL DragEnter(
    CWnd* pWndLock,
    CPoint point);
```

### <a name="parameters"></a>参数

*pWndLock*<br/>
指向拥有拖动图像的窗口的指针。

*点*<br/>
要显示拖动图像的位置。 坐标相对于窗口的左上角（而不是工作区）。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

坐标相对于窗口的左上角，因此在指定坐标时，必须补偿窗口元素（如边框、标题栏和菜单栏）的宽度。

如果*pWndLock*为 NULL，则此函数将在与桌面窗口关联的显示上下文中绘制图像，坐标相对于屏幕的左上角。

此函数在拖动操作期间锁定给定窗口的所有其他更新。 如果需要在拖动操作期间执行任何绘图（例如突出显示拖放操作的目标），可以使用[CImageList：:DragLeave](#dragleave)函数暂时隐藏拖动的图像。

### <a name="example"></a>示例

  请参阅[CImageList 的示例：：开始拖动](#begindrag)。

## <a name="cimagelistdragleave"></a><a name="dragleave"></a>CImageList：:D拉格叶

解锁*pWndLock*指定的窗口并隐藏拖动图像，从而允许更新该窗口。

```
static BOOL PASCAL DragLeave(CWnd* pWndLock);
```

### <a name="parameters"></a>参数

*pWndLock*<br/>
指向拥有拖动图像的窗口的指针。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="example"></a>示例

  请参阅[CImageList：：结束拖动的示例](#enddrag)。

## <a name="cimagelistdragmove"></a><a name="dragmove"></a>CImageList：:D拉格移动

调用此函数以移动在拖放操作期间拖动的图像。

```
static BOOL PASCAL DragMove(CPoint pt);
```

### <a name="parameters"></a>参数

*pt*<br/>
新的拖动位置。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

通常调用此函数是为了响应WM_MOUSEMOVE消息。 要开始拖动操作，`BeginDrag`请使用成员函数。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CImageList#4](../../mfc/reference/codesnippet/cpp/cimagelist-class_8.cpp)]

## <a name="cimagelistdragshownolock"></a><a name="dragshownolock"></a>CImageList：:D拉格秀诺洛克

在拖动操作期间显示或隐藏拖动图像，而不锁定窗口。

```
static BOOL PASCAL DragShowNolock(BOOL bShow);
```

### <a name="parameters"></a>参数

*b显示*<br/>
指定是否显示拖动图像。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

[CImageList：:DragEnter 函数](#dragenter)在拖动操作期间锁定窗口的所有更新。 但是，此功能不会锁定窗口。

## <a name="cimagelistdraw"></a><a name="draw"></a>CImageList：:D原始

调用此函数以绘制在拖放操作期间拖动的图像。

```
BOOL Draw(
    CDC* pDC,
    int nImage,
    POINT pt,
    UINT nStyle);
```

### <a name="parameters"></a>参数

*pDC*<br/>
指向目标设备上下文的指针。

*n图像*<br/>
要绘制的图像的零基索引。

*pt*<br/>
在指定的设备上下文中绘制的位置。

*nStyle*<br/>
指定绘图样式的标志。 它可以是以下一个或多个值：

|“值”|含义|
|-----------|-------------|
|ILD_BLEND25，ILD_FOCUS|绘制图像，将 25% 与系统高光颜色混合。 如果图像列表不包含蒙版，则此值无效。|
|ILD_BLEND50，ILD_SELECTED，ILD_BLEND|绘制图像，将 50% 与系统高光颜色混合。 如果图像列表不包含蒙版，则此值无效。|
|ILD_MASK|绘制蒙版。|
|ILD_NORMAL|使用图像列表的背景颜色绘制图像。 如果背景色为CLR_NONE值，则使用蒙版以透明方式绘制图像。|
|ILD_TRANSPARENT|无论背景颜色如何，都使用蒙版透明地绘制图像。|

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="example"></a>示例

  请参阅[CImageList 的示例：：设置覆盖图像](#setoverlayimage)。

## <a name="cimagelistdrawex"></a><a name="drawex"></a>CImageList：:D原始

在指定的设备上下文中绘制图像列表项。

```
BOOL DrawEx(
    CDC* pDC,
    int nImage,
    POINT pt,
    SIZE sz,
    COLORREF clrBk,
    COLORREF clrFg,
    UINT nStyle);
```

### <a name="parameters"></a>参数

*pDC*<br/>
指向目标设备上下文的指针。

*n图像*<br/>
要绘制的图像的零基索引。

*pt*<br/>
在指定的设备上下文中绘制的位置。

*深圳*<br/>
图像相对于图像左上角绘制的部分的大小。 在 Windows SDK 中[查看 ImageList_DrawEx](/windows/win32/api/commctrl/nf-commctrl-imagelist_drawex)中的*dx* *和 dy。*

*clrBk*<br/>
图像的背景颜色。 在 Windows SDK 中查看[ImageList_DrawEx](/windows/win32/api/commctrl/nf-commctrl-imagelist_drawex)中的*rgbBk。*

*clrFg*<br/>
图像的前景颜色。 在 Windows SDK 中[查看 ImageList_DrawEx](/windows/win32/api/commctrl/nf-commctrl-imagelist_drawex)中的*rgbFg。*

*nStyle*<br/>
指定绘图样式的标志。 请参阅 windows SDK 中[ImageList_DrawEx](/windows/win32/api/commctrl/nf-commctrl-imagelist_drawex)*中的 fStyle。*

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

该函数使用指定的绘图样式，并将图像与指定颜色混合。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CImageList#10](../../mfc/reference/codesnippet/cpp/cimagelist-class_9.cpp)]

## <a name="cimagelistdrawindirect"></a><a name="drawindirect"></a>CImageList：:D原始间接

调用此成员函数从图像列表中绘制图像。

```
BOOL DrawIndirect(IMAGELISTDRAWPARAMS* pimldp);

BOOL DrawIndirect(
    CDC* pDC,
    int nImage,
    POINT pt,
    SIZE sz,
    POINT ptOrigin,
    UINT fStyle = ILD_NORMAL,
    DWORD dwRop = SRCCOPY,
    COLORREF rgbBack = CLR_DEFAULT,
    COLORREF rgbFore = CLR_DEFAULT,
    DWORD fState = ILS_NORMAL,
    DWORD Frame = 0,
    COLORREF crEffect = CLR_DEFAULT);
```

### <a name="parameters"></a>参数

*皮姆LDP*<br/>
指向[图像列表DRAWPARAMS](/windows/win32/api/commctrl/ns-commctrl-imagelistdrawparams)结构的指针，其中包含有关绘制操作的信息。

*pDC*<br/>
指向目标设备上下文的指针。 完成此[CDC](../../mfc/reference/cdc-class.md)对象后，必须将其删除。

*n图像*<br/>
要绘制的图像的零基索引。

*pt*<br/>
包含绘制图像的 x 和 y 坐标的[POINT](/windows/win32/api/windef/ns-windef-point)结构。

*深圳*<br/>
指示要绘制的图像大小的[SIZE](/windows/win32/api/windef/ns-windef-size)结构。

*ptOrigin*<br/>
包含 x 坐标和 y 坐标的[POINT](/windows/win32/api/windef/ns-windef-point)结构，用于指定绘图操作相对于图像本身的左上角。 不绘制 x 坐标左侧和 y 坐标上方图像的像素。

*fStyle*<br/>
指定绘图样式的标志，以及（可选）叠加图像。 有关叠加图像的信息，请参阅备注部分。 MFC 默认实现ILD_NORMAL使用图像列表的背景颜色绘制图像。 如果背景色为CLR_NONE值，则使用蒙版以透明方式绘制图像。

其他可能的样式在[IMAGELISTDRAWPARAMS](/windows/win32/api/commctrl/ns-commctrl-imagelistdrawparams)结构的*fStyle*成员下描述。

*dwRop*<br/>
指定栅格操作代码的值。 这些代码定义如何将源矩形的颜色数据与目标矩形的颜色数据组合，以实现最终颜色。 MFC 的默认实现 SRCCOPY 将源矩形直接复制到目标矩形。 如果*fStyle*参数不包含ILD_ROP标志，则忽略此参数。

其他可能的值在[IMAGELISTDRAWPARAMS](/windows/win32/api/commctrl/ns-commctrl-imagelistdrawparams)结构的*dwRop*成员下描述。

*rgbBack*<br/>
默认情况下，图像背景颜色CLR_DEFAULT。 此参数可以是应用程序定义的 RGB 值或以下值之一：

|“值”|含义|
|-----------|-------------|
|CLR_DEFAULT|默认背景颜色。 使用图像列表背景颜色绘制图像。|
|CLR_NONE|无背景颜色。 图像以透明方式绘制。|

*rgbFore*<br/>
默认情况下，图像前景颜色CLR_DEFAULT。 此参数可以是应用程序定义的 RGB 值或以下值之一：

|“值”|含义|
|-----------|-------------|
|CLR_DEFAULT|默认前景颜色。 使用系统高光颜色作为前景颜色绘制图像。|
|CLR_NONE|无混合颜色。 图像与目标设备上下文的颜色混合。|

仅当*fStyle*包含ILD_BLEND25或ILD_BLEND50标志时，才使用此参数。

*f国家*<br/>
指定绘图状态的标志。 此成员可以包含一个或多个图像列表状态标志。

*Frame*<br/>
影响饱和和 α 混合效果的行为。

当与ILS_SATURATE一起使用时，此成员保留添加到图标中每个像素的 RGB 三重组件的值。

当与ILS_APLHA一起使用时，此成员保留 alpha 通道的值。 此值可以是 0 到 255，0 是完全透明的，255 是完全不透明的。

*crEffect*<br/>
用于发光和阴影效果的[COLORREF](/windows/win32/gdi/colorref)值。

### <a name="return-value"></a>返回值

如果图像成功绘制，则为 TRUE;如果图像已成功绘制，则为 TRUE。否则 FALSE。

### <a name="remarks"></a>备注

如果要自己填充 Win32 结构，请使用第一个版本。 如果要利用一个或多个 MFC 的默认参数，或避免管理结构，请使用第二个版本。

叠加图像是在主图像顶部绘制的图像，由*nImage*参数在此成员函数中指定。 使用["绘制](#draw)"成员函数使用使用[INDEXTOOVERLAYMASK](/windows/win32/api/commctrl/nf-commctrl-indextooverlaymask)宏指定的叠加蒙版的单一索引绘制叠加蒙版。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CImageList#11](../../mfc/reference/codesnippet/cpp/cimagelist-class_10.cpp)]

## <a name="cimagelistenddrag"></a><a name="enddrag"></a>CImageList：结束拖动

调用此函数以结束拖动操作。

```
static void PASCAL EndDrag();
```

### <a name="remarks"></a>备注

要开始拖动操作，`BeginDrag`请使用成员函数。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CImageList#5](../../mfc/reference/codesnippet/cpp/cimagelist-class_11.cpp)]

## <a name="cimagelistextracticon"></a><a name="extracticon"></a>CImage列表：：提取图标

调用此函数可根据图像及其相关蒙版在图像列表中创建图标。

```
HICON ExtractIcon(int nImage);
```

### <a name="parameters"></a>参数

*n图像*<br/>
图像的零基索引。

### <a name="return-value"></a>返回值

如果成功，则处理图标;否则 NULL。

### <a name="remarks"></a>备注

此方法依赖于[ImageList_ExtractIcon](/windows/win32/api/commctrl/nf-commctrl-imagelist_extracticon)宏的行为来创建图标。 有关图标创建和清理的详细信息，请参阅[ImageList_ExtractIcon](/windows/win32/api/commctrl/nf-commctrl-imagelist_extracticon)宏。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CImageList#12](../../mfc/reference/codesnippet/cpp/cimagelist-class_12.cpp)]

## <a name="cimagelistfromhandle"></a><a name="fromhandle"></a>CImageList：从手处理

当为图像列表指定`CImageList`句柄时，返回指向对象的指针。

```
static CImageList* PASCAL FromHandle(HIMAGELIST hImageList);
```

### <a name="parameters"></a>参数

*h图像列表*<br/>
指定图像列表。

### <a name="return-value"></a>返回值

指向`CImageList`对象的指针（如果成功）;如果成功，则指向对象。否则 NULL。

### <a name="remarks"></a>备注

`CImageList`如果 尚未附加到句柄 ， 将创建并附加`CImageList`临时对象。 此临时`CImageList`对象仅在下次应用程序在其事件循环中有空闲时间之前有效，此时将删除所有临时对象。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CImageList#13](../../mfc/reference/codesnippet/cpp/cimagelist-class_13.cpp)]

## <a name="cimagelistfromhandlepermanent"></a><a name="fromhandlepermanent"></a>CImageList：：从永久处理

当为图像列表指定`CImageList`句柄时，返回指向对象的指针。

```
static CImageList* PASCAL FromHandlePermanent(HIMAGELIST hImageList);
```

### <a name="parameters"></a>参数

*h图像列表*<br/>
指定图像列表。

### <a name="return-value"></a>返回值

指向`CImageList`对象的指针（如果成功）;如果成功，则指向对象。否则 NULL。

### <a name="remarks"></a>备注

如果对象`CImageList`未附加到句柄，则返回 NULL。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CImageList#14](../../mfc/reference/codesnippet/cpp/cimagelist-class_14.cpp)]

## <a name="cimagelistgetbkcolor"></a><a name="getbkcolor"></a>CImageList：获取BkColor

调用此函数以检索图像列表的当前背景颜色。

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>返回值

对象背景颜色的`CImageList`RGB 颜色值。

### <a name="example"></a>示例

  请参阅[CImageList 的示例：SetBkColor](#setbkcolor)。

## <a name="cimagelistgetdragimage"></a><a name="getdragimage"></a>CImage列表：：获取拖动图像

获取用于拖动的临时图像列表。

```
static CImageList* PASCAL GetDragImage(
    LPPOINT lpPoint,
    LPPOINT lpPointHotSpot);
```

### <a name="parameters"></a>参数

*lpPoint*<br/>
接收当前拖动位置的[POINT](/windows/win32/api/windef/ns-windef-point)结构的地址。

*lpPointHotSpot*<br/>
`POINT`相对于拖动位置接收拖动图像偏移的结构的地址。

### <a name="return-value"></a>返回值

如果成功，则指向用于拖动的临时图像列表的指针;如果成功，则指向用于拖动的临时图像列表。否则，NULL。

## <a name="cimagelistgetimagecount"></a><a name="getimagecount"></a>CImage列表：获取图像计数

调用此函数以检索图像列表中的图像数。

```
int GetImageCount() const;
```

### <a name="return-value"></a>返回值

图像数。

### <a name="example"></a>示例

  请参阅[CImageList 的示例：：摘要图标](#extracticon)。

## <a name="cimagelistgetimageinfo"></a><a name="getimageinfo"></a>CImageList：获取图片信息

调用此函数以检索有关图像的信息。

```
BOOL GetImageInfo(
    int nImage,
    IMAGEINFO* pImageInfo) const;
```

### <a name="parameters"></a>参数

*n图像*<br/>
图像的零基索引。

*pImageInfo*<br/>
指向接收图像信息的[IMAGEINFO](/windows/win32/api/commctrl/ns-commctrl-imageinfo)结构的指针。 此结构中的信息可用于直接操作图像的位图。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

结构`IMAGEINFO`包含有关图像列表中图像的信息。

## <a name="cimagelistgetsafehandle"></a><a name="getsafehandle"></a>CImageList：：获取安全处理

调用此函数以检索`m_hImageList`数据成员。

```
HIMAGELIST GetSafeHandle() const;
```

### <a name="return-value"></a>返回值

附加图像列表的句柄;句柄否则 NULL，如果没有附加任何对象。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CImageList#15](../../mfc/reference/codesnippet/cpp/cimagelist-class_15.cpp)]

## <a name="cimagelistm_himagelist"></a><a name="m_himagelist"></a>CImageList：m_hImageList

附加到此对象的图像列表的句柄。

`HIMAGELIST m_hImageList;`

### <a name="remarks"></a>备注

数据`m_hImageList`成员是 HIMAGELIST 类型的公共变量。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CImageList#23](../../mfc/reference/codesnippet/cpp/cimagelist-class_16.cpp)]

## <a name="cimagelistoperator-himagelist"></a><a name="operator_himagelist"></a>CImageList：：操作员HIMAGELIST

使用此运算符获取`CImageList`对象的附加句柄。

```
operator HIMAGELIST() const;
```

### <a name="return-value"></a>返回值

如果成功，则对对象表示的图像列表的句柄;`CImageList`如果成功，则对对象表示的图像列表的句柄。否则 NULL。

### <a name="remarks"></a>备注

此运算符是强制转换运算符，支持直接使用 HIMAGELIST 对象。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CImageList#16](../../mfc/reference/codesnippet/cpp/cimagelist-class_17.cpp)]

## <a name="cimagelistread"></a><a name="read"></a>CImageList：阅读

调用此函数从存档中读取图像列表。

```
BOOL Read(CArchive* pArchive);
```

### <a name="parameters"></a>参数

*p存档*<br/>
指向要读取图像`CArchive`列表的对象的指针。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CImageList#18](../../mfc/reference/codesnippet/cpp/cimagelist-class_18.cpp)]

## <a name="cimagelistremove"></a><a name="remove"></a>CImage 列表：：删除

调用此函数以从图像列表对象中删除图像。

```
BOOL Remove(int nImage);
```

### <a name="parameters"></a>参数

*n图像*<br/>
要删除的图像的零索引。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

*nImage*之后的所有项目现在向下移动一个位置。 例如，如果图像列表包含两个项目，删除第一个项将导致其余项现在位于第一个位置。 *nImage*#0 表示第一个位置中的项目。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CImageList#19](../../mfc/reference/codesnippet/cpp/cimagelist-class_19.cpp)]

## <a name="cimagelistreplace"></a><a name="replace"></a>CImageList：替换

调用此函数以将图像列表中的图像替换为新映像。

```
BOOL Replace(
    int nImage,
    CBitmap* pbmImage,
    CBitmap* pbmMask);

int Replace(
    int nImage,
    HICON hIcon);
```

### <a name="parameters"></a>参数

*n图像*<br/>
要替换的图像的零基索引。

*pbmImage*<br/>
指向包含图像的位图的指针。

*pbmMask*<br/>
指向包含掩码的位图的指针。 如果图像列表不使用掩码，则忽略此参数。

*hIcon*<br/>
包含新图像的位图和蒙版的图标的句柄。

### <a name="return-value"></a>返回值

返回 BOOL 的版本返回非零（如果成功）;否则 0。

返回**int**的版本返回图像的零基索引（如果成功）;否则 - 1。

### <a name="remarks"></a>备注

调用[SetImageCount](#setimagecount)后调用此成员函数，将新的有效图像分配给占位符图像索引号。

### <a name="example"></a>示例

  请参阅[CImageList 的示例：：设置图像计数](#setimagecount)。

## <a name="cimagelistsetbkcolor"></a><a name="setbkcolor"></a>CImageList：SetBkColor

调用此函数以设置图像列表的背景颜色。

```
COLORREF SetBkColor(COLORREF cr);
```

### <a name="parameters"></a>参数

*铬*<br/>
要设置的背景颜色。 它可以是CLR_NONE。 在这种情况下，使用蒙版透明地绘制图像。

### <a name="return-value"></a>返回值

如果成功，则上一个背景颜色;否则CLR_NONE。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CImageList#20](../../mfc/reference/codesnippet/cpp/cimagelist-class_20.cpp)]

## <a name="cimagelistsetdragcursorimage"></a><a name="setdragcursorimage"></a>CImageList：：设置DragCursor图像

通过将给定图像（通常是鼠标光标图像）与当前拖动图像相结合，创建新的拖动图像。

```
BOOL SetDragCursorImage(
    int nDrag,
    CPoint ptHotSpot);
```

### <a name="parameters"></a>参数

*nDrag*<br/>
要与拖动图像组合的新图像的索引。

*点热点*<br/>
新图像中热点的位置。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

由于拖动函数在拖动操作期间使用新图像，因此应在调用`CImageList::SetDragCursorImage`后使用 Windows [ShowCursor](/windows/win32/api/winuser/nf-winuser-showcursor)函数隐藏实际鼠标光标。 否则，系统在拖动操作期间可能看起来具有两个鼠标光标。

## <a name="cimagelistsetimagecount"></a><a name="setimagecount"></a>CImage列表：：设置图像计数

调用此成员函数以重置`CImageList`对象中的图像数。

```
BOOL SetImageCount(UINT uNewCount);
```

### <a name="parameters"></a>参数

*uNewCount*<br/>
指定图像列表中的新图像总数的值。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

### <a name="remarks"></a>备注

如果调用此成员函数以增加图像列表中的图像数，则调用每个附加图像的[Replace](#replace)以将新索引分配给有效图像。 如果无法将索引分配给有效图像，则绘制创建新图像的操作将不可预测。

如果使用此功能减小图像列表的大小，则释放截断的图像。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CImageList#21](../../mfc/reference/codesnippet/cpp/cimagelist-class_21.cpp)]

## <a name="cimagelistsetoverlayimage"></a><a name="setoverlayimage"></a>CImageList：：设置叠加图像

调用此函数将图像的零基索引添加到要用作叠加蒙版的图像列表中。

```
BOOL SetOverlayImage(
    int nImage,
    int nOverlay);
```

### <a name="parameters"></a>参数

*n图像*<br/>
图像的零索引，用作叠加蒙版。

*内弗莱*<br/>
叠加蒙版的单基索引。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

最多可以向列表中添加四个索引。

叠加蒙版是在另一个图像上透明绘制的图像。 使用[CImageList：:Draw](#draw)成员函数使用使用 INDEXTOOVERLAYMASK 宏指定的覆盖蒙版的单一索引在图像上绘制叠加蒙版。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CImageList#22](../../mfc/reference/codesnippet/cpp/cimagelist-class_22.cpp)]

## <a name="cimagelistwrite"></a><a name="write"></a>CImageList：写入

调用此函数将图像列表对象写入存档。

```
BOOL Write(CArchive* pArchive);
```

### <a name="parameters"></a>参数

*p存档*<br/>
指向要存储图像`CArchive`列表的对象的指针。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CImageList#17](../../mfc/reference/codesnippet/cpp/cimagelist-class_23.cpp)]

## <a name="see-also"></a>另请参阅

[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CListCtrl 类](../../mfc/reference/clistctrl-class.md)<br/>
[CTabCtrl 类](../../mfc/reference/ctabctrl-class.md)
