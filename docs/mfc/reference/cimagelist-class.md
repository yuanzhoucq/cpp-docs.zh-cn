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
ms.openlocfilehash: 2fc92858f84826e2b953fcbc9de020741e97b007
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62346361"
---
# <a name="cimagelist-class"></a>CImageList 类

提供 Windows 公共图像列表控件的功能。

## <a name="syntax"></a>语法

```
class CImageList : public CObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CImageList::CImageList](#cimagelist)|构造 `CImageList` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CImageList::Add](#add)|将图像添加到图像列表。|
|[CImageList::Attach](#attach)|将附加到图像列表`CImageList`对象。|
|[CImageList::BeginDrag](#begindrag)|开始拖动图像。|
|[CImageList::Copy](#copy)|将复制内的图像`CImageList`对象。|
|[CImageList::Create](#create)|初始化图像列表，并将其附加到`CImageList`对象。|
|[CImageList::DeleteImageList](#deleteimagelist)|删除图像列表。|
|[CImageList::DeleteTempMap](#deletetempmap)|调用[CWinApp](../../mfc/reference/cwinapp-class.md)空闲时间处理程序以删除任何临时`CImageList`对象创建的`FromHandle`。|
|[CImageList::Detach](#detach)|从图像列表对象中分离`CImageList`对象并返回的句柄的图像列表。|
|[CImageList::DragEnter](#dragenter)|在拖动操作期间锁定更新并显示在指定位置处拖动图像。|
|[CImageList::DragLeave](#dragleave)|解锁窗口并隐藏拖动图像，以便该窗口可以更新。|
|[CImageList::DragMove](#dragmove)|将图像拖放操作期间所拖动的移动。|
|[CImageList::DragShowNolock](#dragshownolock)|显示或在拖动操作中，而无需锁定在窗口隐藏拖动图像。|
|[CImageList::Draw](#draw)|绘制正被拖动拖放操作期间的图像。|
|[CImageList::DrawEx](#drawex)|在指定的设备上下文中绘制的图像列表项。 该函数使用指定的绘制样式，并结合使用指定的颜色的图像。|
|[CImageList::DrawIndirect](#drawindirect)|从图像列表绘制图像。|
|[CImageList::EndDrag](#enddrag)|结束拖动操作。|
|[CImageList::ExtractIcon](#extracticon)|创建基于的图像和掩码图像列表中的图标。|
|[CImageList::FromHandle](#fromhandle)|返回一个指向`CImageList`对象在给定一个句柄到图像列表。 如果 `CImageList` 对象未附加到该句柄，则会创建并附加一个临时 `CImageList` 对象。|
|[CImageList::FromHandlePermanent](#fromhandlepermanent)|返回一个指向`CImageList`对象在给定一个句柄到图像列表。 如果`CImageList`对象未附加到该句柄，则返回 NULL。|
|[CImageList::GetBkColor](#getbkcolor)|检索图像列表的当前背景色。|
|[CImageList::GetDragImage](#getdragimage)|获取用于拖动的临时图像列表。|
|[CImageList::GetImageCount](#getimagecount)|检索图像列表中的映像数。|
|[CImageList::GetImageInfo](#getimageinfo)|检索有关映像的信息。|
|[CImageList::GetSafeHandle](#getsafehandle)|检索`m_hImageList`。|
|[CImageList::Read](#read)|从存档中读取图像列表。|
|[CImageList::Remove](#remove)|从图像列表中移除图像。|
|[CImageList::Replace](#replace)|图像列表中的图像替换为新图像。|
|[CImageList::SetBkColor](#setbkcolor)|设置图像列表的背景色。|
|[CImageList::SetDragCursorImage](#setdragcursorimage)|创建一个新的拖动图像。|
|[CImageList::SetImageCount](#setimagecount)|重置图像列表中的图像的计数。|
|[CImageList::SetOverlayImage](#setoverlayimage)|将图像的从零开始的索引添加到映像用作覆盖掩码的列表。|
|[CImageList::Write](#write)|将图像列表写入到存档。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CImageList::operator HIMAGELIST](#operator_himagelist)|返回 HIMAGELIST 附加到`CImageList`。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CImageList::m_hImageList](#m_himagelist)|一个包含附加到此对象的图像列表的句柄。|

## <a name="remarks"></a>备注

"图像列表"是相同大小的图像，其中每个可以按其从零开始的索引引用的集合。 图像列表用于有效地管理大的图标或位图集。 图像列表中的所有映像都包含在单一、 宽位图以屏幕设备格式。 图像列表可能包含一个单色位图，该位图包含用于透明地绘制图像的蒙板（图标样式）。 Microsoft Win32 应用程序编程接口 (API) 提供了可用于绘制图像、 创建和销毁图像列表、 添加和删除映像、 替换图像、 合并图像以及拖动图像的图像列表函数。

此控件 (并因此`CImageList`类) 仅适用于 Windows 95/98 和 Windows NT 版本 3.51 下运行的程序和更高版本。

有关使用的详细信息`CImageList`，请参阅[控件](../../mfc/controls-mfc.md)并[使用 CImageList](../../mfc/using-cimagelist.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CImageList`

