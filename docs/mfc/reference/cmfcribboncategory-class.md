---
title: CMFCRibbonCategory 类
ms.date: 11/19/2018
f1_keywords:
- CMFCRibbonCategory
- AFXRIBBONCATEGORY/CMFCRibbonCategory
- AFXRIBBONCATEGORY/CMFCRibbonCategory::CMFCRibbonCategory
- AFXRIBBONCATEGORY/CMFCRibbonCategory::AddHidden
- AFXRIBBONCATEGORY/CMFCRibbonCategory::AddPanel
- AFXRIBBONCATEGORY/CMFCRibbonCategory::CopyFrom
- AFXRIBBONCATEGORY/CMFCRibbonCategory::FindByData
- AFXRIBBONCATEGORY/CMFCRibbonCategory::FindByID
- AFXRIBBONCATEGORY/CMFCRibbonCategory::FindPanelWithElem
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetContextID
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetData
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetDroppedDown
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetElements
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetElementsByID
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetFirstVisibleElement
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetFocused
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetHighlighted
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetImageCount
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetImageSize
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetItemIDsList
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetLastVisibleElement
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetLargeImages
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetMaxHeight
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetName
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetPanel
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetPanelCount
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetPanelFromPoint
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetPanelIndex
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetParentButton
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetParentMenuBar
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetParentRibbonBar
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetRect
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetSmallImages
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetTabColor
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetTabRect
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetTextTopLine
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetVisibleElements
- AFXRIBBONCATEGORY/CMFCRibbonCategory::HighlightPanel
- AFXRIBBONCATEGORY/CMFCRibbonCategory::HitTest
- AFXRIBBONCATEGORY/CMFCRibbonCategory::HitTestEx
- AFXRIBBONCATEGORY/CMFCRibbonCategory::HitTestScrollButtons
- AFXRIBBONCATEGORY/CMFCRibbonCategory::IsActive
- AFXRIBBONCATEGORY/CMFCRibbonCategory::IsVisible
- AFXRIBBONCATEGORY/CMFCRibbonCategory::IsWindows7Look
- AFXRIBBONCATEGORY/CMFCRibbonCategory::NotifyControlCommand
- AFXRIBBONCATEGORY/CMFCRibbonCategory::OnCancelMode
- AFXRIBBONCATEGORY/CMFCRibbonCategory::OnDraw
- AFXRIBBONCATEGORY/CMFCRibbonCategory::OnDrawImage
- AFXRIBBONCATEGORY/CMFCRibbonCategory::OnDrawMenuBorder
- AFXRIBBONCATEGORY/CMFCRibbonCategory::OnKey
- AFXRIBBONCATEGORY/CMFCRibbonCategory::OnLButtonDown
- AFXRIBBONCATEGORY/CMFCRibbonCategory::OnLButtonUp
- AFXRIBBONCATEGORY/CMFCRibbonCategory::OnMouseMove
- AFXRIBBONCATEGORY/CMFCRibbonCategory::OnRTLChanged
- AFXRIBBONCATEGORY/CMFCRibbonCategory::OnScrollHorz
- AFXRIBBONCATEGORY/CMFCRibbonCategory::OnUpdateCmdUI
- AFXRIBBONCATEGORY/CMFCRibbonCategory::RecalcLayout
- AFXRIBBONCATEGORY/CMFCRibbonCategory::RemovePanel
- AFXRIBBONCATEGORY/CMFCRibbonCategory::ReposPanels
- AFXRIBBONCATEGORY/CMFCRibbonCategory::SetCollapseOrder
- AFXRIBBONCATEGORY/CMFCRibbonCategory::SetData
- AFXRIBBONCATEGORY/CMFCRibbonCategory::SetKeys
- AFXRIBBONCATEGORY/CMFCRibbonCategory::SetName
- AFXRIBBONCATEGORY/CMFCRibbonCategory::SetTabColor
helpviewer_keywords:
- CMFCRibbonCategory [MFC], CMFCRibbonCategory
- CMFCRibbonCategory [MFC], AddHidden
- CMFCRibbonCategory [MFC], AddPanel
- CMFCRibbonCategory [MFC], CopyFrom
- CMFCRibbonCategory [MFC], FindByData
- CMFCRibbonCategory [MFC], FindByID
- CMFCRibbonCategory [MFC], FindPanelWithElem
- CMFCRibbonCategory [MFC], GetContextID
- CMFCRibbonCategory [MFC], GetData
- CMFCRibbonCategory [MFC], GetDroppedDown
- CMFCRibbonCategory [MFC], GetElements
- CMFCRibbonCategory [MFC], GetElementsByID
- CMFCRibbonCategory [MFC], GetFirstVisibleElement
- CMFCRibbonCategory [MFC], GetFocused
- CMFCRibbonCategory [MFC], GetHighlighted
- CMFCRibbonCategory [MFC], GetImageCount
- CMFCRibbonCategory [MFC], GetImageSize
- CMFCRibbonCategory [MFC], GetItemIDsList
- CMFCRibbonCategory [MFC], GetLastVisibleElement
- CMFCRibbonCategory [MFC], GetLargeImages
- CMFCRibbonCategory [MFC], GetMaxHeight
- CMFCRibbonCategory [MFC], GetName
- CMFCRibbonCategory [MFC], GetPanel
- CMFCRibbonCategory [MFC], GetPanelCount
- CMFCRibbonCategory [MFC], GetPanelFromPoint
- CMFCRibbonCategory [MFC], GetPanelIndex
- CMFCRibbonCategory [MFC], GetParentButton
- CMFCRibbonCategory [MFC], GetParentMenuBar
- CMFCRibbonCategory [MFC], GetParentRibbonBar
- CMFCRibbonCategory [MFC], GetRect
- CMFCRibbonCategory [MFC], GetSmallImages
- CMFCRibbonCategory [MFC], GetTabColor
- CMFCRibbonCategory [MFC], GetTabRect
- CMFCRibbonCategory [MFC], GetTextTopLine
- CMFCRibbonCategory [MFC], GetVisibleElements
- CMFCRibbonCategory [MFC], HighlightPanel
- CMFCRibbonCategory [MFC], HitTest
- CMFCRibbonCategory [MFC], HitTestEx
- CMFCRibbonCategory [MFC], HitTestScrollButtons
- CMFCRibbonCategory [MFC], IsActive
- CMFCRibbonCategory [MFC], IsVisible
- CMFCRibbonCategory [MFC], IsWindows7Look
- CMFCRibbonCategory [MFC], NotifyControlCommand
- CMFCRibbonCategory [MFC], OnCancelMode
- CMFCRibbonCategory [MFC], OnDraw
- CMFCRibbonCategory [MFC], OnDrawImage
- CMFCRibbonCategory [MFC], OnDrawMenuBorder
- CMFCRibbonCategory [MFC], OnKey
- CMFCRibbonCategory [MFC], OnLButtonDown
- CMFCRibbonCategory [MFC], OnLButtonUp
- CMFCRibbonCategory [MFC], OnMouseMove
- CMFCRibbonCategory [MFC], OnRTLChanged
- CMFCRibbonCategory [MFC], OnScrollHorz
- CMFCRibbonCategory [MFC], OnUpdateCmdUI
- CMFCRibbonCategory [MFC], RecalcLayout
- CMFCRibbonCategory [MFC], RemovePanel
- CMFCRibbonCategory [MFC], ReposPanels
- CMFCRibbonCategory [MFC], SetCollapseOrder
- CMFCRibbonCategory [MFC], SetData
- CMFCRibbonCategory [MFC], SetKeys
- CMFCRibbonCategory [MFC], SetName
- CMFCRibbonCategory [MFC], SetTabColor
ms.assetid: 99ba25b6-d060-4fdd-bfab-3c46c22981bb
ms.openlocfilehash: a1653242675db0e235b58f2c4865bb838753c484
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375264"
---
# <a name="cmfcribboncategory-class"></a>CMFCRibbonCategory 类

