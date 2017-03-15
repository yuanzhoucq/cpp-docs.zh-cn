---
title: "CImageList 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CImageList
dev_langs:
- C++
helpviewer_keywords:
- Windows common controls [C++], CImageList
- image lists [C++], CImageList class
- CImageList class
ms.assetid: b6d1a704-1c82-4548-8a8f-77972adc98a5
caps.latest.revision: 19
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
ms.openlocfilehash: e61d99d6d68b1c68cd5e306dd0fcd10d6fe4324d
ms.lasthandoff: 02/24/2017

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
  
|名称|说明|  
|----------|-----------------|  
|[CImageList::Add](#add)|将图像添加到图像列表。|  
|[CImageList::Attach](#attach)|将附加到图像列表`CImageList`对象。|  
|[CImageList::BeginDrag](#begindrag)|开始拖动图像。|  
|[CImageList::Copy](#copy)|将图像内的复制`CImageList`对象。|  
|[CImageList::Create](#create)|初始化图像列表并将其附加到`CImageList`对象。|  
|[CImageList::DeleteImageList](#deleteimagelist)|删除图像列表。|  
|[CImageList::DeleteTempMap](#deletetempmap)|由调用[CWinApp](../../mfc/reference/cwinapp-class.md)空闲时间处理程序，以删除任何临时`CImageList`创建的对象`FromHandle`。|  
|[CImageList::Detach](#detach)|从图像列表对象中分离`CImageList`对象，并返回图像列表的句柄。|  
|[CImageList::DragEnter](#dragenter)|在拖动操作期间锁定更新并在指定位置显示拖动图像。|  
|[CImageList::DragLeave](#dragleave)|解锁窗口中，并隐藏拖动图像，以便该窗口可以更新。|  
|[CImageList::DragMove](#dragmove)|将图像拖放操作期间所拖动的移动。|  
|[CImageList::DragShowNolock](#dragshownolock)|显示或隐藏在拖动操作期间的拖动图像，而不会锁定窗口中。|  
|[Cimagelist:: Draw](#draw)|绘制拖放操作期间所拖动的图像。|  
|[CImageList::DrawEx](#drawex)|在指定的设备上下文中绘制的图像列表项。 该函数使用指定的绘制样式，并结合使用指定的颜色的图像。|  
|[CImageList::DrawIndirect](#drawindirect)|从图像列表绘制图像。|  
|[CImageList::EndDrag](#enddrag)|结束执行拖动操作。|  
|[CImageList::ExtractIcon](#extracticon)|创建基于的图像和掩码图像列表中的图标。|  
|[CImageList::FromHandle](#fromhandle)|返回一个指向`CImageList`对象时提供给图像列表的句柄。 如果 `CImageList` 对象未附加到该句柄，则会创建并附加一个临时 `CImageList` 对象。|  
|[CImageList::FromHandlePermanent](#fromhandlepermanent)|返回一个指向`CImageList`对象时提供给图像列表的句柄。 如果`CImageList`对象未附加到该句柄， **NULL**返回。|  
|[CImageList::GetBkColor](#getbkcolor)|检索图像列表的当前背景色。|  
|[CImageList::GetDragImage](#getdragimage)|获取用于拖动的临时图像列表。|  
|[CImageList::GetImageCount](#getimagecount)|检索图像列表中的映像数。|  
|[CImageList::GetImageInfo](#getimageinfo)|检索有关某个映像的信息。|  
|[CImageList::GetSafeHandle](#getsafehandle)|检索**m_hImageList**。|  
|[CImageList::Read](#read)|从存档中读取图像列表。|  
|[CImageList::Remove](#remove)|从图像列表中删除映像。|  
|[CImageList::Replace](#replace)|图像列表中的图像替换为新图像。|  
|[CImageList::SetBkColor](#setbkcolor)|设置图像列表的背景色。|  
|[CImageList::SetDragCursorImage](#setdragcursorimage)|创建一个新的拖动图像。|  
|[CImageList::SetImageCount](#setimagecount)|将图像列表中的图像的计数重置。|  
|[Cimagelist:: Setoverlayimage](#setoverlayimage)|要用作覆盖掩码的图像列表中添加图像的从零开始的索引。|  
|[CImageList::Write](#write)|图像列表写入存档。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|说明|  
|----------|-----------------|  
|[CImageList::operator HIMAGELIST](#operator_himagelist)|返回`HIMAGELIST`附加到`CImageList`。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CImageList::m_hImageList](#m_himagelist)|一个包含图像列表附加到此对象的句柄。|  
  
## <a name="remarks"></a>备注  
 "图像列表"是相同大小的图像，其中每个可以通过从零开始的索引引用的集合。 图像列表用于有效地管理大的图标或位图集。 图像列表中的所有图像都包含在单个的宽位图，以屏幕设备格式。 图像列表可能包含一个单色位图，该位图包含用于透明地绘制图像的蒙板（图标样式）。 Microsoft Win32 应用程序编程接口 (API) 提供了可让您绘制图像、 创建和销毁图像列表、 添加和移除图像、 替换图像、 合并图像以及拖动图像的图像列表函数。  
  
 此控件 (并因此`CImageList`类) 仅适用于在 Windows 95/98 和 Windows NT 版本 3.51 下运行的程序和更高版本。  
  
 有关详细信息使用`CImageList`，请参阅[控件](../../mfc/controls-mfc.md)和[使用 CImageList](../../mfc/using-cimagelist.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CImageList`  
  
## <a name="requirements"></a>要求  
 **标头：** afxcmn.h  
  
##  <a name="a-nameadda--cimagelistadd"></a><a name="add"></a>CImageList::Add  
 调用此函数可将一个或多个图像或一个图标添加到图像列表。  
  
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
 `pbmImage`  
 指针，指向包含的图像的位图。 位图的宽度推断的映像数量。  
  
 `pbmMask`  
 指针，指向包含该掩码的位图。 如果未应用蒙板的图像列表一起使用，则忽略此参数。  
  
 `crMask`  
 用来生成屏蔽的颜色。 每个像素的给定位图中此颜色更改为黑色和掩码中的对应位设置为一个。  
  
 `hIcon`  
 包含位图和新图像的图标的句柄。  
  
### <a name="return-value"></a>返回值  
 如果成功，则第一个新图像的从零开始的索引否则为-1。  
  
### <a name="remarks"></a>备注  
 您有责任在完成时将其释放图标句柄。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CImageList #&1;](../../mfc/reference/codesnippet/cpp/cimagelist-class_1.cpp)]  
  
##  <a name="a-nameattacha--cimagelistattach"></a><a name="attach"></a>CImageList::Attach  
 调用此函数可将附加到图像列表`CImageList`对象。  
  
```  
BOOL Attach(HIMAGELIST hImageList);
```  
  
### <a name="parameters"></a>参数  
 `hImageList`  
 图像列表对象的句柄。  
  
### <a name="return-value"></a>返回值  
 如果附件成功，则非零值否则为 0。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CImageList #&2;](../../mfc/reference/codesnippet/cpp/cimagelist-class_2.cpp)]  
  
##  <a name="a-namebegindraga--cimagelistbegindrag"></a><a name="begindrag"></a>CImageList::BeginDrag  
 调用此函数开始拖动图像。  
  
```  
BOOL BeginDrag(
    int nImage,  
    CPoint ptHotSpot);
```  
  
### <a name="parameters"></a>参数  
 `nImage`  
 要拖动图像的从零开始索引。  
  
 `ptHotSpot`  
 开始拖动位置 （通常情况下，光标位置） 的坐标。 坐标是相对于图像的左上角。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 此函数创建用于拖动一个临时的图像列表。 图像将指定的图像和其掩码与当前光标结合起来。 在后续响应`WM_MOUSEMOVE`消息，您可以通过使用移动拖动图像`DragMove`成员函数。 若要结束拖放操作，可以使用`EndDrag`成员函数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CImageList #&3;](../../mfc/reference/codesnippet/cpp/cimagelist-class_3.cpp)]  
  
##  <a name="a-namecimagelista--cimagelistcimagelist"></a><a name="cimagelist"></a>CImageList::CImageList  
 构造 `CImageList` 对象。  
  
```  
CImageList();
```  
  
##  <a name="a-namecopya--cimagelistcopy"></a><a name="copy"></a>CImageList::Copy  
 此成员函数实现的 Win32 函数的行为[ImageList_Copy](http://msdn.microsoft.com/library/windows/desktop/bb761520)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
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
 *iDst*  
 要作为复制操作的目标使用的图像的从零开始的索引。  
  
 `iSrc`  
 要作为复制操作的源使用的图像的从零开始的索引。  
  
 `uFlags`  
 位标志值，指定要进行复制操作的类型。 此参数可以是下列值之一︰  
  
|值|含义|  
|-----------|-------------|  
|`ILCF_MOVE`|源图像复制到目标图像的索引。 此操作会导致给定图像的多个实例。 默认为 `ILCF_MOVE`。|  
|`ILCF_SWAP`|源和目标图像交换图像列表内的位置。|  
  
 `pSrc`  
 一个指向`CImageList`复制操作的目标对象。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CImageList #&6;](../../mfc/reference/codesnippet/cpp/cimagelist-class_4.cpp)]  
  
##  <a name="a-namecreatea--cimagelistcreate"></a><a name="create"></a>CImageList::Create  
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
 `cx`  
 每个映像，以像素为单位的尺寸。  
  
 `cy`  
 每个映像，以像素为单位的尺寸。  
  
 `nFlags`  
 指定要创建的图像列表的类型。 此参数可以是下列值的组合，但它可以包括只有其中一个`ILC_COLOR`值。  
  
|值|含义|  
|-----------|-------------|  
|`ILC_COLOR`|使用默认行为，如果没有其他`ILC_COLOR`* 指定标志。 通常，默认值是`ILC_COLOR4`; 但默认情况下较旧的显示器驱动程序的`ILC_COLORDDB`。|  
|`ILC_COLOR4`|使用 4 位 （16 种颜色） 与设备无关位图 (DIB) 节与位图的图像列表。|  
|`ILC_COLOR8`|使用 8 位 DIB 部分。 使用颜色表的颜色是作为半色调调色板的相同颜色。|  
|`ILC_COLOR16`|使用 16 位 (32/64 k 颜色) DIB 部分。|  
|`ILC_COLOR24`|使用 24 位 DIB 部分。|  
|`ILC_COLOR32`|使用 32 位 DIB 部分。|  
|`ILC_COLORDDB`|使用设备无关位图。|  
|`ILC_MASK`|使用掩码。 图像列表包含两个位图，其中之一是用作掩码的单色位图。 如果未包括此值，则图像列表包含了只有一个位图。 请参阅[从图像列表绘制图像](../../mfc/drawing-images-from-an-image-list.md)蒙板的图像上的其他信息。|  
  
 `nInitial`  
 图像列表最初包含的映像数。  
  
 `nGrow`  
 图像列表可以依据增长时系统需要调整大小的列表，以便腾出空间供新的映像的映像数。 此参数表示调整大小的图像列表可能包含新映像的数量。  
  
 `nBitmapID`  
 资源的位图的 Id 与图像列表相关联。  
  
 `crMask`  
 若要生成掩码所使用的颜色。 指定位图中此颜色的每个像素将变为黑色，并且对应的位掩码中设置为其中一个。  
  
 `lpszBitmapID`  
 包含的图像的资源 Id 的字符串。  
  
 `imagelist1`  
 对 `CImageList` 对象的引用。  
  
 `nImage1`  
 第一个现有图像的索引。  
  
 `imagelist2`  
 对 `CImageList` 对象的引用。  
  
 `nImage2`  
 第二个现有图像的索引。  
  
 `dx`  
 与第一个图像，以像素为单位的关系中的第二个图像的 x 轴的偏移量。  
  
 `dy`  
 与第一个图像，以像素为单位的关系中第二个图像的 y 轴的偏移量。  
  
 `pImageList`  
 一个指向`CImageList`对象。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 您构造`CImageList`分两个步骤。 首先，调用构造函数，然后调用`Create`，它创建图像列表并将其附加到`CImageList`对象。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CImageList #&7;](../../mfc/reference/codesnippet/cpp/cimagelist-class_5.cpp)]  
  
##  <a name="a-namedeleteimagelista--cimagelistdeleteimagelist"></a><a name="deleteimagelist"></a>CImageList::DeleteImageList  
 调用此函数可删除图像列表。  
  
```  
BOOL DeleteImageList();
```  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CImageList #&8;](../../mfc/reference/codesnippet/cpp/cimagelist-class_6.cpp)]  
  
##  <a name="a-namedeletetempmapa--cimagelistdeletetempmap"></a><a name="deletetempmap"></a>CImageList::DeleteTempMap  
 自动调用`CWinApp`空闲时间处理程序中，`DeleteTempMap`删除任何临时`CImageList`由创建的对象[fromhandle，前者能够](#fromhandle)，但不会破坏任何句柄 ( `hImageList`) 与临时关联**ImageList**对象。  
  
```  
static void PASCAL DeleteTempMap();
```  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CImageList #&9;](../../mfc/reference/codesnippet/cpp/cimagelist-class_7.cpp)]  
  
##  <a name="a-namedetacha--cimagelistdetach"></a><a name="detach"></a>CImageList::Detach  
 调用此函数可从图像列表对象中分离`CImageList`对象。  
  
```  
HIMAGELIST Detach();
```  
  
### <a name="return-value"></a>返回值  
 图像列表对象的句柄。  
  
### <a name="remarks"></a>备注  
 此函数返回的句柄的图像列表对象。  
  
### <a name="example"></a>示例  
  请参阅示例[CImageList::Attach](#attach)。  
  
##  <a name="a-namedragentera--cimagelistdragenter"></a><a name="dragenter"></a>CImageList::DragEnter  
 在拖动操作期间锁定指定的窗口更新`pWndLock`并显示由指定的位置拖动图像`point`。  
  
```  
static BOOL PASCAL DragEnter(
    CWnd* pWndLock,  
    CPoint point);
```  
  
### <a name="parameters"></a>参数  
 `pWndLock`  
 指向拥有拖动图像的窗口。  
  
 `point`  
 在显示拖动图像的位置。 坐标是相对于窗口 （而不是工作区） 的左上角。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 坐标是相对于窗口的左上角，因此在指定坐标时必须补偿窗口元素，如边框、 标题栏和菜单栏的宽度。  
  
 如果`pWndLock`是**NULL**、 此函数与桌面窗口关联的显示上下文中绘制的图像和坐标是相对于屏幕左上角。  
  
 此函数在拖动操作期间将锁定给定窗口的所有其他更新。 如果您需要做的任何绘图，在拖动操作，如突出显示拖放操作的目标可以使用临时隐藏拖动的图像[CImageList::DragLeave](#dragleave)函数。  
  
### <a name="example"></a>示例  
  请参阅示例[CImageList::BeginDrag](#begindrag)。  
  
##  <a name="a-namedragleavea--cimagelistdragleave"></a><a name="dragleave"></a>CImageList::DragLeave  
 取消锁定指定的窗口`pWndLock`并隐藏拖动图像，允许更新窗口。  
  
```  
static BOOL PASCAL DragLeave(CWnd* pWndLock);
```  
  
### <a name="parameters"></a>参数  
 `pWndLock`  
 指向拥有拖动图像的窗口。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="example"></a>示例  
  请参阅示例[CImageList::EndDrag](#enddrag)。  
  
##  <a name="a-namedragmovea--cimagelistdragmove"></a><a name="dragmove"></a>CImageList::DragMove  
 调用此函数可将拖放操作期间所拖动的图像。  
  
```  
static BOOL PASCAL DragMove(CPoint pt);
```  
  
### <a name="parameters"></a>参数  
 `pt`  
 新的拖动位置。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 此函数通常调用以响应`WM_MOUSEMOVE`消息。 若要开始拖动操作，请使用`BeginDrag`成员函数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CImageList #&4;](../../mfc/reference/codesnippet/cpp/cimagelist-class_8.cpp)]  
  
##  <a name="a-namedragshownolocka--cimagelistdragshownolock"></a><a name="dragshownolock"></a>CImageList::DragShowNolock  
 显示或隐藏在拖动操作期间的拖动图像，而不会锁定窗口中。  
  
```  
static BOOL PASCAL DragShowNolock(BOOL bShow);
```  
  
### <a name="parameters"></a>参数  
 `bShow`  
 指定是否要显示拖动图像。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 [CImageList::DragEnter](#dragenter)函数会在拖动操作期间锁定窗口中的所有更新。 此函数，但是，不会锁定窗口中。  
  
##  <a name="a-namedrawa--cimagelistdraw"></a><a name="draw"></a>Cimagelist:: Draw  
 调用此函数可绘制在拖放操作期间所拖动图像。  
  
```  
BOOL Draw(
    CDC* pDC,  
    int nImage,  
    POINT pt,  
    UINT nStyle);
```  
  
### <a name="parameters"></a>参数  
 `pDC`  
 指向目标设备上下文指针。  
  
 `nImage`  
 要绘制的图像的从零开始索引。  
  
 `pt`  
 要在该处绘制指定的设备上下文中的位置。  
  
 `nStyle`  
 指定的绘制样式的标志。 它可以是一个或多个值︰  
  
|值|含义|  
|-----------|-------------|  
|`ILD_BLEND25`**ILD_FOCUS**|绘制图像，混合系统突出显示颜色的 25%。 如果图像列表不包含一个掩码，则此值无效。|  
|`ILD_BLEND50`**ILD_SELECTED**， **ILD_BLEND**|绘制图像，混合系统突出显示颜色的 50%。 如果图像列表不包含一个掩码，则此值无效。|  
|**ILD_MASK**|绘制掩码。|  
|`ILD_NORMAL`|绘制图像的图像列表中使用的背景色。 如果背景色为`CLR_NONE`值，该图像绘制以透明方式使用的掩码。|  
|`ILD_TRANSPARENT`|使用绘制的图像以透明方式的掩码，不论背景色是什么。|  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="example"></a>示例  
  请参阅示例[cimagelist:: Setoverlayimage](#setoverlayimage)。  
  
##  <a name="a-namedrawexa--cimagelistdrawex"></a><a name="drawex"></a>CImageList::DrawEx  
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
 `pDC`  
 指向目标设备上下文指针。  
  
 `nImage`  
 要绘制的图像的从零开始索引。  
  
 `pt`  
 要在该处绘制指定的设备上下文中的位置。  
  
 `sz`  
 要相对于图像的左上角绘制图像的部分的大小。 请参阅`dx`和*dy*中[ImageList_DrawEx](http://msdn.microsoft.com/library/windows/desktop/bb761536)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] *。*  
  
 *clrBk*  
 图像的背景色。 请参阅*rgbBk*中[ImageList_DrawEx](http://msdn.microsoft.com/library/windows/desktop/bb761536)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] *。*  
  
 *clrFg*  
 图像的前景色。 请参阅*rgbFg*中[ImageList_DrawEx](http://msdn.microsoft.com/library/windows/desktop/bb761536)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] *。*  
  
 `nStyle`  
 指定的绘制样式的标志。 请参阅*fStyle*中[ImageList_DrawEx](http://msdn.microsoft.com/library/windows/desktop/bb761536)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] *。*  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 该函数使用指定的绘制样式，并结合使用指定的颜色的图像。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CImageList #&10;](../../mfc/reference/codesnippet/cpp/cimagelist-class_9.cpp)]  
  
##  <a name="a-namedrawindirecta--cimagelistdrawindirect"></a><a name="drawindirect"></a>CImageList::DrawIndirect  
 调用该成员函数以从图像列表绘制图像。  
  
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
 *pimldp*  
 一个指向[IMAGELISTDRAWPARAMS](http://msdn.microsoft.com/library/windows/desktop/bb761395)结构，其中包含与绘制操作有关的信息。  
  
 `pDC`  
 指向目标设备上下文的指针。 您必须删除此[CDC](../../mfc/reference/cdc-class.md)对象完成此操作使用它。  
  
 `nImage`  
 要绘制的图像的从零开始的索引。  
  
 `pt`  
 一个[点](http://msdn.microsoft.com/library/windows/desktop/dd162805)结构，其中包含 x – 和 y – 坐标绘制图像的位置。  
  
 `sz`  
 一个[大小](http://msdn.microsoft.com/library/windows/desktop/dd145106)结构，指示要绘制的图像的大小。  
  
 *ptOrigin*  
 一个[点](http://msdn.microsoft.com/library/windows/desktop/dd162805)结构，其中包含 x – 和 y – 坐标指定针对图像本身绘图操作左上的角。 不绘制图像的左边的 x – 坐标和更高版本 y – 坐标的像素。  
  
 `fStyle`  
 指定的绘制样式和 （可选） 将覆盖图像的标志。 在覆盖图像，请参阅备注部分中的信息。 MFC 默认实现中， `ILD_NORMAL`，使用的背景色为图像列表绘制图像。 如果背景色为`CLR_NONE`值，该图像绘制以透明方式使用掩码。  
  
 下面描述了其他可能的样式**fStyle**的成员[IMAGELISTDRAWPARAMS](http://msdn.microsoft.com/library/windows/desktop/bb761395)结构。  
  
 *dwRop*  
 值，该值指定的光栅操作代码。 这些代码定义如何源矩形的颜色数据组合在一起以实现最终颜色的目标矩形的颜色数据。 MFC 的默认实现中， **SRCCOPY**，将从源矩形复制直接到目标矩形。 如果忽略此参数`fStyle`参数不包括**ILD_ROP**标志。  
  
 其他可取的值描述下**dwRop**的成员[IMAGELISTDRAWPARAMS](http://msdn.microsoft.com/library/windows/desktop/bb761395)结构。  
  
 *rgbBack*  
 图像背景色，默认情况下的`CLR_DEFAULT`。 此参数可以是一个应用程序定义的 RGB 值或下列值之一︰  
  
|值|含义|  
|-----------|-------------|  
|`CLR_DEFAULT`|默认背景色。 使用图像列表的背景颜色绘制图像。|  
|`CLR_NONE`|没有背景色。 透明地绘制图像。|  
  
 *rgbFore*  
 默认情况下图像前景颜色`CLR_DEFAULT`。 此参数可以是一个应用程序定义的 RGB 值或下列值之一︰  
  
|值|含义|  
|-----------|-------------|  
|`CLR_DEFAULT`|默认前景色。 使用系统突出显示颜色作为的前景颜色绘制图像。|  
|`CLR_NONE`|无色 blend。 图像是与目标设备上下文的颜色混合。|  
  
 仅当使用此参数`fStyle`包括`ILD_BLEND25`或`ILD_BLEND50`标志。  
  
 *fState*  
 指定绘制对象的状态的标志。 此成员可以包含一个或多个图像列表状态标志。  
  
 *框架*  
 影响 saturate 和 alpha 混合效果的行为。  
  
 如果用于**ILS_SATURATE**，此成员保留添加到每个颜色部分中的每个像素的图标 RGB 三联数的值。  
  
 如果用于**ILS_APLHA**，此成员具有 alpha 通道的值。 此值可为从 0 到 255，0 表示完全透明，255 表示完全不透明。  
  
 *crEffect*  
 一个[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)值，该值用于发光和阴影效果。  
  
### <a name="return-value"></a>返回值  
 **TRUE**如果图像是成功绘制; 否则为**FALSE**。  
  
### <a name="remarks"></a>备注  
 如果您想要自己填充 Win32 结构，使用的第一个版本。 如果您想要利用的一个或多个 MFC 的默认参数，或避免管理这种结构，请使用第二个版本。  
  
 覆盖图像是由该成员函数中指定的主图像上方绘制的图像`nImage`参数。 通过使用上绘制覆盖掩码[绘制](#draw)成员函数时通过使用指定覆盖掩码的基于&1; 的索引[INDEXTOOVERLAYMASK](http://msdn.microsoft.com/library/windows/desktop/bb761408)宏。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CImageList #&11;](../../mfc/reference/codesnippet/cpp/cimagelist-class_10.cpp)]  
  
##  <a name="a-nameenddraga--cimagelistenddrag"></a><a name="enddrag"></a>CImageList::EndDrag  
 调用此函数以结束执行拖动操作。  
  
```  
static void PASCAL EndDrag();
```  
  
### <a name="remarks"></a>备注  
 若要开始拖动操作，请使用`BeginDrag`成员函数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CImageList #&5;](../../mfc/reference/codesnippet/cpp/cimagelist-class_11.cpp)]  
  
##  <a name="a-nameextracticona--cimagelistextracticon"></a><a name="extracticon"></a>CImageList::ExtractIcon  
 调用此函数可创建基于图像和图像列表中的其相关的掩码中的图标。  
  
```  
HICON ExtractIcon(int nImage);
```  
  
### <a name="parameters"></a>参数  
 `nImage`  
 图像的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 如果成功，则图标的句柄否则为**NULL**。  
  
### <a name="remarks"></a>备注  
 此方法的行为依赖于[ImageList_ExtractIcon](http://msdn.microsoft.com/library/windows/desktop/bb761401)宏以创建图标。 请参阅[ImageList_ExtractIcon](http://msdn.microsoft.com/library/windows/desktop/bb761401)图标创建和清理的详细信息的宏。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CImageList #&12;](../../mfc/reference/codesnippet/cpp/cimagelist-class_12.cpp)]  
  
##  <a name="a-namefromhandlea--cimagelistfromhandle"></a><a name="fromhandle"></a>CImageList::FromHandle  
 返回一个指向`CImageList`对象时提供给图像列表的句柄。  
  
```  
static CImageList* PASCAL FromHandle(HIMAGELIST hImageList);
```  
  
### <a name="parameters"></a>参数  
 `hImageList`  
 指定的图像列表。  
  
### <a name="return-value"></a>返回值  
 一个指向`CImageList`对象成功，否则为如果**NULL**。  
  
### <a name="remarks"></a>备注  
 如果`CImageList`尚未附加到该句柄，一种临时`CImageList`创建对象并将其连接。 此临时`CImageList`直到下一次应用程序在其事件循环内有空闲时间，在这段时间所有临时对象删除仅有效对象。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CImageList #&13;](../../mfc/reference/codesnippet/cpp/cimagelist-class_13.cpp)]  
  
##  <a name="a-namefromhandlepermanenta--cimagelistfromhandlepermanent"></a><a name="fromhandlepermanent"></a>CImageList::FromHandlePermanent  
 返回一个指向`CImageList`对象时提供给图像列表的句柄。  
  
```  
static CImageList* PASCAL FromHandlePermanent(HIMAGELIST hImageList);
```  
  
### <a name="parameters"></a>参数  
 `hImageList`  
 指定的图像列表。  
  
### <a name="return-value"></a>返回值  
 一个指向`CImageList`对象成功，否则为如果**NULL**。  
  
### <a name="remarks"></a>备注  
 如果`CImageList`对象未附加到该句柄， **NULL**返回。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CImageList #&14;](../../mfc/reference/codesnippet/cpp/cimagelist-class_14.cpp)]  
  
##  <a name="a-namegetbkcolora--cimagelistgetbkcolor"></a><a name="getbkcolor"></a>CImageList::GetBkColor  
 调用此函数可检索图像列表的当前背景色。  
  
```  
COLORREF GetBkColor() const;  
```  
  
### <a name="return-value"></a>返回值  
 RGB 颜色值的`CImageList`对象背景色。  
  
### <a name="example"></a>示例  
  请参阅示例[CImageList::SetBkColor](#setbkcolor)。  
  
##  <a name="a-namegetdragimagea--cimagelistgetdragimage"></a><a name="getdragimage"></a>CImageList::GetDragImage  
 获取用于拖动的临时图像列表。  
  
```  
static CImageList* PASCAL GetDragImage(
    LPPOINT lpPoint,  
    LPPOINT lpPointHotSpot);
```  
  
### <a name="parameters"></a>参数  
 `lpPoint`  
 地址的指针[点](http://msdn.microsoft.com/library/windows/desktop/dd162805)结构，它接收当前拖动位置。  
  
 *lpPointHotSpot*  
 地址的指针**点**结构，它接收拖动图像相对于拖动位置的偏移量。  
  
### <a name="return-value"></a>返回值  
 如果成功，指向临时图像的列表，用于拖动;否则为**NULL**。  
  
##  <a name="a-namegetimagecounta--cimagelistgetimagecount"></a><a name="getimagecount"></a>CImageList::GetImageCount  
 调用此函数可检索图像列表中的映像数。  
  
```  
int GetImageCount() const;  
```  
  
### <a name="return-value"></a>返回值  
 映像数量。  
  
### <a name="example"></a>示例  
  请参阅示例[CImageList::ExtractIcon](#extracticon)。  
  
##  <a name="a-namegetimageinfoa--cimagelistgetimageinfo"></a><a name="getimageinfo"></a>CImageList::GetImageInfo  
 调用此函数可检索有关某个映像的信息。  
  
```  
BOOL GetImageInfo(
    int nImage,  
    IMAGEINFO* pImageInfo) const;  
```  
  
### <a name="parameters"></a>参数  
 `nImage`  
 图像的从零开始索引。  
  
 *pImageInfo*  
 指向[IMAGEINFO](http://msdn.microsoft.com/library/windows/desktop/bb761393)结构，它接收有关映像的信息。 此结构中的信息可用于直接操作图像的位图。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 `IMAGEINFO`结构包含有关图像列表中的映像的信息。  
  
##  <a name="a-namegetsafehandlea--cimagelistgetsafehandle"></a><a name="getsafehandle"></a>CImageList::GetSafeHandle  
 调用此函数可检索**m_hImageList**数据成员。  
  
```  
HIMAGELIST GetSafeHandle() const;  
```  
  
### <a name="return-value"></a>返回值  
 附加的图像列表中; 句柄否则为**NULL**如果连接没有任何对象。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CImageList #&15;](../../mfc/reference/codesnippet/cpp/cimagelist-class_15.cpp)]  
  
##  <a name="a-namemhimagelista--cimagelistmhimagelist"></a><a name="m_himagelist"></a>CImageList::m_hImageList  
 图像列表附加到此对象的句柄。  
  
 **HIMAGELIST m_hImageList;**  
  
### <a name="remarks"></a>备注  
 **M_hImageList**数据成员是类型的公共变量`HIMAGELIST`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CImageList 第&23;](../../mfc/reference/codesnippet/cpp/cimagelist-class_16.cpp)]  
  
##  <a name="a-nameoperatorhimagelista--cimagelistoperator-himagelist"></a><a name="operator_himagelist"></a>CImageList::operator HIMAGELIST  
 使用此运算符将获取的连接句柄`CImageList`对象。  
  
```  
operator HIMAGELIST() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果成功，图像列表的句柄由表示`CImageList`对象; 否则为**NULL**。  
  
### <a name="remarks"></a>备注  
 此运算符被强制转换运算符，它支持直接使用`HIMAGELIST`对象。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CImageList #&16;](../../mfc/reference/codesnippet/cpp/cimagelist-class_17.cpp)]  
  
##  <a name="a-namereada--cimagelistread"></a><a name="read"></a>CImageList::Read  
 调用此函数可从存档中读取图像列表。  
  
```  
BOOL Read(CArchive* pArchive);
```  
  
### <a name="parameters"></a>参数  
 `pArchive`  
 一个指向`CArchive`对象是要读取的图像列表。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CImageList #&18;](../../mfc/reference/codesnippet/cpp/cimagelist-class_18.cpp)]  
  
##  <a name="a-nameremovea--cimagelistremove"></a><a name="remove"></a>CImageList::Remove  
 调用此函数可从图像列表对象中删除映像。  
  
```  
BOOL Remove(int nImage);
```  
  
### <a name="parameters"></a>参数  
 `nImage`  
 要删除的图像的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 后面的所有项`nImage`现在将下移一个位置。 例如，如果图像列表包含两个项，则删除的第一项将导致现在是在第一个位置中的其余项。 `nImage`=&0; 的第一个位置中的项。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CImageList #&19;](../../mfc/reference/codesnippet/cpp/cimagelist-class_19.cpp)]  
  
##  <a name="a-namereplacea--cimagelistreplace"></a><a name="replace"></a>CImageList::Replace  
 调用此函数可将图像列表中的图像替换为新映像。  
  
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
 `nImage`  
 要替换的图像的从零开始索引。  
  
 `pbmImage`  
 一个指向包含的图像的位图。  
  
 `pbmMask`  
 指向包含的蒙版位图的指针。 如果未应用蒙板的图像列表一起使用，则忽略此参数。  
  
 `hIcon`  
 指向包含位图和新图像的图标的句柄。  
  
### <a name="return-value"></a>返回值  
 返回的版本**BOOL**返回非零值，如果成功; 否则为 0。  
  
 返回的版本`int`返回图像的从零开始的索引; 如果成功; 否则为-1。  
  
### <a name="remarks"></a>备注  
 在调用后调用此成员函数[SetImageCount](#setimagecount)要分配给新，有效映像部署到占位符映像索引号。  
  
### <a name="example"></a>示例  
  请参阅示例[CImageList::SetImageCount](#setimagecount)。  
  
##  <a name="a-namesetbkcolora--cimagelistsetbkcolor"></a><a name="setbkcolor"></a>CImageList::SetBkColor  
 调用此函数可设置图像列表的背景色。  
  
```  
COLORREF SetBkColor(COLORREF cr);
```  
  
### <a name="parameters"></a>参数  
 `cr`  
 若要设置的背景色。 它可以是`CLR_NONE`。 在这种情况下，以透明方式使用掩码绘制图像。  
  
### <a name="return-value"></a>返回值  
 如果成功，则以前的背景颜色否则为`CLR_NONE`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CImageList #&20;](../../mfc/reference/codesnippet/cpp/cimagelist-class_20.cpp)]  
  
##  <a name="a-namesetdragcursorimagea--cimagelistsetdragcursorimage"></a><a name="setdragcursorimage"></a>CImageList::SetDragCursorImage  
 通过组合给定的图像 （通常是鼠标光标图像） 与当前拖动图像创建一个新的拖动图像。  
  
```  
BOOL SetDragCursorImage(
    int nDrag,  
    CPoint ptHotSpot);
```  
  
### <a name="parameters"></a>参数  
 *nDrag*  
 要结合拖动图像的新图像的索引。  
  
 `ptHotSpot`  
 新图像中作用点的位置。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 由于拖动函数将在拖动操作期间使用新的映像，您应使用 Windows [ShowCursor](http://msdn.microsoft.com/library/windows/desktop/ms648396)函数调用后隐藏实际鼠标光标`CImageList::SetDragCursorImage`。 否则，系统在拖动操作期间可能看起来具有两个鼠标光标。  
  
##  <a name="a-namesetimagecounta--cimagelistsetimagecount"></a><a name="setimagecount"></a>CImageList::SetImageCount  
 调用此成员函数以重置中的图像数`CImageList`对象。  
  
```  
BOOL SetImageCount(UINT uNewCount);
```  
  
### <a name="parameters"></a>参数  
 *uNewCount*  
 图像列表中指定新的映像的总数目的值。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="remarks"></a>备注  
 如果调用该成员函数以增加图像列表中的图像数，然后调用[替换](#replace)的每个其他映像将新的索引分配到有效的映像。 如果您不能将索引分配到有效的图像，描述创建新映像的操作将不可预知。  
  
 如果通过使用此函数减小图像列表的大小，则释放截断的图像。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CImageList #&21;](../../mfc/reference/codesnippet/cpp/cimagelist-class_21.cpp)]  
  
##  <a name="a-namesetoverlayimagea--cimagelistsetoverlayimage"></a><a name="setoverlayimage"></a>Cimagelist:: Setoverlayimage  
 调用此函数可将图像的从零开始的索引添加到映像以用作覆盖掩码的列表。  
  
```  
BOOL SetOverlayImage(
    int nImage,  
    int nOverlay);
```  
  
### <a name="parameters"></a>参数  
 `nImage`  
 要用作覆盖掩码的图像的从零开始索引。  
  
 *nOverlay*  
 覆盖掩码的基于&1; 的索引。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 最多四个索引可以被添加到列表。  
  
 覆盖掩码是在另一个图像上透明绘制的图像。 通过使用在图像上绘制覆盖掩码[cimagelist:: Draw](#draw)成员函数时通过使用指定覆盖掩码的基于&1; 的索引**INDEXTOOVERLAYMASK**宏。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CImageList #&22;](../../mfc/reference/codesnippet/cpp/cimagelist-class_22.cpp)]  
  
##  <a name="a-namewritea--cimagelistwrite"></a><a name="write"></a>CImageList::Write  
 调用此函数可写入存档的图像列表对象。  
  
```  
BOOL Write(CArchive* pArchive);
```  
  
### <a name="parameters"></a>参数  
 `pArchive`  
 一个指向`CArchive`对象是用来存储图像列表。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CImageList #&17;](../../mfc/reference/codesnippet/cpp/cimagelist-class_23.cpp)]  
  
## <a name="see-also"></a>另请参阅  
 [CObject 类](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CListCtrl 类](../../mfc/reference/clistctrl-class.md)   
 [CTabCtrl 类](../../mfc/reference/ctabctrl-class.md)