## <a name="requirements"></a>要求

**标头：** afxcmn.h

##  <a name="add"></a>  CImageList::Add

调用此函数可将一个或多个图像或图标添加到图像列表。

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
指向包含的图像的位图。 位图的宽度推断的映像数量。

*pbmMask*<br/>
指向包含掩码的位图。 如果未应用蒙板的图像列表一起使用，则忽略此参数。

*crMask*<br/>
用于生成掩码的颜色。 此颜色在指定位图中的每个像素更改为黑色和相应的位掩码中设置为一个。

*hIcon*<br/>
包含位图和掩码为新映像的图标的句柄。

### <a name="return-value"></a>返回值

如果成功，则第一个的新图像的从零开始的索引否则为-1。

### <a name="remarks"></a>备注

你负责其完成时释放图标句柄。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CImageList#1](../../mfc/reference/codesnippet/cpp/cimagelist-class_1.cpp)]

##  <a name="attach"></a>  CImageList::Attach

调用此函数可将附加到图像列表`CImageList`对象。

```
BOOL Attach(HIMAGELIST hImageList);
```

### <a name="parameters"></a>参数

*hImageList*<br/>
图像列表对象的句柄。

### <a name="return-value"></a>返回值

如果附加成功，则非零值否则为 0。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CImageList#2](../../mfc/reference/codesnippet/cpp/cimagelist-class_2.cpp)]

##  <a name="begindrag"></a>  CImageList::BeginDrag

调用此函数可开始拖动图像。

```
BOOL BeginDrag(
    int nImage,
    CPoint ptHotSpot);
```

### <a name="parameters"></a>参数

*nImage*<br/>
要拖动的图像的从零开始的索引。

*ptHotSpot*<br/>
开始拖动位置 （通常情况下，光标位置） 的坐标。 坐标是相对于图像的左上角。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

此函数会创建用于拖动临时图像列表。 图像将指定的图像和其掩码与当前游标结合起来。 在后续 WM_MOUSEMOVE 消息响应，您可以通过使用移动拖动图像`DragMove`成员函数。 若要结束拖动操作，可以使用`EndDrag`成员函数。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CImageList#3](../../mfc/reference/codesnippet/cpp/cimagelist-class_3.cpp)]

##  <a name="cimagelist"></a>  CImageList::CImageList

构造 `CImageList` 对象。

```
CImageList();
```

##  <a name="copy"></a>  CImageList::Copy

此成员函数可实现 Win32 函数的行为[ImageList_Copy](/windows/desktop/api/commctrl/nf-commctrl-imagelist_copy)，如 Windows SDK 中所述。

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
要用作目标的复制操作的图像的从零开始的索引。

*iSrc*<br/>
要作为复制操作的源使用的图像的从零开始的索引。

*uFlags*<br/>
用于指定要进行的复制操作的类型的位标志值。 此参数可以是下列值之一：

|“值”|含义|
|-----------|-------------|
|ILCF_MOVE|源映像复制到目标图像的索引。 此操作会导致给定图像的多个实例。 默认值为 ILCF_MOVE。|
|ILCF_SWAP|源和目标图像交换内的图像列表的位置。|

*pSrc*<br/>
一个指向`CImageList`目标的复制操作的对象。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CImageList#6](../../mfc/reference/codesnippet/cpp/cimagelist-class_4.cpp)]

##  <a name="create"></a>  CImageList::Create