类`CMFCRibbonCategory`实现包含一组[功能区面板的功能区](../../mfc/reference/cmfcribbonpanel-class.md)选项卡。

## <a name="syntax"></a>语法

```
class CMFCRibbonCategory : public CObject
```

## <a name="members"></a>成员

### <a name="protected-constructors"></a>受保护的构造函数

|名称|说明|
|----------|-----------------|
|[CMFC 功能分类：CMFC 功能分类](#cmfcribboncategory)|构造函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMFC 功能分类：：添加隐藏](#addhidden)|向功能区类别添加隐藏元素。|
|[CMFC 功能分类：：添加面板](#addpanel)|向功能区类别添加新面板。|
|[CMFC 功能分类：：从](#copyfrom)||
|[CMFC 功能分类：：查找数据](#findbydata)||
|[CMFC 功能分类：：查找ByID](#findbyid)||
|[CMFC 功能分类：：查找面板与Elem](#findpanelwithelem)||
|[CMFC 功能分类：获取上下文 ID](#getcontextid)|返回功能区类别的上下文 ID。|
|[CMFC 功能分类：获取数据](#getdata)|返回与功能区类别关联的用户定义的数据。|
|[CMFC 功能分类：获取向下](#getdroppeddown)||
|[CMFC 功能分类：获取元素](#getelements)||
|[CMFC 功能分类类别：获取元素 ByID](#getelementsbyid)||
|[CMFC 功能分类：获取第一个可见元素](#getfirstvisibleelement)|获取属于功能区类别的第一个可见元素。|
|[CMFC 功能分类：获得重点](#getfocused)|返回焦点元素。|
|[CMFC 功能分类：获取突出显示](#gethighlighted)|返回突出显示的元素。|
|[CMFC 功能分类：获取图像计数](#getimagecount)||
|[CMFC 功能分类：获取图像大小](#getimagesize)||
|[CMFC 功能分类：获取项目 Id 列表](#getitemidslist)||
|[CMFC 功能分类类别：获取最后可见元素](#getlastvisibleelement)|获取属于功能区类别的最后一个可见元素|
|[CMFC 功能分类：获取大型图像](#getlargeimages)|返回对功能区类别使用的大型图像列表的引用。|
|[CMFC 功能分类：：获取最大高度](#getmaxheight)||
|[CMFC 功能分类：获取名称](#getname)||
|[CMFC 功能分类：获取面板](#getpanel)|返回指向位于指定索引的功能区面板的指针。|
|[CMFC 功能分类：：获取面板计数](#getpanelcount)|返回功能区类别中的功能区面板数。|
|[CMFC 功能类别：从点获取面板](#getpanelfrompoint)||
|[CMFC功能分类：获取面板索引](#getpanelindex)|返回指定功能区面板的索引。|
|[CMFCRibbonCategory::GetParentButton](#getparentbutton)||
|[CMFCRibbonCategory::GetParentMenuBar](#getparentmenubar)||
|[CMFC 功能分类类别：获取父系功能栏](#getparentribbonbar)||
|[CMFC 功能类别：获取 Rect](#getrect)||
|[CMFC 功能分类：获取小图像](#getsmallimages)|返回对类别使用的小图像列表的引用。|
|[CMFC 功能分类：：获取 TabColor](#gettabcolor)|返回功能区类别选项卡的当前颜色。|
|[CMFC 功能类别：获取 Tabrect](#gettabrect)||
|[CMFC 功能分类：：获取文本顶线](#gettexttopline)||
|[CMFC 功能分类：获取可见元素](#getvisibleelements)|获取属于功能区类别的所有可见元素。|
|[CMFC 功能分类：：高光面板](#highlightpanel)||
|[CMFC 功能分类：hitTest](#hittest)||
|[CMFC功能分类：hitTestEx](#hittestex)||
|[CMFCRibbonCategory::HitTestScrollButtons](#hittestscrollbuttons)||
|[CMFC 功能类别：有效](#isactive)||
|[CMFC 功能分类：可见](#isvisible)|确定功能区类别是否可见。|
|[CMFC 功能分类类别：：是 Windows7 查看](#iswindows7look)|指示父功能区是否有 Windows 7 样式的外观（小型矩形应用程序按钮）|
|[CMFCRibbonCategory::NotifyControlCommand](#notifycontrolcommand)||
|[CMFCRibbonCategory::OnCancelMode](#oncancelmode)||
|[CMFC 功能分类：：开拉](#ondraw)||
|[CMFC 功能分类：：画像](#ondrawimage)||
|[CMFC 功能分类：：在绘制菜单边框](#ondrawmenuborder)||
|[CMFC 功能类别：：打开键](#onkey)|当用户按下键盘按钮时，框架调用。|
|[CMFC 功能分类：：打开按钮](#onlbuttondown)||
|[CMFC 功能分类：：OnLButtonUp](#onlbuttonup)||
|[CMFC 功能分类：：鼠标移动](#onmousemove)||
|[CMFC 功能分类：：在RTL改变](#onrtlchanged)||
|[CMFC 功能分类：：ScrollHorz](#onscrollhorz)||
|[CMFCRibbonCategory::OnUpdateCmdUI](#onupdatecmdui)||
|[CMFC 功能分类：recalclayout](#recalclayout)||
|[CMFC 功能分类：：删除面板](#removepanel)||
|[CMFC 功能分类：：存储库面板](#repospanels)||
|[CMFC 功能分类类别：设置折叠顺序](#setcollapseorder)|定义功能区类别中存在的功能区面板的折叠顺序。|
|[CMFC 功能分类：：集数据](#setdata)|将用户定义的数据存储在功能区类别中。|
|[CMFC 功能分类：：设置密钥](#setkeys)|为功能区类别分配一个键尖。|
|[CMFC 功能分类：：设置名称](#setname)||
|[CMFC 功能分类：：设置 TabColor](#settabcolor)|设置功能区类别的颜色。|

## <a name="remarks"></a>备注

通常，通过调用[CMFCRibbonBar：：：addCategory](../../mfc/reference/cmfcribbonbar-class.md#addcategory)，间接创建功能区类别，该类别返回指向新创建的功能区类别的指针。 通过调用[CMFC 功能分类：：添加面板](#addpanel)，将面板添加到类别。

该`CMFCRibbonTab`类绘制功能区类别。 它派生自[CMFCRibbonBase元素类](../../mfc/reference/cmfcribbonbaseelement-class.md)。

以下示例演示如何创建功能区类别并将其添加面板。

```cpp
// Create a new ribbon category and get a pointer to it`
CMFCRibbonCategory* pCategory = m_wndRibbonBar.AddCategory
    (_T("&Write"),           // Category name
    IDB_WRITE,               // Category small images (16 x 16)
    IDB_WRITE_LARGE);        // Category large images (32 x 32)

// Add a panel to the new category
CMFCRibbonPanel* pPanel = pCategory->AddPanel (
    _T("Clipboard"),                // Panel name
    m_PanelIcons.ExtractIcon (0));  // Panel icon
```

下图显示了功能区应用示例应用程序中的"主页"类别的图形。

![功能区应用示例应用程序中的家庭类别](../../mfc/reference/media/cmfcribboncategory.png "功能区应用示例应用程序中的家庭类别")

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CMFCRibbonCategory`

## <a name="requirements"></a>要求

**标题：** afxribbon 类别.h

## <a name="cmfcribboncategoryaddhidden"></a><a name="addhidden"></a>CMFC 功能分类：：添加隐藏

将指定的功能区元素添加到自定义对话框中显示的功能区元素数组中。

```
void AddHidden(CMFCRibbonBaseElement* pElem);
```

### <a name="parameters"></a>参数

*佩莱姆*<br/>
[在]指向功能区元素的指针。

### <a name="remarks"></a>备注

自定义对话框上的功能区元素是可以添加到快速访问工具栏的命令。

## <a name="cmfcribboncategoryaddpanel"></a><a name="addpanel"></a>CMFC 功能分类：：添加面板

为功能区类别创建功能区面板。

```
CMFCRibbonPanel* AddPanel(
    LPCTSTR lpszPanelName,
    HICON hIcon = 0,
    CRuntimeClass* pRTI = NULL);
```

### <a name="parameters"></a>参数

*lpszPanel名称*<br/>
[在]指向新功能区面板的名称。

*hIcon*<br/>
[在]处理新功能区面板的默认图标。

*pRTI*<br/>
[在]指向自定义功能区面板的运行时类信息的指针。

### <a name="return-value"></a>返回值

如果方法成功，则指向新功能区面板的指针;否则 NULL，如果面板未创建。

### <a name="remarks"></a>备注

如果要创建自定义功能区面板，则必须在*pRTI*中指定其运行时类信息。 自定义功能区面板类必须派生自类`CMFCRibbonPanel`。

当功能区元素空间不足时，将显示功能区面板的默认图标。

### <a name="example"></a>示例

下面的示例演示如何在`AddPanel``CMFCRibbonCategory`类中使用 方法。

[!code-cpp[NVC_MFC_RibbonApp#10](../../mfc/reference/codesnippet/cpp/cmfcribboncategory-class_1.cpp)]

## <a name="cmfcribboncategorycmfcribboncategory"></a><a name="cmfcribboncategory"></a>CMFC 功能分类：CMFC 功能分类

构造并初始化[CMFC 功能分类对象](../../mfc/reference/cmfcribboncategory-class.md)。

```
CMFCRibbonCategory(
    CMFCRibbonBar* pParenrRibbonBar,
    LPCTSTR lpszName,
    UINT uiSmallImagesResID,
    UINT uiLargeImagesResID,
    CSize sizeSmallImage = CSize(16,
    16),
    CSize sizeLargeImage = CSize(32,
    32));
```

### <a name="parameters"></a>参数

*pParenr 带条*<br/>
[在]指向功能区类别的父功能区栏。

*lpsz名称*<br/>
[在]功能区类别的名称。

*ui 小图像雷斯ID*<br/>
[在]功能区类别中功能区元素使用的小图像图像列表的资源 ID。

*uiLargeImagesResID*<br/>
[在]功能区类别中功能区元素使用的大型图像的图像列表的资源 ID。

*大小 小图像*<br/>
[在]功能区类别中功能区元素的小图像的默认大小。

*大小大图像*<br/>
[在]功能区类别中功能区元素的大图像的默认大小。

## <a name="cmfcribboncategorycopyfrom"></a><a name="copyfrom"></a>CMFC 功能分类：：从

将指定的[CMFC 功能分类](../../mfc/reference/cmfcribboncategory-class.md)的状态复制到当前[CMFC 功能分类对象](../../mfc/reference/cmfcribboncategory-class.md)。

```
virtual void CopyFrom(CMFCRibbonCategory& src);
```

### <a name="parameters"></a>参数

*src*<br/>
[在]源`CMFCRibbonCategory`对象。

### <a name="remarks"></a>备注

## <a name="cmfcribboncategoryfindbydata"></a><a name="findbydata"></a>CMFC 功能分类：：查找数据

检索与指定数据关联的功能区元素。

```
CMFCRibbonBaseElement* FindByData(
    DWORD_PTR dwData,
    BOOL bVisibleOnly = TRUE) const;
```

### <a name="parameters"></a>参数

*dwData*<br/>
[在]与功能区元素关联的数据。

*仅可见*<br/>
[在]TRUE 在搜索中包括快速访问功能区元素;FALSE 以排除搜索中快速访问功能区元素。

### <a name="return-value"></a>返回值

如果方法成功，则指向功能区元素的指针;否则 NULL。

### <a name="remarks"></a>备注

## <a name="cmfcribboncategoryfindbyid"></a><a name="findbyid"></a>CMFC 功能分类：：查找ByID

检索与指定命令 ID 关联的功能区元素。

```
CMFCRibbonBaseElement* FindByID(
    UINT uiCmdID,
    BOOL bVisibleOnly = TRUE) const;
```

### <a name="parameters"></a>参数

*乌伊CmdID*<br/>
[在]与功能区元素关联的命令 ID。

*仅可见*<br/>
[在]TRUE 在搜索中包括快速访问功能区元素;FALSE 以排除搜索中快速访问功能区元素。

### <a name="return-value"></a>返回值

如果方法成功，则指向功能区元素的指针;否则 NULL。

### <a name="remarks"></a>备注

## <a name="cmfcribboncategoryfindpanelwithelem"></a><a name="findpanelwithelem"></a>CMFC 功能分类：：查找面板与Elem

检索包含指定功能区元素的功能区面板。

```
CMFCRibbonPanel* FindPanelWithElem(const CMFCRibbonBaseElement* pElement);
```

### <a name="parameters"></a>参数

*p元素*<br/>
[在]指向功能区元素的指针。

### <a name="return-value"></a>返回值

如果方法成功，则指向功能区面板的指针;否则 NULL。

### <a name="remarks"></a>备注

## <a name="cmfcribboncategorygetcontextid"></a><a name="getcontextid"></a>CMFC 功能分类：获取上下文 ID

检索功能区类别的上下文 ID。

```
UINT GetContextID() const;
```

### <a name="return-value"></a>返回值

功能区类别的上下文 ID。

### <a name="remarks"></a>备注

如果功能区类别不是上下文功能区类别，则上下文 ID 为 0。

## <a name="cmfcribboncategorygetdata"></a><a name="getdata"></a>CMFC 功能分类：获取数据

检索与功能区类别关联的用户定义的数据。

```
DWORD_PTR GetData() const;
```

### <a name="return-value"></a>返回值

与功能区类别关联的用户定义的数据。

## <a name="cmfcribboncategorygetdroppeddown"></a><a name="getdroppeddown"></a>CMFC 功能分类：获取向下

检索指向功能区元素的指针，该功能区元素当前显示其弹出式菜单。

```
CMFCRibbonBaseElement* GetDroppedDown();
```

### <a name="return-value"></a>返回值

如果方法成功，则指向功能区元素的指针;否则 NULL。

### <a name="remarks"></a>备注

## <a name="cmfcribboncategorygetelements"></a><a name="getelements"></a>CMFC 功能分类：获取元素

检索功能区类别中的所有功能区元素。

```
void GetElements(
    CArray <CMFCRibbonBaseElement*, CMFCRibbonBaseElement*>& arElements);
```

### <a name="parameters"></a>参数

*ar元素*<br/>
[进出]对功能区元素的[CArray](../../mfc/reference/carray-class.md)的引用。

### <a name="remarks"></a>备注

阵列中包含用于快速访问工具栏的功能区元素。

## <a name="cmfcribboncategorygetelementsbyid"></a><a name="getelementsbyid"></a>CMFC 功能分类类别：获取元素 ByID

检索与指定命令 ID 关联的所有功能区元素。

```
void GetElementsByID(
    UINT uiCmdID,
    CArray <CMFCRibbonBaseElement*, CMFCRibbonBaseElement*>& arElements);
```

### <a name="parameters"></a>参数

*乌伊CmdID*<br/>
[在]与功能区元素关联的命令 ID。

*ar元素*<br/>
[进出]对功能区元素的[CArray](../../mfc/reference/carray-class.md)的引用。

### <a name="remarks"></a>备注

阵列中包含用于快速访问工具栏的功能区元素。

## <a name="cmfcribboncategorygetfirstvisibleelement"></a><a name="getfirstvisibleelement"></a>CMFC 功能分类：获取第一个可见元素

检索属于功能区类别的第一个可见元素。

```
CMFCRibbonBaseElement* GetFirstVisibleElement() const;
```

### <a name="return-value"></a>返回值

指向第一个可见元素的指针;如果类别没有任何可见元素，则可能是 NULL。

### <a name="remarks"></a>备注

## <a name="cmfcribboncategorygetfocused"></a><a name="getfocused"></a>CMFC 功能分类：获得重点

返回焦点元素。

```
CMFCRibbonBaseElement* GetFocused();
```

### <a name="return-value"></a>返回值

指向焦点元素或 NULL 的指针。

### <a name="remarks"></a>备注

## <a name="cmfcribboncategorygethighlighted"></a><a name="gethighlighted"></a>CMFC 功能分类：获取突出显示

返回突出显示的元素。

```
CMFCRibbonBaseElement* GetHighlighted();
```

### <a name="return-value"></a>返回值

如果没有突出显示的元素，则指向突出显示的元素或 NULL 的指针。

### <a name="remarks"></a>备注

## <a name="cmfcribboncategorygetimagecount"></a><a name="getimagecount"></a>CMFC 功能分类：获取图像计数

检索功能区类别中包含的指定图像列表中的图像数。

```
int GetImageCount(BOOL bIsLargeImage) const;
```

### <a name="parameters"></a>参数

*bIsLargeImage*<br/>
[在]大图像列表中的图像数为 TRUE;FALSE 表示小图像列表中的图像数。

### <a name="return-value"></a>返回值

指定图像列表中的图像数。

### <a name="remarks"></a>备注

## <a name="cmfcribboncategorygetimagesize"></a><a name="getimagesize"></a>CMFC 功能分类：获取图像大小

检索功能区类别中包含的指定图像列表中的图像大小。

```
CSize GetImageSize(BOOL bIsLargeImage) const;
```

### <a name="parameters"></a>参数

*bIsLargeImage*<br/>
[在]大图像大小的真真;用于小图像大小的 FALSE。

### <a name="return-value"></a>返回值

指定图像列表中图像的大小。

### <a name="remarks"></a>备注

检索的大小包括全局图像比例因子。

## <a name="cmfcribboncategorygetitemidslist"></a><a name="getitemidslist"></a>CMFC 功能分类：获取项目 Id 列表

检索功能区类别中包含的功能区元素的命令 ID。

```
void GetItemIDsList(
    CList<UINT, UINT>& lstItems,
    BOOL bHiddenOnly = FALSE) const;
```

### <a name="parameters"></a>参数

*lstItem*<br/>
[出]功能区类别中功能区元素的命令 ID 列表。

*仅隐藏*<br/>
[在]TRUE 以排除功能区类别中功能区面板上显示的功能区元素;FALSE 以包括功能区类别中的所有功能区元素。

### <a name="remarks"></a>备注

## <a name="cmfcribboncategorygetlargeimages"></a><a name="getlargeimages"></a>CMFC 功能分类：获取大型图像

检索功能区类别中包含的大型图像的列表。

```
CMFCToolBarImages& GetLargeImages();
```

### <a name="return-value"></a>返回值

功能区类别中包含的大图像的列表。

## <a name="cmfcribboncategorygetlastvisibleelement"></a><a name="getlastvisibleelement"></a>CMFC 功能分类类别：获取最后可见元素

检索属于功能区类别的最后一个可见元素。

```
CMFCRibbonBaseElement* GetLastVisibleElement() const;
```

### <a name="return-value"></a>返回值

指向最后一个可见元素的指针;如果类别没有任何可见元素，则可能是 NULL。

### <a name="remarks"></a>备注

## <a name="cmfcribboncategorygetmaxheight"></a><a name="getmaxheight"></a>CMFC 功能分类：：获取最大高度

检索功能区类别中包含的功能区面板的最大高度。

```
int GetMaxHeight(CDC* pDC);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[在]指向功能区面板的设备上下文。

### <a name="return-value"></a>返回值

功能区类别中包含的功能区面板的最大高度。

### <a name="remarks"></a>备注

检索的值包括功能区面板的顶部和底部边距的高度。

## <a name="cmfcribboncategorygetname"></a><a name="getname"></a>CMFC 功能分类：获取名称

检索功能区类别的名称。

```
LPCTSTR GetName() const;
```

### <a name="return-value"></a>返回值

功能区类别的名称。

### <a name="remarks"></a>备注

## <a name="cmfcribboncategorygetpanel"></a><a name="getpanel"></a>CMFC 功能分类：获取面板

返回指向位于指定索引的功能区面板的指针。

```
CMFCRibbonPanel* GetPanel(int nIndex);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
[在]功能区面板的零基索引。

### <a name="return-value"></a>返回值

指向位于指定索引的功能区面板的指针。

### <a name="remarks"></a>备注

如果*nIndex*的范围不广，则引发异常。

## <a name="cmfcribboncategorygetpanelcount"></a><a name="getpanelcount"></a>CMFC 功能分类：：获取面板计数

返回功能区类别中的功能区面板数。

```
int GetPanelCount() const;
```

### <a name="return-value"></a>返回值

功能区类别中的功能区面板数。

## <a name="cmfcribboncategorygetpanelfrompoint"></a><a name="getpanelfrompoint"></a>CMFC 功能类别：从点获取面板

如果指定的点位于其中，则检索指向功能区面板的指针。

```
CMFCRibbonPanel* GetPanelFromPoint(CPoint point) const;
```

### <a name="parameters"></a>参数

*点*<br/>
[在]指针的 x 和 y 坐标，相对于窗口的左上角。

### <a name="return-value"></a>返回值

如果方法成功，则指向功能区面板的指针;否则 NULL。

### <a name="remarks"></a>备注

仅测试功能区类别中的功能区面板。

## <a name="cmfcribboncategorygetpanelindex"></a><a name="getpanelindex"></a>CMFC功能分类：获取面板索引

检索指定功能区面板的零基索引。

```
int GetPanelIndex(const CMFCRibbonPanel* pPanel) const;
```

### <a name="parameters"></a>参数

*p面板*<br/>
[在]指向功能区面板的指针。

### <a name="return-value"></a>返回值

如果方法成功，则指定功能区面板的零索引;否则 -1。

### <a name="remarks"></a>备注

仅搜索功能区类别中的功能区面板。

## <a name="cmfcribboncategorygetparentbutton"></a><a name="getparentbutton"></a>CMFC 功能分类类别：获取父按钮

检索功能区类别的父功能区元素。

```
CMFCRibbonBaseElement* GetParentButton() const;
```

### <a name="return-value"></a>返回值

返回指向父功能区元素的指针，如果没有父元素则返回 NULL。

### <a name="remarks"></a>备注

## <a name="cmfcribboncategorygetparentmenubar"></a><a name="getparentmenubar"></a>CMFC 功能分类类别：获取父菜单栏

返回指向对象父菜单栏的`CMFCRibbonCategory`指针。

```
CMFCRibbonPanelMenuBar* GetParentMenuBar() const;
```

### <a name="return-value"></a>返回值

返回`m_pParentMenuBar`受保护成员的内容。

### <a name="remarks"></a>备注

## <a name="cmfcribboncategorygetparentribbonbar"></a><a name="getparentribbonbar"></a>CMFC 功能分类类别：获取父系功能栏

检索功能区类别的父功能区栏。

```
CMFCRibbonBar* GetParentRibbonBar() const;
```

### <a name="return-value"></a>返回值

指向功能区类别的父功能区栏。

### <a name="remarks"></a>备注

## <a name="cmfcribboncategorygetrect"></a><a name="getrect"></a>CMFC 功能类别：获取 Rect

检索功能区类别的显示矩形。

```
CRect GetRect() const;
```

### <a name="return-value"></a>返回值

功能区类别的显示矩形。

### <a name="remarks"></a>备注

功能区类别的显示矩形不包括类别选项卡。

## <a name="cmfcribboncategorygetsmallimages"></a><a name="getsmallimages"></a>CMFC 功能分类：获取小图像

检索功能区类别中包含的小图像的列表。

```
CMFCToolBarImages& GetSmallImages();
```

### <a name="return-value"></a>返回值

功能区类别中包含的小图像的列表。

## <a name="cmfcribboncategorygettabcolor"></a><a name="gettabcolor"></a>CMFC 功能分类：：获取 TabColor

返回功能区类别选项卡的当前颜色。

```
AFX_RibbonCategoryColor GetTabColor() const;
```

### <a name="return-value"></a>返回值

功能区类别选项卡的当前颜色。

### <a name="remarks"></a>备注

返回的值可以是以下枚举值之一：

- AFX_CategoryColor_Red

- AFX_CategoryColor_Orange

- AFX_CategoryColor_Yellow

- AFX_CategoryColor_Green

- AFX_CategoryColor_Blue

- AFX_CategoryColor_Indigo

- AFX_CategoryColor_Violet

## <a name="cmfcribboncategorygettabrect"></a><a name="gettabrect"></a>CMFC 功能类别：获取 Tabrect

检索功能区类别选项卡的显示矩形。

```
CRect GetTabRect() const;
```

### <a name="return-value"></a>返回值

功能区类别选项卡的显示矩形。

### <a name="remarks"></a>备注

## <a name="cmfcribboncategorygettexttopline"></a><a name="gettexttopline"></a>CMFC 功能分类：：获取文本顶线

检索显示大图像的功能区类别中功能区按钮上文本的垂直位置。

```
int GetTextTopLine() const;
```

### <a name="return-value"></a>返回值

显示大图像的功能区按钮上的文本（以像素为单位）的垂直位置。

### <a name="remarks"></a>备注

## <a name="cmfcribboncategorygetvisibleelements"></a><a name="getvisibleelements"></a>CMFC 功能分类：获取可见元素

检索属于功能区类别的所有可见元素。

```
void GetVisibleElements(
    CArray <CMFCRibbonBaseElement*,
    CMFCRibbonBaseElement*>& arElements);
```

### <a name="parameters"></a>参数

*ar元素*<br/>
所有可见元素的数组。

### <a name="remarks"></a>备注

## <a name="cmfcribboncategoryhighlightpanel"></a><a name="highlightpanel"></a>CMFC 功能分类：：高光面板

突出显示指定的功能区面板。

```
CMFCRibbonPanel* HighlightPanel(
    CMFCRibbonPanel* pHLPanel,
    CPoint point);
```

### <a name="parameters"></a>参数

*pHL面板*<br/>
[在]指向功能区面板以突出显示。

*点*<br/>
[在]指针的 x 和 y 坐标，相对于窗口的左上角。

### <a name="return-value"></a>返回值

指向以前突出显示的功能区面板;否则 NULL，如果在调用此方法时没有突出显示功能区面板。

### <a name="remarks"></a>备注

有关突出显示功能区面板的详细信息，请参阅[CMFC 功能面板：：：高亮显示](../../mfc/reference/cmfcribbonpanel-class.md#highlight)。

## <a name="cmfcribboncategoryhittest"></a><a name="hittest"></a>CMFC 功能分类：hitTest

如果指定点位于其中，则检索指向功能区元素的指针。

```
CMFCRibbonBaseElement* HitTest(
    CPoint point,
    BOOL bCheckPanelCaption = FALSE) const;
```

### <a name="parameters"></a>参数

*点*<br/>
[在]鼠标指针相对于窗口左上角的 x 和 y 坐标。

*b检查面板标题*<br/>
[在]TRUE 以测试功能区面板标题;FALSE 以排除功能区面板标题。

### <a name="return-value"></a>返回值

如果方法成功，则指向功能区元素的指针;否则 NULL。

### <a name="remarks"></a>备注

仅测试功能区类别中的功能区元素。

## <a name="cmfcribboncategoryhittestex"></a><a name="hittestex"></a>CMFC功能分类：hitTestEx

如果指定点位于功能区元素中，则检索功能区元素的零基索引。

```
int HitTestEx(CPoint point) const;
```

### <a name="parameters"></a>参数

*点*<br/>
[在]鼠标指针相对于窗口左上角的 x 和 y 坐标。

### <a name="return-value"></a>返回值

如果方法成功，则功能区元素的零基索引;否则 -1。

### <a name="remarks"></a>备注

仅测试功能区类别中的功能区元素。

## <a name="cmfcribboncategoryhittestscrollbuttons"></a><a name="hittestscrollbuttons"></a>CMFC 功能分类类别：：HitTestScrollButton

如果某个点位于功能区类别的左或右滚动按钮内，则返回指向该按钮的指针。

```
CMFCRibbonBaseElement* HitTestScrollButtons(CPoint point) const;
```

### <a name="parameters"></a>参数

*点*<br/>
[在]要测试的点。

### <a name="return-value"></a>返回值

如果*点*位于功能区类别的左侧或右侧滚动按钮的边界矩形内，则返回指向该按钮的指针，否则返回 NULL。

### <a name="remarks"></a>备注

## <a name="cmfcribboncategoryisactive"></a><a name="isactive"></a>CMFC 功能类别：有效

指示功能区类别是否是功能区栏上的活动类别。

```
BOOL IsActive() const;
```

### <a name="return-value"></a>返回值

如果功能区类别为活动类别，则为 TRUE;如果功能区类别为活动类别，则为 TRUE。否则 FALSE。

### <a name="remarks"></a>备注

活动功能区类别显示其功能区面板。

## <a name="cmfcribboncategoryisvisible"></a><a name="isvisible"></a>CMFC 功能分类：可见

指示功能区类别是否可见。

```
BOOL IsVisible() const;
```

### <a name="return-value"></a>返回值

如果功能区类别可见，则为 TRUE;如果功能区类别可见，则为 TRUE。否则 FALSE。

### <a name="remarks"></a>备注

可见的功能区类别将显示类别选项卡。

## <a name="cmfcribboncategoryiswindows7look"></a><a name="iswindows7look"></a>CMFC 功能分类类别：：是 Windows7 查看

指示父功能区是否具有 Windows 7 外观（小型矩形应用程序按钮）。

```
BOOL IsWindows7Look() const;
```

### <a name="return-value"></a>返回值

如果父功能区具有 Windows 7 外观，则为 TRUE;如果父功能区具有 Windows 7 外观，则为 TRUE。否则 FALSE。

### <a name="remarks"></a>备注

## <a name="cmfcribboncategorynotifycontrolcommand"></a><a name="notifycontrolcommand"></a>CMFC 功能分类：：通知控制命令

将WM_NOTIFY命令消息传递到 中的所有`CMFCRibbonPanel``CMFCRibbonCategory`元素，直到消息得到处理。

```
virtual BOOL NotifyControlCommand(
    BOOL bAccelerator,
    int nNotifyCode,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>参数

*b加速器*<br/>
[在]如果此命令源自加速器，则为 TRUE，否则为 FALSE。

*nNotify代码*<br/>
[在]通知代码。

*wParam*<br/>
[在]消息的 WPARAM 字段。

*lParam*<br/>
[在]消息的 LPARAM 字段。

### <a name="return-value"></a>返回值

如果消息已处理，则返回 TRUE;如果未处理，则返回 FALSE。

### <a name="remarks"></a>备注

## <a name="cmfcribboncategoryoncancelmode"></a><a name="oncancelmode"></a>CMFC 功能分类：：打开取消模式

调用 的取消模式在`CMFCRibbonPanel`的所有元素。 `CMFCRibbonCategory`

```
virtual void OnCancelMode();
```

### <a name="remarks"></a>备注

## <a name="cmfcribboncategoryondraw"></a><a name="ondraw"></a>CMFC 功能分类：：开拉

由框架调用以绘制功能区类别。

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[在]指向功能区类别的设备上下文。

### <a name="remarks"></a>备注

## <a name="cmfcribboncategoryondrawimage"></a><a name="ondrawimage"></a>CMFC 功能分类：：画像

由框架调用以在功能区类别上绘制指定的图像。

```
virtual BOOL OnDrawImage(
    CDC* pDC,
    CRect rect,
    CMFCRibbonBaseElement* pElement,
    BOOL bIsLargeImage,
    BOOL nImageIndex,
    BOOL bCenter);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[在]指向图像的设备上下文。

*矩形*<br/>
[在]显示图像的矩形。

*p元素*<br/>
[在]指向包含图像的功能区元素的指针。

*bIsLargeImage*<br/>
[在]如果图像是大尺寸，则为 TRUE;如果图像大小较小，则 FALSE。

*n图像索引*<br/>
[在]功能区类别中包含的图像数组中图像的零基索引。

*b中心*<br/>
[在]TRUE 以将图像居中以显示矩形为中心;FALSE 以在显示矩形的左上角绘制图像。

### <a name="return-value"></a>返回值

如果方法成功，则为 TRUE;否则 FALSE。

### <a name="remarks"></a>备注

## <a name="cmfcribboncategoryondrawmenuborder"></a><a name="ondrawmenuborder"></a>CMFC 功能分类：：在绘制菜单边框

由框架调用以绘制弹出菜单的边框。

```
virtual void OnDrawMenuBorder(
    CDC* pDC,
    CMFCRibbonPanelMenuBar* pMenuBar);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[在]不使用此参数。

*pMenuBar*<br/>
[在]不使用此参数。

### <a name="remarks"></a>备注

默认情况下，此方法不执行任何操作。 重写此方法以绘制弹出菜单的边框。

## <a name="cmfcribboncategoryonkey"></a><a name="onkey"></a>CMFC 功能类别：：打开键

当用户按下键盘按钮时，框架调用。

```
virtual BOOL OnKey(UINT nChar);
```

### <a name="parameters"></a>参数

*n查尔*<br/>
用户按下的密钥的虚拟密钥代码。

### <a name="remarks"></a>备注

## <a name="cmfcribboncategoryonlbuttondown"></a><a name="onlbuttondown"></a>CMFC 功能分类：：打开按钮

当用户按下鼠标左键时，框架调用以在指定点下检索功能区元素。

```
virtual CMFCRibbonBaseElement* OnLButtonDown(CPoint point);
```

### <a name="parameters"></a>参数

*点*<br/>
[在]鼠标指针相对于窗口左上角的 x 和 y 坐标。

### <a name="return-value"></a>返回值

如果方法成功，则指向功能区元素的指针;否则 NULL。

### <a name="remarks"></a>备注

## <a name="cmfcribboncategoryonlbuttonup"></a><a name="onlbuttonup"></a>CMFC 功能分类：：OnLButtonUp

当用户释放鼠标左键且指针位于功能区类别上时，由框架调用。

```
virtual void OnLButtonUp(CPoint point);
```

### <a name="parameters"></a>参数

*点*<br/>
[在]指针的 x 和 y 坐标，相对于窗口的左上角。

### <a name="remarks"></a>备注

## <a name="cmfcribboncategoryonmousemove"></a><a name="onmousemove"></a>CMFC 功能分类：：鼠标移动

当指针在功能区栏上移动以更新功能区类别显示时，由框架调用。

```
virtual void OnMouseMove(CPoint point);
```

### <a name="parameters"></a>参数

*点*<br/>
[在]指针的 x 和 y 坐标，相对于窗口的左上角。

### <a name="remarks"></a>备注

## <a name="cmfcribboncategoryonrtlchanged"></a><a name="onrtlchanged"></a>CMFC 功能分类：：在RTL改变

当布局更改方向时由框架调用。

```
virtual void OnRTLChanged(BOOL bIsRTL);
```

### <a name="parameters"></a>参数

*比塞尔*<br/>
[在]如果布局从右到左，则为 TRUE;如果布局从右到左，则为 TRUE。如果布局从左到右，则 FALSE。

### <a name="remarks"></a>备注

此方法调整功能区类别中包含的所有功能区面板和功能区元素的布局。

## <a name="cmfcribboncategoryonscrollhorz"></a><a name="onscrollhorz"></a>CMFC 功能分类：：ScrollHorz

沿水平方向滚动功能区类别。

```
virtual BOOL OnScrollHorz(
    BOOL bScrollLeft,
    int nScrollOffset = 0);
```

### <a name="parameters"></a>参数

*bScroll左*<br/>
[在]TRUE 向左滚动;FALSE 向右滚动。

*nScroll 偏移*<br/>
[在]滚动距离（以像素为单位）。

### <a name="return-value"></a>返回值

如果功能区类别以水平方向移动，则为 TRUE;如果功能区类别以水平方向移动，则为 TRUE。否则 FALSE。

### <a name="remarks"></a>备注

## <a name="cmfcribboncategoryonupdatecmdui"></a><a name="onupdatecmdui"></a>CMFC 功能分类：：更新 CmdUI

调用`OnUpdateCmdUI`中`CMFCRibbonPanel``CMFCRibbonCategory`每个元素中的成员函数，以启用或禁用其中的用户界面元素。

```
virtual void OnUpdateCmdUI(
    CMFCRibbonCmdUI* pCmdUI,
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler);
```

### <a name="parameters"></a>参数

*pCmdUI*<br/>
[在]指向`CMFCRibbonCmdUI`指定要启用哪些用户界面元素和要禁用的对象的指针。

*p目标*<br/>
[在]指向控制用户界面元素启用或禁用的窗口的指针。

*b 禁用IfNoHndler*<br/>
[在]如果消息映射中未定义处理程序，则为禁用用户界面项;如果消息映射中未定义任何处理程序，则为 TRUE。否则，FALSE。

### <a name="remarks"></a>备注

## <a name="cmfcribboncategoryrecalclayout"></a><a name="recalclayout"></a>CMFC 功能分类：recalclayout

调整功能区类别上所有控件的布局。

```
virtual void RecalcLayout(CDC* pDC);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[在]指向功能区类别的设备上下文。

### <a name="remarks"></a>备注

## <a name="cmfcribboncategoryremovepanel"></a><a name="removepanel"></a>CMFC 功能分类：：删除面板

从功能区类别中删除功能区面板。

```cpp
BOOL RemovePanel(
    int nIndex,
    BOOL bDelete = TRUE);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
[在]要删除的面板的索引号。 通过调用[CMFC 功能分类：：获取面板索引](#getpanelindex)方法获得。

*b 删除*<br/>
[在]TRUE 从内存中删除面板对象;FALSE 以删除面板对象而不将其删除。

### <a name="return-value"></a>返回值

如果方法成功，则为 TRUE;否则，FALSE。

## <a name="cmfcribboncategoryrepospanels"></a><a name="repospanels"></a>CMFC 功能分类：：存储库面板

调整功能区类别中包含的功能区面板上所有控件的布局。

```
virtual void ReposPanels(CDC* pDC);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[在]指向功能区类别中包含的功能区面板的设备上下文。

### <a name="remarks"></a>备注

## <a name="cmfcribboncategorysetcollapseorder"></a><a name="setcollapseorder"></a>CMFC 功能分类类别：设置折叠顺序

定义功能区类别的功能区面板折叠的顺序。

```
void SetCollapseOrder(const CArray<int,int>& arCollapseOrder);
```

### <a name="parameters"></a>参数

*ar折叠顺序*<br/>
[在]指定折叠顺序。 该数组包含功能区面板的零基索引。

### <a name="remarks"></a>备注

库定义折叠顺序。 但是，您可以通过向类别提供指定折叠顺序的索引列表来自定义此行为。

当类别检测到必须折叠功能区面板时，它将查找指定列表中的下一个元素。 如果列表为空，或者您没有指定足够的元素，则类别将使用内部算法。

例如，该类别具有三个功能区面板，可以折叠多次，直到所有面板处于完全折叠状态。 您可以设置以下折叠顺序：0、0、2、2。 在这种情况下，类别将折叠面板 0 两次，面板 2 次。 索引为 1 的面板将保持未折叠状态。

### <a name="example"></a>示例

下面的示例演示如何在`SetCollapseOrder``CMFCRibbonCategory`类中使用 方法。 该示例演示如何为折叠顺序构造数组，以及如何将折叠顺序设置为功能区类别。

[!code-cpp[NVC_MFC_RibbonApp#13](../../mfc/reference/codesnippet/cpp/cmfcribboncategory-class_2.cpp)]

## <a name="cmfcribboncategorysetdata"></a><a name="setdata"></a>CMFC 功能分类：：集数据

将用户定义的数据设置为与功能区类别关联的数据。

```
void SetData(DWORD_PTR dwData);
```

### <a name="parameters"></a>参数

*dwData*<br/>
[在]用户定义的数据。

## <a name="cmfcribboncategorysetkeys"></a><a name="setkeys"></a>CMFC 功能分类：：设置密钥

为功能区类别分配一个键尖。

```
void SetKeys(LPCTSTR lpszKeys);
```

### <a name="parameters"></a>参数

*lpszKeys*<br/>
[在]键提示文本。

### <a name="remarks"></a>备注

当用户按下 Alt 键或 F10 键时，将显示钥匙提示。

## <a name="cmfcribboncategorysetname"></a><a name="setname"></a>CMFC 功能分类：：设置名称

为功能区类别分配名称和键尖。

```
void SetName(LPCTSTR lpszName);
```

### <a name="parameters"></a>参数

*lpsz名称*<br/>
[在]功能区类别的名称和键尖。

### <a name="remarks"></a>备注

要设置功能区类别的键尖，附加一个换行符序列，然后将键尖字符追加到*lpszName*。

## <a name="cmfcribboncategorysettabcolor"></a><a name="settabcolor"></a>CMFC 功能分类：：设置 TabColor

设置功能区类别的颜色。

```
void SetTabColor(AFX_RibbonCategoryColor color);
```

### <a name="parameters"></a>参数

*颜色*<br/>
[在]指定功能区类别的新颜色。

### <a name="remarks"></a>备注

颜色可以是以下值之一：

- AFX_CategoryColor_None

- AFX_CategoryColor_Red

- AFX_CategoryColor_Orange

- AFX_CategoryColor_Yellow

- AFX_CategoryColor_Green

- AFX_CategoryColor_Blue

- AFX_CategoryColor_Indigo

- AFX_CategoryColor_Violet

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CObject 类](../../mfc/reference/cobject-class.md)
