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
ms.openlocfilehash: 6c419081a649fddd65120270decb0cb57ee743fa
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916189"
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
|[CImageList::Add](#add)|向图像列表添加图像或图像。|
|[CImageList::Attach](#attach)|将图像列表附加到`CImageList`对象。|
|[CImageList::BeginDrag](#begindrag)|开始拖动图像。|
|[CImageList::Copy](#copy)|复制`CImageList`对象中的图像。|
|[CImageList::Create](#create)|初始化图像列表, 并将其附加到`CImageList`对象。|
|[CImageList::DeleteImageList](#deleteimagelist)|删除图像列表。|
|[CImageList::DeleteTempMap](#deletetempmap)|由[CWinApp](../../mfc/reference/cwinapp-class.md)空闲时间处理程序调用, 以删除由创建`CImageList`的`FromHandle`任何临时对象。|
|[CImageList::Detach](#detach)|从`CImageList`对象分离图像列表对象并返回图像列表的句柄。|
|[CImageList::DragEnter](#dragenter)|在拖动操作过程中锁定更新, 并在指定位置显示拖动图像。|
|[CImageList::DragLeave](#dragleave)|解锁窗口并隐藏拖动图像, 以便可以更新窗口。|
|[CImageList::DragMove](#dragmove)|在拖放操作过程中移动正在拖动的图像。|
|[CImageList::DragShowNolock](#dragshownolock)|在拖动操作期间显示或隐藏拖动图像, 而不锁定窗口。|
|[CImageList::Draw](#draw)|绘制拖放操作过程中正在拖动的图像。|
|[CImageList::DrawEx](#drawex)|在指定的设备上下文中绘制图像列表项。 函数使用指定的绘制样式, 并将图像与指定的颜色混合。|
|[CImageList::DrawIndirect](#drawindirect)|从图像列表绘制图像。|
|[CImageList::EndDrag](#enddrag)|结束拖动操作。|
|[CImageList::ExtractIcon](#extracticon)|基于图像列表中的图像和掩码创建图标。|
|[CImageList::FromHandle](#fromhandle)|当给定图像列表的`CImageList`句柄时, 返回指向对象的指针。 如果 `CImageList` 对象未附加到该句柄，则会创建并附加一个临时 `CImageList` 对象。|
|[CImageList::FromHandlePermanent](#fromhandlepermanent)|当给定图像列表的`CImageList`句柄时, 返回指向对象的指针。 `CImageList`如果对象未附加到句柄, 则返回 NULL。|
|[CImageList::GetBkColor](#getbkcolor)|检索图像列表的当前背景色。|
|[CImageList::GetDragImage](#getdragimage)|获取用于拖动的临时图像列表。|
|[CImageList::GetImageCount](#getimagecount)|检索图像列表中的图像数量。|
|[CImageList::GetImageInfo](#getimageinfo)|检索有关映像的信息。|
|[CImageList::GetSafeHandle](#getsafehandle)|检索`m_hImageList`。|
|[CImageList::Read](#read)|从存档中读取图像列表。|
|[CImageList::Remove](#remove)|从图像列表中移除图像。|
|[CImageList::Replace](#replace)|使用新图像替换图像列表中的图像。|
|[CImageList::SetBkColor](#setbkcolor)|设置图像列表的背景色。|
|[CImageList::SetDragCursorImage](#setdragcursorimage)|创建新的拖动图像。|
|[CImageList::SetImageCount](#setimagecount)|重置图像列表中的图像计数。|
|[CImageList::SetOverlayImage](#setoverlayimage)|将图像的从零开始的索引添加到要用作覆盖蒙板的图像的列表。|
|[CImageList::Write](#write)|将图像列表写入存档。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CImageList:: operator HIMAGELIST](#operator_himagelist)|返回附加到的`CImageList`HIMAGELIST。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CImageList::m_hImageList](#m_himagelist)|包含附加到此对象的图像列表的句柄。|

## <a name="remarks"></a>备注

"图像列表" 是大小相同的图像的集合, 每个图像都可以通过其从零开始的索引来引用。 图像列表用于有效地管理大的图标或位图集。 图像列表中的所有图像都包含在屏幕设备格式的单个宽位图中。 图像列表可能包含一个单色位图，该位图包含用于透明地绘制图像的蒙板（图标样式）。 Microsoft Win32 应用程序编程接口 (API) 提供了图像列表功能, 使你能够绘制图像、创建和销毁图像列表、添加和删除图像、替换图像、合并图像和拖动图像。

此控件 (因而`CImageList`类) 仅适用于在 windows 95/98 和 windows NT 版本3.51 及更高版本下运行的程序。

有关使用`CImageList`的详细信息, 请参阅[控件](../../mfc/controls-mfc.md)和[使用 CImageList](../../mfc/using-cimagelist.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CImageList`

## <a name="requirements"></a>要求

**标头：** afxcmn.h

##  <a name="add"></a>CImageList:: Add

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
一个指针, 指向包含图像或图像的位图。 从位图的宽度推理出的图像数量。

*pbmMask*<br/>
指向包含掩码的位图的指针。 如果没有与图像列表一起使用的掩码, 则忽略此参数。

*crMask*<br/>
用于生成掩码的颜色。 给定位图中此颜色的每个像素都将更改为黑色, 并且掩码中的相应位将设置为1。

*hIcon*<br/>
包含新图像的位图和掩码的图标的句柄。

### <a name="return-value"></a>返回值

如果成功, 则为第一个新图像的从零开始的索引;否则为-1。

### <a name="remarks"></a>备注

完成后, 你将负责释放图标句柄。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CImageList#1](../../mfc/reference/codesnippet/cpp/cimagelist-class_1.cpp)]

##  <a name="attach"></a>CImageList:: Attach

调用此函数可将图像列表附加到`CImageList`对象。

```
BOOL Attach(HIMAGELIST hImageList);
```

### <a name="parameters"></a>参数

*hImageList*<br/>
图像列表对象的句柄。

### <a name="return-value"></a>返回值

如果连接成功, 则为非零值;否则为0。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CImageList#2](../../mfc/reference/codesnippet/cpp/cimagelist-class_2.cpp)]

##  <a name="begindrag"></a>  CImageList::BeginDrag

调用此函数开始拖动图像。

```
BOOL BeginDrag(
    int nImage,
    CPoint ptHotSpot);
```

### <a name="parameters"></a>参数

*nImage*<br/>
要拖动的图像的从零开始的索引。

*ptHotSpot*<br/>
起始拖动位置 (通常为光标位置) 的坐标。 坐标相对于图像的左上角。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

此函数创建用于拖动的临时图像列表。 图像将指定的图像及其掩码与当前光标组合在一起。 为了响应后续的 WM_MOUSEMOVE 消息, 您可以使用`DragMove`成员函数移动拖动图像。 若要结束拖动操作, 可以使用`EndDrag`成员函数。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CImageList#3](../../mfc/reference/codesnippet/cpp/cimagelist-class_3.cpp)]

##  <a name="cimagelist"></a>CImageList:: CImageList

构造 `CImageList` 对象。

```
CImageList();
```

##  <a name="copy"></a>CImageList:: Copy

此成员函数实现 Win32 函数[ImageList_Copy](/windows/desktop/api/commctrl/nf-commctrl-imagelist_copy)的行为, 如 Windows SDK 中所述。

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
要用作复制操作目标的图像的从零开始的索引。

*iSrc*<br/>
要用作复制操作的源的图像的从零开始的索引。

*uFlags*<br/>
用于指定要进行的复制操作类型的位标志值。 此参数可以是下列值之一:

|值|含义|
|-----------|-------------|
|ILCF_MOVE|源映像将复制到目标映像的索引。 此操作会导致给定映像的多个实例。 默认值为 ILCF_MOVE。|
|ILCF_SWAP|源和目标映像交换映像列表中的位置。|

*pSrc*<br/>
指向作为复制操作`CImageList`目标的对象的指针。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CImageList#6](../../mfc/reference/codesnippet/cpp/cimagelist-class_4.cpp)]

##  <a name="create"></a>CImageList:: Create

初始化图像列表, 并将其附加到[CImageList](../../mfc/reference/cimagelist-class.md)对象。

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
每个图像的尺寸 (以像素为单位)。

*cy*<br/>
每个图像的尺寸 (以像素为单位)。

*nFlags*<br/>
指定要创建的图像列表的类型。 此参数可以是下列值的组合, 但它只能包含其中一个`ILC_COLOR`值。

|值|含义|
|-----------|-------------|
|ILC_COLOR|如果未指定其他任何 ILC_COLOR * 标志, 则使用默认行为。 通常, 默认值为 ILC_COLOR4;但对于较旧的显示驱动程序, 默认值为 ILC_COLORDDB。|
|ILC_COLOR4|使用4位 (16 色) 与设备无关的位图 (DIB) 部分作为图像列表的位图。|
|ILC_COLOR8|使用8位 DIB 部分。 颜色表使用的颜色与半色调调色板的颜色相同。|
|ILC_COLOR16|使用16位 (32/64k 颜色) DIB 部分。|
|ILC_COLOR24|使用24位 DIB 部分。|
|ILC_COLOR32|使用32位 DIB 部分。|
|ILC_COLORDDB|使用设备相关位图。|
|ILC_MASK|使用掩码。 图像列表包含两个位图, 其中一个位图是用作掩码的单色位图。 如果不包含此值, 则图像列表只包含一个位图。 有关屏蔽图像的其他信息, 请参阅[从图像列表绘制图像](../../mfc/drawing-images-from-an-image-list.md)。|

*nInitial*<br/>
图像列表最初包含的图像的数目。

*nGrow*<br/>
当系统需要调整列表大小以为新图像腾出空间时, 图像列表可以增加的映像数。 此参数表示已调整大小的图像列表可以包含的新图像的数目。

*nBitmapID*<br/>
要与图像列表关联的位图的资源 Id。

*crMask*<br/>
用于生成掩码的颜色。 在指定位图中, 此颜色的每个像素都将更改为黑色, 并且掩码中的相应位将设置为1。

*lpszBitmapID*<br/>
一个包含映像的资源 Id 的字符串。

*imagelist1*<br/>
对 `CImageList` 对象的引用。

*nImage1*<br/>
第一个现有图像的索引。

*imagelist2*<br/>
对 `CImageList` 对象的引用。

*nImage2*<br/>
第二个现有图像的索引。

*dx*<br/>
与第一个图像的关系中的第二个图像的 x 轴的偏移量 (以像素为单位)。

*dy*<br/>
与第一个图像的关系中的第二个图像的 y 轴的偏移量 (以像素为单位)。

*pImageList*<br/>
指向 `CImageList` 对象的指针。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

可以通过`CImageList`两个步骤构造。 首先, 调用构造函数, 然后调用`Create`, 它将创建图像列表, 并将其附加`CImageList`到对象。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CImageList#7](../../mfc/reference/codesnippet/cpp/cimagelist-class_5.cpp)]

##  <a name="deleteimagelist"></a>CImageList::D eleteImageList

调用此函数可删除图像列表。

```
BOOL DeleteImageList();
```

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CImageList#8](../../mfc/reference/codesnippet/cpp/cimagelist-class_6.cpp)]

##  <a name="deletetempmap"></a>  CImageList::DeleteTempMap

由`CWinApp` `DeleteTempMap`空闲时间处理程序自动调用, 删除由`hImageList` [FromHandle](#fromhandle)创建`CImageList`的所有临时对象, 但不会销毁暂时与`ImageList`对象.

```
static void PASCAL DeleteTempMap();
```

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CImageList#9](../../mfc/reference/codesnippet/cpp/cimagelist-class_7.cpp)]

##  <a name="detach"></a>CImageList::D etach

调用此函数可将图像列表对象与`CImageList`对象分离。

```
HIMAGELIST Detach();
```

### <a name="return-value"></a>返回值

图像列表对象的句柄。

### <a name="remarks"></a>备注

此函数返回图像列表对象的句柄。

### <a name="example"></a>示例

  请参阅[CImageList:: Attach](#attach)的示例。

##  <a name="dragenter"></a>CImageList::D ragEnter

在拖动操作过程中, 会锁定*pWndLock*指定的窗口的更新, 并在*点*指定的位置显示拖动图像。

```
static BOOL PASCAL DragEnter(
    CWnd* pWndLock,
    CPoint point);
```

### <a name="parameters"></a>参数

*pWndLock*<br/>
指向拥有拖动图像的窗口的指针。

*point*<br/>
要显示拖动图像的位置。 坐标相对于窗口的左上角 (而非工作区)。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

坐标相对于窗口的左上角, 因此, 在指定坐标时, 您必须对窗口元素 (例如, 边框、标题栏和菜单栏) 的宽度进行补偿。

如果*pWndLock*为 NULL, 则此函数将在与桌面窗口关联的显示上下文中绘制图像, 坐标相对于屏幕的左上角。

此函数在拖动操作过程中锁定给定窗口的所有其他更新。 如果需要在拖动操作期间执行任何绘图 (例如突出显示拖放操作的目标), 则可以使用[CImageList::D ragleave](#dragleave)函数暂时隐藏拖动后的图像。

### <a name="example"></a>示例

  请参阅[CImageList:: BeginDrag](#begindrag)的示例。

##  <a name="dragleave"></a>CImageList::D ragLeave

解锁*pWndLock*指定的窗口, 并隐藏拖动图像, 以允许更新窗口。

```
static BOOL PASCAL DragLeave(CWnd* pWndLock);
```

### <a name="parameters"></a>参数

*pWndLock*<br/>
指向拥有拖动图像的窗口的指针。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="example"></a>示例

  请参阅[CImageList:: EndDrag](#enddrag)的示例。

##  <a name="dragmove"></a>CImageList::D ragMove

调用此函数可在拖放操作过程中移动正在拖动的图像。

```
static BOOL PASCAL DragMove(CPoint pt);
```

### <a name="parameters"></a>参数

*pt*<br/>
新的拖动位置。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

通常调用此函数以响应 WM_MOUSEMOVE 消息。 若要开始拖动操作, 请使用`BeginDrag`成员函数。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CImageList#4](../../mfc/reference/codesnippet/cpp/cimagelist-class_8.cpp)]

##  <a name="dragshownolock"></a>CImageList::D ragShowNolock

在拖动操作期间显示或隐藏拖动图像, 而不锁定窗口。

```
static BOOL PASCAL DragShowNolock(BOOL bShow);
```

### <a name="parameters"></a>参数

*bShow*<br/>
指定是否要显示拖动图像。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

在拖动操作过程中, [CImageList::D ragenter](#dragenter)函数会锁定对该窗口的所有更新。 但是, 此函数不会锁定窗口。

##  <a name="draw"></a>CImageList::D raw

调用此函数可绘制拖放操作过程中正在拖动的图像。

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

*nImage*<br/>
要绘制的图像的从零开始的索引。

*pt*<br/>
在指定设备上下文中绘制的位置。

*nStyle*<br/>
指定绘制样式的标志。 它可以是以下一个或多个值:

|值|含义|
|-----------|-------------|
|ILD_BLEND25, ILD_FOCUS|绘制图像, 将 25% 与系统突出显示颜色混合。 如果图像列表不包含掩码, 此值将不起作用。|
|ILD_BLEND50, ILD_SELECTED, ILD_BLEND|绘制图像, 将 50% 与系统突出显示颜色混合。 如果图像列表不包含掩码, 此值将不起作用。|
|ILD_MASK|绘制掩码。|
|ILD_NORMAL|使用图像列表的背景色绘制图像。 如果背景色是 CLR_NONE 值, 则使用掩码以透明方式绘制图像。|
|ILD_TRANSPARENT|使用掩码以透明方式绘制图像, 而不考虑背景色。|

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="example"></a>示例

  请参阅[CImageList:: SetOverlayImage](#setoverlayimage)的示例。

##  <a name="drawex"></a>CImageList::D rawEx

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

*nImage*<br/>
要绘制的图像的从零开始的索引。

*pt*<br/>
在指定设备上下文中绘制的位置。

*sz*<br/>
相对于图像的左上角绘制的图像部分的大小。 请参阅 Windows SDK 中[ImageList_DrawEx](/windows/desktop/api/commctrl/nf-commctrl-imagelist_drawex)的*dx*和*dy* 。

*clrBk*<br/>
图像的背景色。 请参阅 Windows SDK 的[ImageList_DrawEx](/windows/desktop/api/commctrl/nf-commctrl-imagelist_drawex)中的*rgbBk* 。

*clrFg*<br/>
图像的前景色。 请参阅 Windows SDK 的[ImageList_DrawEx](/windows/desktop/api/commctrl/nf-commctrl-imagelist_drawex)中的*rgbFg* 。

*nStyle*<br/>
指定绘制样式的标志。 请参阅 Windows SDK 的[ImageList_DrawEx](/windows/desktop/api/commctrl/nf-commctrl-imagelist_drawex)中的*fStyle* 。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

函数使用指定的绘制样式, 并将图像与指定的颜色混合。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CImageList#10](../../mfc/reference/codesnippet/cpp/cimagelist-class_9.cpp)]

##  <a name="drawindirect"></a>CImageList::D rawIndirect

调用此成员函数以从图像列表中绘制图像。

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
指向[IMAGELISTDRAWPARAMS](/windows/desktop/api/commctrl/ns-commctrl-imagelistdrawparams)结构的指针, 该结构包含有关绘制操作的信息。

*pDC*<br/>
指向目标设备上下文的指针。 完成此[CDC](../../mfc/reference/cdc-class.md)对象之后, 必须将其删除。

*nImage*<br/>
要绘制的图像的从零开始的索引。

*pt*<br/>
一个[点](/previous-versions/dd162805\(v=vs.85\))结构, 其中包含将在其中绘制图像的 x 坐标和 y 坐标。

*sz*<br/>
一个[大小](/windows/desktop/api/windef/ns-windef-tagsize)结构, 指示要绘制的图像的大小。

*ptOrigin*<br/>
一个[点](/previous-versions/dd162805\(v=vs.85\))结构, 其中包含指定绘制操作的左上角的 x 坐标和 y 坐标 (相对于图像本身)。 不绘制 x 坐标左侧和上方 y 坐标上方的图像的像素。

*fStyle*<br/>
用于指定绘制样式和覆盖图像 (可选) 的标志。 有关覆盖图像的信息, 请参阅 "备注" 部分。 MFC 默认实现 ILD_NORMAL 使用图像列表的背景色绘制图像。 如果背景色是 CLR_NONE 值, 则使用掩码以透明方式绘制图像。

其他可能的样式在[IMAGELISTDRAWPARAMS](/windows/desktop/api/commctrl/ns-commctrl-imagelistdrawparams)结构的*fStyle*成员下介绍。

*dwRop*<br/>
指定光栅操作代码的值。 这些代码定义了如何将源矩形的颜色数据与目标矩形的颜色数据组合在一起以实现最终颜色。 MFC 的默认实现 SRCCOPY 将源矩形直接复制到目标矩形。 如果*fStyle*参数不包含 ILD_ROP 标志, 则忽略此参数。

其他可能的值在[IMAGELISTDRAWPARAMS](/windows/desktop/api/commctrl/ns-commctrl-imagelistdrawparams)结构的*dwRop*成员下介绍。

*rgbBack*<br/>
默认情况下, 图像背景色为 CLR_DEFAULT。 此参数可以是应用程序定义的 RGB 值, 也可以是以下值之一:

|值|含义|
|-----------|-------------|
|CLR_DEFAULT|默认背景色。 使用图像列表背景色绘制图像。|
|CLR_NONE|无背景色。 以透明方式绘制图像。|

*rgbFore*<br/>
图像前景色, 默认情况下为 CLR_DEFAULT。 此参数可以是应用程序定义的 RGB 值, 也可以是以下值之一:

|值|含义|
|-----------|-------------|
|CLR_DEFAULT|默认前景色。 使用系统突出显示颜色作为前景颜色绘制图像。|
|CLR_NONE|无混合颜色。 图像与目标设备上下文的颜色混合。|

仅当*fStyle*包含 ILD_BLEND25 或 ILD_BLEND50 标志时, 才使用此参数。

*fState*<br/>
指定绘制状态的标志。 此成员可以包含一个或多个图像列表状态标志。

*框架*<br/>
影响 "饱和" 和 "alpha" 混合效果的行为。

与 ILS_SATURATE 一起使用时, 此成员保留添加到图标中每个像素的 RGB 三个颜色部分的值。

与 ILS_APLHA 一起使用时, 此成员保存 alpha 通道的值。 此值可以是从0到255的值, 0 是完全透明的, 255 完全不透明。

*crEffect*<br/>
用于发光和阴影效果的[COLORREF](/windows/desktop/gdi/colorref)值。

### <a name="return-value"></a>返回值

如果图像已成功绘制, 则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

如果要自行填充 Win32 结构, 请使用第一个版本。 如果要利用一个或多个 MFC 默认参数, 请使用第二个版本, 或者避免管理结构。

覆盖图像是在主图像上绘制的图像, 该图像在此成员函数中由*n*参数指定。 使用带有[INDEXTOOVERLAYMASK](/windows/desktop/api/commctrl/nf-commctrl-indextooverlaymask)宏指定的覆盖[Draw](#draw)掩码的从1开始的索引, 绘制覆盖掩码。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CImageList#11](../../mfc/reference/codesnippet/cpp/cimagelist-class_10.cpp)]

##  <a name="enddrag"></a>CImageList:: EndDrag

调用此函数可结束拖动操作。

```
static void PASCAL EndDrag();
```

### <a name="remarks"></a>备注

若要开始拖动操作, 请使用`BeginDrag`成员函数。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CImageList#5](../../mfc/reference/codesnippet/cpp/cimagelist-class_11.cpp)]

##  <a name="extracticon"></a>CImageList:: ExtractIcon

调用此函数可基于图像列表中的图像及其相关掩码创建图标。

```
HICON ExtractIcon(int nImage);
```

### <a name="parameters"></a>参数

*nImage*<br/>
图像的从零开始的索引。

### <a name="return-value"></a>返回值

如果成功, 则返回图标的句柄;否则为 NULL。

### <a name="remarks"></a>备注

此方法依赖于[ImageList_ExtractIcon](/windows/desktop/api/commctrl/nf-commctrl-imagelist_extracticon)宏的行为来创建图标。 有关图标创建和清理的详细信息, 请参阅[ImageList_ExtractIcon](/windows/desktop/api/commctrl/nf-commctrl-imagelist_extracticon)宏。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CImageList#12](../../mfc/reference/codesnippet/cpp/cimagelist-class_12.cpp)]

##  <a name="fromhandle"></a>CImageList:: FromHandle

当给定图像列表的`CImageList`句柄时, 返回指向对象的指针。

```
static CImageList* PASCAL FromHandle(HIMAGELIST hImageList);
```

### <a name="parameters"></a>参数

*hImageList*<br/>
指定图像列表。

### <a name="return-value"></a>返回值

如果成功, 则`CImageList`为指向对象的指针; 否则为 NULL。

### <a name="remarks"></a>备注

如果尚未附加到句柄, 则会创建并附加`CImageList`一个临时对象。 `CImageList` 此临时`CImageList`对象仅在下一次应用程序的事件循环中有空闲时间之前有效, 此时将删除所有临时对象。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CImageList#13](../../mfc/reference/codesnippet/cpp/cimagelist-class_13.cpp)]

##  <a name="fromhandlepermanent"></a>CImageList:: FromHandlePermanent

当给定图像列表的`CImageList`句柄时, 返回指向对象的指针。

```
static CImageList* PASCAL FromHandlePermanent(HIMAGELIST hImageList);
```

### <a name="parameters"></a>参数

*hImageList*<br/>
指定图像列表。

### <a name="return-value"></a>返回值

如果成功, 则`CImageList`为指向对象的指针; 否则为 NULL。

### <a name="remarks"></a>备注

`CImageList`如果对象未附加到句柄, 则返回 NULL。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CImageList#14](../../mfc/reference/codesnippet/cpp/cimagelist-class_14.cpp)]

##  <a name="getbkcolor"></a>CImageList:: GetBkColor

调用此函数可检索图像列表的当前背景色。

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>返回值

`CImageList`对象背景色的 RGB 颜色值。

### <a name="example"></a>示例

  请参阅[CImageList:: SetBkColor](#setbkcolor)的示例。

##  <a name="getdragimage"></a>CImageList:: GetDragImage

获取用于拖动的临时图像列表。

```
static CImageList* PASCAL GetDragImage(
    LPPOINT lpPoint,
    LPPOINT lpPointHotSpot);
```

### <a name="parameters"></a>参数

*lpPoint*<br/>
接收当前拖动位置的[点](/previous-versions/dd162805\(v=vs.85\))结构的地址。

*lpPointHotSpot*<br/>
`POINT`结构的地址, 该结构接收拖动图像相对于拖动位置的偏移量。

### <a name="return-value"></a>返回值

如果成功, 则为指向用于拖动的临时图像列表的指针;否则为 NULL。

##  <a name="getimagecount"></a>CImageList:: GetImageCount

调用此函数可检索图像列表中的图像数量。

```
int GetImageCount() const;
```

### <a name="return-value"></a>返回值

图像数量。

### <a name="example"></a>示例

  请参阅[CImageList:: ExtractIcon](#extracticon)的示例。

##  <a name="getimageinfo"></a>CImageList:: GetImageInfo

调用此函数可检索有关映像的信息。

```
BOOL GetImageInfo(
    int nImage,
    IMAGEINFO* pImageInfo) const;
```

### <a name="parameters"></a>参数

*nImage*<br/>
图像的从零开始的索引。

*pImageInfo*<br/>
指向[IMAGEINFO](/windows/desktop/api/commctrl/ns-commctrl-imageinfo)结构的指针, 该结构接收有关图像的信息。 此结构中的信息可用于直接操作图像的位图。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

`IMAGEINFO`结构包含图像列表中图像的相关信息。

##  <a name="getsafehandle"></a>CImageList:: GetSafeHandle

调用此函数可检索`m_hImageList`数据成员。

```
HIMAGELIST GetSafeHandle() const;
```

### <a name="return-value"></a>返回值

附加图像列表的句柄;否则为 NULL。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CImageList#15](../../mfc/reference/codesnippet/cpp/cimagelist-class_15.cpp)]

##  <a name="m_himagelist"></a>CImageList:: m_hImageList

附加到此对象的图像列表的句柄。

`HIMAGELIST m_hImageList;`

### <a name="remarks"></a>备注

`m_hImageList`数据成员是 HIMAGELIST 类型的公共变量。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CImageList#23](../../mfc/reference/codesnippet/cpp/cimagelist-class_16.cpp)]

##  <a name="operator_himagelist"></a>CImageList:: operator HIMAGELIST

使用此运算符可获取`CImageList`对象的附加句柄。

```
operator HIMAGELIST() const;
```

### <a name="return-value"></a>返回值

如果成功, 则为`CImageList`对象表示的图像列表的句柄; 否则为 NULL。

### <a name="remarks"></a>备注

此运算符是支持直接使用 HIMAGELIST 对象的强制转换运算符。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CImageList#16](../../mfc/reference/codesnippet/cpp/cimagelist-class_17.cpp)]

##  <a name="read"></a>CImageList:: Read

调用此函数可从存档中读取图像列表。

```
BOOL Read(CArchive* pArchive);
```

### <a name="parameters"></a>参数

*pArchive*<br/>
指向`CArchive`对象的指针, 将从该对象中读取图像列表。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CImageList#18](../../mfc/reference/codesnippet/cpp/cimagelist-class_18.cpp)]

##  <a name="remove"></a>CImageList:: Remove

调用此函数可从图像列表对象中移除图像。

```
BOOL Remove(int nImage);
```

### <a name="parameters"></a>参数

*nImage*<br/>
要移除的图像的从零开始的索引。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

*N*后面的所有项现在都向下移动一个位置。 例如, 如果图像列表包含两个项, 则删除第一项将导致剩余项现在位于第一个位置。 对于第一个位置中的项, *n*= 0。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CImageList#19](../../mfc/reference/codesnippet/cpp/cimagelist-class_19.cpp)]

##  <a name="replace"></a>CImageList:: Replace

调用此函数可将图像列表中的图像替换为新图像。

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
指向包含图像的位图的指针。

*pbmMask*<br/>
指向包含掩码的位图的指针。 如果没有与图像列表一起使用的掩码, 则忽略此参数。

*hIcon*<br/>
包含新图像的位图和掩码的图标的句柄。

### <a name="return-value"></a>返回值

如果成功, 返回 BOOL 的版本返回非零值;否则为0。

如果成功, 返回**int**的版本返回映像的从零开始的索引;否则为-1。

### <a name="remarks"></a>备注

在调用[SetImageCount](#setimagecount)之后调用此成员函数, 以将新的有效图像分配给占位符图像索引号。

### <a name="example"></a>示例

  请参阅[CImageList:: SetImageCount](#setimagecount)的示例。

##  <a name="setbkcolor"></a>CImageList:: SetBkColor

调用此函数可设置图像列表的背景色。

```
COLORREF SetBkColor(COLORREF cr);
```

### <a name="parameters"></a>参数

*cr*<br/>
要设置的背景色。 它可以是 CLR_NONE。 在这种情况下, 将使用掩码以透明方式绘制图像。

### <a name="return-value"></a>返回值

如果成功, 则为上一种背景色;否则为 CLR_NONE。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CImageList#20](../../mfc/reference/codesnippet/cpp/cimagelist-class_20.cpp)]

##  <a name="setdragcursorimage"></a>CImageList:: SetDragCursorImage

通过将给定图像 (通常是鼠标光标图像) 与当前拖动图像组合来创建新的拖动图像。

```
BOOL SetDragCursorImage(
    int nDrag,
    CPoint ptHotSpot);
```

### <a name="parameters"></a>参数

*nDrag*<br/>
要与拖动图像合并的新图像的索引。

*ptHotSpot*<br/>
热点在新图像中的位置。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

由于拖动函数在拖动操作期间使用新图像, 因此应在调用`CImageList::SetDragCursorImage`后使用 Windows [ShowCursor](/windows/desktop/api/winuser/nf-winuser-showcursor)函数隐藏实际的鼠标光标。 否则，系统在拖动操作期间可能看起来具有两个鼠标光标。

##  <a name="setimagecount"></a>CImageList:: SetImageCount

调用此成员函数可重置`CImageList`对象中的图像数量。

```
BOOL SetImageCount(UINT uNewCount);
```

### <a name="parameters"></a>参数

*uNewCount*<br/>
指定图像列表中的新图像总数的值。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

### <a name="remarks"></a>备注

如果调用此成员函数以增加图像列表中的图像数, 则对每个其他图像调用[Replace](#replace) , 以将新索引分配给有效的图像。 如果无法将索引分配给有效的映像, 则创建新映像的绘图操作将是不可预知的。

如果使用此函数减小图像列表的大小, 则会释放截断的图像。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CImageList#21](../../mfc/reference/codesnippet/cpp/cimagelist-class_21.cpp)]

##  <a name="setoverlayimage"></a>CImageList:: SetOverlayImage

调用此函数可将图像的从零开始的索引添加到要用作覆盖蒙板的图像的列表。

```
BOOL SetOverlayImage(
    int nImage,
    int nOverlay);
```

### <a name="parameters"></a>参数

*nImage*<br/>
要用作覆盖蒙板的图像的从零开始的索引。

*nOverlay*<br/>
覆盖掩码的从1开始的索引。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

最多可向列表中添加四个索引。

覆盖屏蔽是在另一个图像上透明绘制的图像。 使用[CImageList::D raw](#draw)成员函数, 通过 INDEXTOOVERLAYMASK 宏指定的覆盖掩码从1开始的索引, 在图像上绘制叠加掩码。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CImageList#22](../../mfc/reference/codesnippet/cpp/cimagelist-class_22.cpp)]

##  <a name="write"></a>CImageList:: Write

调用此函数可将图像列表对象写入存档。

```
BOOL Write(CArchive* pArchive);
```

### <a name="parameters"></a>参数

*pArchive*<br/>
一个指针, 指向`CArchive`要在其中存储图像列表的对象。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CImageList#17](../../mfc/reference/codesnippet/cpp/cimagelist-class_23.cpp)]

## <a name="see-also"></a>请参阅

[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CListCtrl 类](../../mfc/reference/clistctrl-class.md)<br/>
[CTabCtrl 类](../../mfc/reference/ctabctrl-class.md)