初始化图像列表，并将其附加到[CImageList](../../mfc/reference/cimagelist-class.md)对象。

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

*cx*<br/>
维度的每个映像，以像素为单位。

*cy*<br/>
维度的每个映像，以像素为单位。

*nFlags*<br/>
指定要创建图像列表的类型。 此参数可以是以下值的组合，但它可以包括只有一个`ILC_COLOR`值。

|“值”|含义|
|-----------|-------------|
|ILC_COLOR|如果指定任何其他 ILC_COLOR * 标志时，请使用默认行为。 通常情况下，默认值是 ILC_COLOR4;但对于较旧的显示器驱动程序，默认值是 ILC_COLORDDB。|
|ILC_COLOR4|使用 4 位 （16 种颜色） 与设备无关位图 (DIB) 部分作为位图图像列表。|
|ILC_COLOR8|使用 8 位 DIB 部分。 用于颜色表的颜色是半色调调色板为相同的颜色。|
|ILC_COLOR16|使用 16 位 (32/64 k 颜色) DIB 部分。|
|ILC_COLOR24|使用 24 位 DIB 部分。|
|ILC_COLOR32|使用 32 位 DIB 部分。|
|ILC_COLORDDB|使用依赖于设备的位图。|
|ILC_MASK|使用掩码。 图像列表包含两个位图，其中之一是用作掩码的单色位图。 如果不包括此值，则图像列表包含了一个位图。 请参阅[从图像列表绘制图像](../../mfc/drawing-images-from-an-image-list.md)屏蔽映像上的其他信息。|

*nInitial*<br/>
图像列表最初包含的映像数量。

*nGrow*<br/>
图像列表可以按其增长时系统需要重新调整大小以容纳新映像的列表的图像数量。 此参数表示调整大小的图像列表可以包含新映像的数量。

*nBitmapID*<br/>
资源 Id 的位图图像列表与相关联。

*crMask*<br/>
用于生成掩码的颜色。 指定位图中此颜色的每个像素更改为黑色和相应的位掩码中设置为一个。

*lpszBitmapID*<br/>
包含资源的映像 Id 的字符串。

*imagelist1*<br/>
对 `CImageList` 对象的引用。

*nImage1*<br/>
第一个现有图像的索引。

*imagelist2*<br/>
对 `CImageList` 对象的引用。

*nImage2*<br/>
第二个现有图像的索引。

*dx*<br/>
与第一个映像，以像素为单位的关系中的第二个图像的 x 轴的偏移量。

*dy*<br/>
与第一个映像，以像素为单位的关系中的第二个图像的 y 轴的偏移量。

*pImageList*<br/>
指向 `CImageList` 对象的指针。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

构造`CImageList`中两个步骤。 首先，调用构造函数，然后调用`Create`，它创建图像列表并将其附加到`CImageList`对象。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CImageList#7](../../mfc/reference/codesnippet/cpp/cimagelist-class_5.cpp)]

##  <a name="deleteimagelist"></a>  CImageList::DeleteImageList

调用此函数可删除图像列表。

```
BOOL DeleteImageList();
```

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CImageList#8](../../mfc/reference/codesnippet/cpp/cimagelist-class_6.cpp)]

##  <a name="deletetempmap"></a>  CImageList::DeleteTempMap

自动调用`CWinApp`空闲时间处理程序`DeleteTempMap`删除临时`CImageList`创建的对象[FromHandle](#fromhandle)，但不会销毁任何句柄 ( `hImageList`) 暂时关联使用`ImageList`对象。

```
static void PASCAL DeleteTempMap();
```

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CImageList#9](../../mfc/reference/codesnippet/cpp/cimagelist-class_7.cpp)]

##  <a name="detach"></a>  CImageList::Detach

调用此函数可分离从图像列表对象`CImageList`对象。

```
HIMAGELIST Detach();
```

### <a name="return-value"></a>返回值

图像列表对象的句柄。

### <a name="remarks"></a>备注

此函数返回的句柄的图像列表对象。

### <a name="example"></a>示例

  有关示例，请参阅[CImageList::Attach](#attach)。

##  <a name="dragenter"></a>  CImageList::DragEnter

在拖动操作中，锁定指定的窗口内容的最新更新*pWndLock* ，并显示在指定的位置拖动图像*点*。

```
static BOOL PASCAL DragEnter(
    CWnd* pWndLock,
    CPoint point);
```

### <a name="parameters"></a>参数

*pWndLock*<br/>
对拥有拖动图像的窗口的指针。

*point*<br/>
要显示拖动图像的位置。 坐标都相对于窗口 （而不是工作区） 的左上角。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

坐标是相对于窗口的左上角，因此您必须补偿窗口元素，如边框、 标题栏和菜单栏的宽度时指定的坐标。

如果*pWndLock*为 NULL，此函数与在桌面窗口关联的显示上下文中绘制的图像和坐标都相对于屏幕左上角。

此函数会在拖动操作期间锁定给定窗口的所有其他更新。 如果你需要执行任何绘图在拖动操作，例如，突出显示拖放操作的目标可以通过使用临时隐藏拖动的图像[CImageList::DragLeave](#dragleave)函数。

### <a name="example"></a>示例

  有关示例，请参阅[CImageList::BeginDrag](#begindrag)。

##  <a name="dragleave"></a>  CImageList::DragLeave

解锁指定的窗口*pWndLock*并隐藏拖动图像，允许更新窗口。

```
static BOOL PASCAL DragLeave(CWnd* pWndLock);
```

### <a name="parameters"></a>参数

*pWndLock*<br/>
对拥有拖动图像的窗口的指针。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="example"></a>示例

  有关示例，请参阅[CImageList::EndDrag](#enddrag)。

##  <a name="dragmove"></a>  CImageList::DragMove

调用此函数可将正被拖动拖放操作期间的图像。

```
static BOOL PASCAL DragMove(CPoint pt);
```

### <a name="parameters"></a>参数

*pt*<br/>
新的拖动位置。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

通常以响应 WM_MOUSEMOVE 消息时调用此函数。 若要开始拖动操作，请使用`BeginDrag`成员函数。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CImageList#4](../../mfc/reference/codesnippet/cpp/cimagelist-class_8.cpp)]

##  <a name="dragshownolock"></a>  CImageList::DragShowNolock

显示或在拖动操作中，而无需锁定在窗口隐藏拖动图像。

```
static BOOL PASCAL DragShowNolock(BOOL bShow);
```

### <a name="parameters"></a>参数

*bShow*<br/>
指定是否要显示拖动图像。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

[CImageList::DragEnter](#dragenter)函数在拖动操作期间会锁定到窗口的所有更新。 此函数，但是，不会锁定该窗口。

##  <a name="draw"></a>  CImageList::Draw

调用此函数可绘制拖放操作期间正被拖动图像。

```
BOOL Draw(
    CDC* pDC,
    int nImage,
    POINT pt,
    UINT nStyle);
```

### <a name="parameters"></a>参数

*pDC*<br/>
指向目标设备上下文指针。

*nImage*<br/>
要绘制的图像的从零开始的索引。

*pt*<br/>
在其中绘制指定的设备上下文中的位置。

*nStyle*<br/>
标志，指定的绘制样式。 它可以是一个或多个值：

|“值”|含义|
|-----------|-------------|
|ILD_BLEND25 ILD_FOCUS|绘制图像，混合系统突出显示颜色的 25%。 如果图像列表不包含一个掩码，则此值无效。|
|ILD_BLEND50, ILD_SELECTED, ILD_BLEND|绘制图像，混合系统突出显示颜色的 50%。 如果图像列表不包含一个掩码，则此值无效。|
|ILD_MASK|绘制掩码。|
|ILD_NORMAL|绘制图像的图像列表中使用的背景色。 如果背景色为 CLR_NONE 值，以透明方式使用掩码绘制图像。|
|ILD_TRANSPARENT|使用绘制的图像以透明方式的掩码，而不考虑的背景色。|

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="example"></a>示例

  有关示例，请参阅[cimagelist:: Setoverlayimage](#setoverlayimage)。

##  <a name="drawex"></a>  CImageList::DrawEx

在指定的设备上下文中绘制的图像列表项。

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
指向目标设备上下文指针。

*nImage*<br/>
要绘制的图像的从零开始的索引。

*pt*<br/>
在其中绘制指定的设备上下文中的位置。

*sz*<br/>
相对于图像的左上角绘制图像的部分的大小。 请参阅*dx*并*dy*中[ImageList_DrawEx](/windows/desktop/api/commctrl/nf-commctrl-imagelist_drawex) Windows SDK 中。

*clrBk*<br/>
图像的背景色。 请参阅*rgbBk*中[ImageList_DrawEx](/windows/desktop/api/commctrl/nf-commctrl-imagelist_drawex) Windows SDK 中。

*clrFg*<br/>
图像的前景色。 请参阅*rgbFg*中[ImageList_DrawEx](/windows/desktop/api/commctrl/nf-commctrl-imagelist_drawex) Windows SDK 中。

*nStyle*<br/>
标志，指定的绘制样式。 请参阅*fStyle*中[ImageList_DrawEx](/windows/desktop/api/commctrl/nf-commctrl-imagelist_drawex) Windows SDK 中。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

该函数使用指定的绘制样式，并结合使用指定的颜色的图像。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CImageList#10](../../mfc/reference/codesnippet/cpp/cimagelist-class_9.cpp)]

##  <a name="drawindirect"></a>  CImageList::DrawIndirect

调用此成员函数以从图像列表绘制图像。

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

*pimldp*<br/>
一个指向[2&AMP;GT;IMAGELISTDRAWPARAMS&AMP;LT;2](/windows/desktop/api/commctrl/ns-commctrl-_imagelistdrawparams)结构，其中包含与绘制操作有关的信息。

*pDC*<br/>
指向目标设备上下文的指针。 必须删除这[CDC](../../mfc/reference/cdc-class.md)对象都完成。

*nImage*<br/>
要绘制的图像的从零开始的索引。

*pt*<br/>
一个[点](/previous-versions/dd162805\(v=vs.85\))结构，它包含 x 坐标和 y 坐标绘制图像的位置。

*sz*<br/>
一个[大小](/windows/desktop/api/windef/ns-windef-tagsize)结构，指示要绘制的图像的大小。

*ptOrigin*<br/>
一个[点](/previous-versions/dd162805\(v=vs.85\))结构，它包含 x 坐标和 y 坐标指定相对于映像自身绘制操作的左上的角。 不绘制左侧的 x 坐标和 y 坐标上面的图像的像素。

*fStyle*<br/>
标志，指定的绘制样式和覆盖层图像 （可选）。 上覆盖图像，请参阅备注部分的信息。 MFC 默认实现，ILD_NORMAL，绘制图像的图像列表中使用的背景色。 如果背景色为 CLR_NONE 值，以透明方式使用掩码绘制图像。

其他可能的样式下所述*fStyle*的成员[2&AMP;GT;IMAGELISTDRAWPARAMS&AMP;LT;2](/windows/desktop/api/commctrl/ns-commctrl-_imagelistdrawparams)结构。

*dwRop*<br/>
值，该值指定光栅操作代码。 这些代码定义源矩形的颜色数据与目标矩形来实现的最终颜色的颜色数据组合的方式。 MFC 的默认实现，SRCCOPY，将源矩形复制直接到目标矩形。 如果忽略此参数*fStyle*参数不包括 ILD_ROP 标志。

其他可能的值下所述*dwRop*的成员[2&AMP;GT;IMAGELISTDRAWPARAMS&AMP;LT;2](/windows/desktop/api/commctrl/ns-commctrl-_imagelistdrawparams)结构。

*rgbBack*<br/>
图像背景色，默认情况下 CLR_DEFAULT。 此参数可以是应用程序定义的 RGB 值或以下值之一：

|“值”|含义|
|-----------|-------------|
|CLR_DEFAULT|默认背景色。 使用图像列表的背景色绘制图像。|
|CLR_NONE|无背景色。 透明地绘制图像。|

*rgbFore*<br/>
映像前景色，默认情况下 CLR_DEFAULT。 此参数可以是应用程序定义的 RGB 值或以下值之一：

|“值”|含义|
|-----------|-------------|
|CLR_DEFAULT|默认前景色。 使用系统突出显示颜色作为前景色绘制图像。|
|CLR_NONE|没有 blend 颜色。 图像与目标设备上下文的颜色混合。|

仅当使用此参数*fStyle*包括 ILD_BLEND25 或 ILD_BLEND50 标志。

*fState*<br/>
标志，指定绘制的状态。 此成员可以包含一个或多个图像列表状态标志。

*框架*<br/>
影响 saturate 和 alpha 值混合处理效果的行为。

当与 ILS_SATURATE 一起使用，此成员将保留添加到每个像素图标中的 RGB 三元数组的每个颜色组件的值。

当与 ILS_APLHA 一起使用，此成员将保留 alpha 通道值。 此值可以介于 0 到 255，0 表示完全透明，255 完全不透明。

*crEffect*<br/>
一个[COLORREF](/windows/desktop/gdi/colorref)值，该值用于发光和阴影效果。

### <a name="return-value"></a>返回值

如果成功地绘制图像; 则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

如果你想要自己填充 Win32 结构，使用的第一个版本。 如果你想要充分利用一个或多个 MFC 的默认自变量，或避免管理这种结构，请使用第二个版本。

覆盖图像是在通过此成员函数中指定的主图像之上绘制的图像*nImage*参数。 使用绘制覆盖掩码[绘制](#draw)成员函数使用指定覆盖掩码的基于 1 的索引[INDEXTOOVERLAYMASK](/windows/desktop/api/commctrl/nf-commctrl-indextooverlaymask)宏。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CImageList#11](../../mfc/reference/codesnippet/cpp/cimagelist-class_10.cpp)]

##  <a name="enddrag"></a>  CImageList::EndDrag

调用此函数以结束拖动操作。

```
static void PASCAL EndDrag();
```

### <a name="remarks"></a>备注

若要开始拖动操作，请使用`BeginDrag`成员函数。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CImageList#5](../../mfc/reference/codesnippet/cpp/cimagelist-class_11.cpp)]

##  <a name="extracticon"></a>  CImageList::ExtractIcon

调用此函数可创建基于图像和图像列表中的其相关的掩码中的图标。

```
HICON ExtractIcon(int nImage);
```

### <a name="parameters"></a>参数

*nImage*<br/>
图像的从零开始索引。

### <a name="return-value"></a>返回值

如果成功，则该图标的句柄否则为，为 NULL。

### <a name="remarks"></a>备注

此方法依赖的行为[ImageList_ExtractIcon](/windows/desktop/api/commctrl/nf-commctrl-imagelist_extracticon)宏来创建图标。 请参阅[ImageList_ExtractIcon](/windows/desktop/api/commctrl/nf-commctrl-imagelist_extracticon)图标创建和清理的详细信息的宏。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CImageList#12](../../mfc/reference/codesnippet/cpp/cimagelist-class_12.cpp)]

##  <a name="fromhandle"></a>  CImageList::FromHandle

返回一个指向`CImageList`对象在给定一个句柄到图像列表。

```
static CImageList* PASCAL FromHandle(HIMAGELIST hImageList);
```

### <a name="parameters"></a>参数

*hImageList*<br/>
指定的图像列表。

### <a name="return-value"></a>返回值

一个指向`CImageList`如果成功，否则该值为 NULL 的对象。

### <a name="remarks"></a>备注

如果`CImageList`尚未附加到句柄，临时`CImageList`创建并附加对象。 此临时`CImageList`对象仅用于有效直到下一次应用程序在其事件循环内有空闲时间，此时所有临时对象会被删除。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CImageList#13](../../mfc/reference/codesnippet/cpp/cimagelist-class_13.cpp)]

##  <a name="fromhandlepermanent"></a>  CImageList::FromHandlePermanent

返回一个指向`CImageList`对象在给定一个句柄到图像列表。

```
static CImageList* PASCAL FromHandlePermanent(HIMAGELIST hImageList);
```

### <a name="parameters"></a>参数

*hImageList*<br/>
指定的图像列表。

### <a name="return-value"></a>返回值

一个指向`CImageList`如果成功，否则该值为 NULL 的对象。

### <a name="remarks"></a>备注

如果`CImageList`对象未附加到该句柄，则返回 NULL。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CImageList#14](../../mfc/reference/codesnippet/cpp/cimagelist-class_14.cpp)]

##  <a name="getbkcolor"></a>  CImageList::GetBkColor

调用此函数可检索图像列表的当前背景色。

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>返回值

RGB 颜色值的`CImageList`对象背景色。

### <a name="example"></a>示例

  有关示例，请参阅[CImageList::SetBkColor](#setbkcolor)。

##  <a name="getdragimage"></a>  CImageList::GetDragImage

获取用于拖动的临时图像列表。

```
static CImageList* PASCAL GetDragImage(
    LPPOINT lpPoint,
    LPPOINT lpPointHotSpot);
```

### <a name="parameters"></a>参数

*lpPoint*<br/>
地址[点](/previous-versions/dd162805\(v=vs.85\))结构，它接收当前拖动位置。

*lpPointHotSpot*<br/>
地址`POINT`接收拖动图像相对于拖动位置的偏移量的结构。

### <a name="return-value"></a>返回值

如果成功，指向临时图像的列表，用于拖动;否则，为 NULL。

##  <a name="getimagecount"></a>  CImageList::GetImageCount

调用此函数可检索的图像列表中的映像数量。

```
int GetImageCount() const;
```

### <a name="return-value"></a>返回值

映像数量。

### <a name="example"></a>示例

  有关示例，请参阅[CImageList::ExtractIcon](#extracticon)。

##  <a name="getimageinfo"></a>  CImageList::GetImageInfo

调用此函数可检索有关映像的信息。

```
BOOL GetImageInfo(
    int nImage,
    IMAGEINFO* pImageInfo) const;
```

### <a name="parameters"></a>参数

*nImage*<br/>
图像的从零开始索引。

*pImageInfo*<br/>
指向[IMAGEINFO](/windows/desktop/api/commctrl/ns-commctrl-_imageinfo)结构，它接收有关映像的信息。 此结构中的信息可以用于直接操作图像的位图。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

`IMAGEINFO`结构包含有关图像列表中的映像的信息。

##  <a name="getsafehandle"></a>  CImageList::GetSafeHandle

调用此函数可检索`m_hImageList`数据成员。

```
HIMAGELIST GetSafeHandle() const;
```

### <a name="return-value"></a>返回值

句柄附加的图像列表中;如果连接没有任何对象，否则为 NULL。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CImageList#15](../../mfc/reference/codesnippet/cpp/cimagelist-class_15.cpp)]

##  <a name="m_himagelist"></a>  CImageList::m_hImageList

附加到此对象的图像列表的句柄。

`HIMAGELIST m_hImageList;`

### <a name="remarks"></a>备注

`m_hImageList`数据成员是类型 HIMAGELIST 的公共变量。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CImageList#23](../../mfc/reference/codesnippet/cpp/cimagelist-class_16.cpp)]

##  <a name="operator_himagelist"></a>  CImageList::operator HIMAGELIST

此运算符用于获取附加的句柄`CImageList`对象。

```
operator HIMAGELIST() const;
```

### <a name="return-value"></a>返回值

如果成功，句柄的图像列表表示为`CImageList`对象; 否则为 NULL。

### <a name="remarks"></a>备注

此运算符是强制转换运算符，支持直接使用 HIMAGELIST 对象。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CImageList#16](../../mfc/reference/codesnippet/cpp/cimagelist-class_17.cpp)]

##  <a name="read"></a>  CImageList::Read

调用此函数可从存档中读取图像列表。

```
BOOL Read(CArchive* pArchive);
```

### <a name="parameters"></a>参数

*pArchive*<br/>
一个指向`CArchive`对象，为要读取的图像列表。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CImageList#18](../../mfc/reference/codesnippet/cpp/cimagelist-class_18.cpp)]

##  <a name="remove"></a>  CImageList::Remove

调用此函数可从图像列表对象中删除映像。

```
BOOL Remove(int nImage);
```

### <a name="parameters"></a>参数

*nImage*<br/>
要移除的图像的从零开始的索引。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

后面的所有项*nImage*现在将下移一个位置。 例如，如果图像列表包含两个项，则删除的第一项将导致剩余的项现在位于第一个位置。 *nImage*= 0 中的第一个位置的项。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CImageList#19](../../mfc/reference/codesnippet/cpp/cimagelist-class_19.cpp)]

##  <a name="replace"></a>  CImageList::Replace

调用此函数将图像列表中的映像替换为新映像。

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

*nImage*<br/>
要替换的图像的从零开始的索引。

*pbmImage*<br/>
指向包含的图像的位图的指针。

*pbmMask*<br/>
指向包含掩码的位图的指针。 如果未应用蒙板的图像列表一起使用，则忽略此参数。

*hIcon*<br/>
一个包含位图和掩码为新映像的图标的句柄。

### <a name="return-value"></a>返回值

返回非零，如果成功，则返回布尔值的版本否则为 0。

返回的版本**int**返回图像的从零开始的索引; 如果成功; 否则为-1。

### <a name="remarks"></a>备注

调用后调用此成员函数[SetImageCount](#setimagecount)要分配给新，有效图像占位符映像的索引编号。

### <a name="example"></a>示例

  有关示例，请参阅[CImageList::SetImageCount](#setimagecount)。

##  <a name="setbkcolor"></a>  CImageList::SetBkColor

调用此函数可设置图像列表的背景色。

```
COLORREF SetBkColor(COLORREF cr);
```

### <a name="parameters"></a>参数

*cr*<br/>
若要设置的背景色。 它可以是 CLR_NONE。 在这种情况下，以透明方式使用掩码绘制图像。

### <a name="return-value"></a>返回值

如果成功，则以前的背景颜色否则为 CLR_NONE。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CImageList#20](../../mfc/reference/codesnippet/cpp/cimagelist-class_20.cpp)]

##  <a name="setdragcursorimage"></a>  CImageList::SetDragCursorImage

通过组合给定的图像 （通常是鼠标光标图像） 与当前拖动图像来创建一个新的拖动图像。

```
BOOL SetDragCursorImage(
    int nDrag,
    CPoint ptHotSpot);
```

### <a name="parameters"></a>参数

*nDrag*<br/>
要结合拖动图像的新图像的索引。

*ptHotSpot*<br/>
新的映像内的作用点的位置。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

由于拖动函数在拖动操作过程中使用新映像，应使用 Windows [ShowCursor](/windows/desktop/api/winuser/nf-winuser-showcursor)函数来调用后隐藏实际鼠标光标`CImageList::SetDragCursorImage`。 否则，系统在拖动操作期间可能看起来具有两个鼠标光标。

##  <a name="setimagecount"></a>  CImageList::SetImageCount

调用此成员函数以重置中的图像数`CImageList`对象。

```
BOOL SetImageCount(UINT uNewCount);
```

### <a name="parameters"></a>参数

*uNewCount*<br/>
图像列表中指定新的映像总数的值。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

### <a name="remarks"></a>备注

如果调用此成员函数以增加的图像列表中的映像数量，然后调用[替换为](#replace)的每个其他映像要将新的索引分配到有效的图像。 如果您不能将索引分配到有效的图像，描述创建新的映像的操作将是不可预测。

如果使用此函数减小图像列表的大小，会释放已截断的映像。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CImageList#21](../../mfc/reference/codesnippet/cpp/cimagelist-class_21.cpp)]

##  <a name="setoverlayimage"></a>  CImageList::SetOverlayImage

调用此函数可将图像的从零开始的索引添加到映像用作覆盖掩码的列表。

```
BOOL SetOverlayImage(
    int nImage,
    int nOverlay);
```

### <a name="parameters"></a>参数

*nImage*<br/>
要用作覆盖掩码的图像的从零开始的索引。

*nOverlay*<br/>
覆盖掩码的基于 1 的索引。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

最多四个索引可以被添加到列表。

覆盖掩码是另一个图像上透明绘制的图像。 使用图像上绘制覆盖掩码[cimagelist:: Draw](#draw)成员函数具有一个基于使用 INDEXTOOVERLAYMASK 宏指定覆盖掩码的索引。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CImageList#22](../../mfc/reference/codesnippet/cpp/cimagelist-class_22.cpp)]

##  <a name="write"></a>  CImageList::Write

调用此函数将图像列表对象写入存档。

```
BOOL Write(CArchive* pArchive);
```

### <a name="parameters"></a>参数

*pArchive*<br/>
一个指向`CArchive`对象是用来存储图像列表。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CImageList#17](../../mfc/reference/codesnippet/cpp/cimagelist-class_23.cpp)]

## <a name="see-also"></a>请参阅

[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CListCtrl 类](../../mfc/reference/clistctrl-class.md)<br/>
[CTabCtrl 类](../../mfc/reference/ctabctrl-class.md)
