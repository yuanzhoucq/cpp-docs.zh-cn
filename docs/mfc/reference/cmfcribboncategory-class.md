---
title: "CMFCRibbonCategory 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonCategory class
ms.assetid: 99ba25b6-d060-4fdd-bfab-3c46c22981bb
caps.latest.revision: 38
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
ms.openlocfilehash: dccbaac6450985f0d5255a790d83f374b52f06f9
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcribboncategory-class"></a>CMFCRibbonCategory 类
`CMFCRibbonCategory`类实现包含一组功能区选项卡[功能区面板](../../mfc/reference/cmfcribbonpanel-class.md)。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCRibbonCategory : public CObject  
```  
  
## <a name="members"></a>成员  
  
### <a name="protected-constructors"></a>受保护的构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCRibbonCategory::CMFCRibbonCategory](#cmfcribboncategory)|构造函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CMFCRibbonCategory::AddHidden](#addhidden)|将隐藏的元素添加到功能区类别。|  
|[CMFCRibbonCategory::AddPanel](#addpanel)|将一个新的面板添加到功能区类别。|  
|[CMFCRibbonCategory::CopyFrom](#copyfrom)||  
|[CMFCRibbonCategory::FindByData](#findbydata)||  
|[CMFCRibbonCategory::FindByID](#findbyid)||  
|[CMFCRibbonCategory::FindPanelWithElem](#findpanelwithelem)||  
|[CMFCRibbonCategory::GetContextID](#getcontextid)|返回功能区类别的上下文 ID。|  
|[CMFCRibbonCategory::GetData](#getdata)|返回与功能区类别相关联的用户定义的数据。|  
|[CMFCRibbonCategory::GetDroppedDown](#getdroppeddown)||  
|[CMFCRibbonCategory::GetElements](#getelements)||  
|[CMFCRibbonCategory::GetElementsByID](#getelementsbyid)||  
|[CMFCRibbonCategory::GetFirstVisibleElement](#getfirstvisibleelement)|获取属于功能区类别的第一个可见元素。|  
|[CMFCRibbonCategory::GetFocused](#getfocused)|返回焦点元素。|  
|[CMFCRibbonCategory::GetHighlighted](#gethighlighted)|返回一个突出显示的元素。|  
|[CMFCRibbonCategory::GetImageCount](#getimagecount)||  
|[CMFCRibbonCategory::GetImageSize](#getimagesize)||  
|[CMFCRibbonCategory::GetItemIDsList](#getitemidslist)||  
|[CMFCRibbonCategory::GetLastVisibleElement](#getlastvisibleelement)|获取属于功能区类别的最后一个可见元素|  
|[CMFCRibbonCategory::GetLargeImages](#getlargeimages)|返回到功能区类别将使用的大型图像列表的引用。|  
|[CMFCRibbonCategory::GetMaxHeight](#getmaxheight)||  
|[CMFCRibbonCategory::GetName](#getname)||  
|[CMFCRibbonCategory::GetPanel](#getpanel)|返回指向功能区面板，它位于指定索引处的指针。|  
|[CMFCRibbonCategory::GetPanelCount](#getpanelcount)|返回功能区类别中的功能区面板的数目。|  
|[CMFCRibbonCategory::GetPanelFromPoint](#getpanelfrompoint)||  
|[CMFCRibbonCategory::GetPanelIndex](#getpanelindex)|返回指定的功能区面板的索引。|  
|[CMFCRibbonCategory::GetParentButton](#getparentbutton)||  
|[CMFCRibbonCategory::GetParentMenuBar](#getparentmenubar)||  
|[CMFCRibbonCategory::GetParentRibbonBar](#getparentribbonbar)||  
|[CMFCRibbonCategory::GetRect](#getrect)||  
|[CMFCRibbonCategory::GetSmallImages](#getsmallimages)|返回到列表中的类别使用小图像的引用。|  
|[CMFCRibbonCategory::GetTabColor](#gettabcolor)|返回功能区类别选项卡的当前颜色。|  
|[CMFCRibbonCategory::GetTabRect](#gettabrect)||  
|[CMFCRibbonCategory::GetTextTopLine](#gettexttopline)||  
|[CMFCRibbonCategory::GetVisibleElements](#getvisibleelements)|获取属于功能区类别的所有可见元素。|  
|[CMFCRibbonCategory::HighlightPanel](#highlightpanel)||  
|[CMFCRibbonCategory::HitTest](#hittest)||  
|[CMFCRibbonCategory::HitTestEx](#hittestex)||  
|[CMFCRibbonCategory::HitTestScrollButtons](#hittestscrollbuttons)||  
|[CMFCRibbonCategory::IsActive](#isactive)||  
|[CMFCRibbonCategory::IsVisible](#isvisible)|确定功能区类别是否可见。|  
|[CMFCRibbonCategory::IsWindows7Look](#iswindows7look)|指示父功能区是否有 Windows 7 样式外观 （矩形的小型应用程序按钮）|  
|[CMFCRibbonCategory::NotifyControlCommand](#notifycontrolcommand)||  
|[CMFCRibbonCategory::OnCancelMode](#oncancelmode)||  
|[CMFCRibbonCategory::OnDraw](#ondraw)||  
|[CMFCRibbonCategory::OnDrawImage](#ondrawimage)||  
|[CMFCRibbonCategory::OnDrawMenuBorder](#ondrawmenuborder)||  
|[CMFCRibbonCategory::OnKey](#onkey)|当用户按下键盘按钮时由框架调用。|  
|[CMFCRibbonCategory::OnLButtonDown](#onlbuttondown)||  
|[CMFCRibbonCategory::OnLButtonUp](#onlbuttonup)||  
|[CMFCRibbonCategory::OnMouseMove](#onmousemove)||  
|[CMFCRibbonCategory::OnRTLChanged](#onrtlchanged)||  
|[CMFCRibbonCategory::OnScrollHorz](#onscrollhorz)||  
|[CMFCRibbonCategory::OnUpdateCmdUI](#onupdatecmdui)||  
|[CMFCRibbonCategory::RecalcLayout](#recalclayout)||  
|[CMFCRibbonCategory::RemovePanel](#removepanel)||  
|[CMFCRibbonCategory::ReposPanels](#repospanels)||  
|[CMFCRibbonCategory::SetCollapseOrder](#setcollapseorder)|定义功能区类别中存在的功能区面板的折叠顺序。|  
|[CMFCRibbonCategory::SetData](#setdata)|将用户定义的数据存储在功能区类别。|  
|[CMFCRibbonCategory::SetKeys](#setkeys)|将快捷键提示分配给功能区类别。|  
|[CMFCRibbonCategory::SetName](#setname)||  
|[CMFCRibbonCategory::SetTabColor](#settabcolor)|设置功能区类别的颜色。|  
  
## <a name="remarks"></a>备注  
 通常情况下，您创建功能区类别间接通过调用[CMFCRibbonBar::AddCategory](../../mfc/reference/cmfcribbonbar-class.md#addcategory)，它将指针返回到新创建的功能区类别。 通过调用添加到类别面板[CMFCRibbonCategory::AddPanel](#addpanel)。  
  
 `CMFCRibbonTab`类绘制功能区类别。 派生自[CMFCRibbonBaseElement 类](../../mfc/reference/cmfcribbonbaseelement-class.md)。  
  
 下面的示例演示如何创建一个功能区类别并向其中添加一个面板。  
  
 `// Create a new ribbon category and get a pointer to it`  
  
 `CMFCRibbonCategory* pCategory = m_wndRibbonBar.AddCategory`  
  
 `(_T("&Write"),           // Category name`  
  
 `IDB_WRITE,              // Category small images (16 x 16)`  
  
 `IDB_WRITE_LARGE);   // Category large images (32 x 32)`  
  
 `// Add a panel to the new category`  
  
 `CMFCRibbonPanel* pPanel = pCategory->AddPanel (`  
  
 `_T("Clipboard"),                       // Panel name`  
  
 `m_PanelIcons.ExtractIcon (0));  // Panel icon`  
  
 下图显示的图 RibbonApp 示例应用程序的主页类别。  
  
 ![CMFCRibbonCategory 图像](../../mfc/reference/media/cmfcribboncategory.png "cmfcribboncategory")  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMFCRibbonCategory`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxribboncategory.h  
  
##  <a name="addhidden"></a>CMFCRibbonCategory::AddHidden  
 将指定的功能区元素添加到显示在自定义对话框中的功能区元素的数组。  
  
```  
void AddHidden(CMFCRibbonBaseElement* pElem);
```  
  
### <a name="parameters"></a>参数  
 [in] `pElem`  
 指向功能区元素的指针。  
  
### <a name="remarks"></a>备注  
 在自定义对话框中的功能区元素是您可以将其添加到快速访问工具栏的命令。  
  
##  <a name="addpanel"></a>CMFCRibbonCategory::AddPanel  
 创建一个用于显示功能区类别的功能区面板。  
  
```  
CMFCRibbonPanel* AddPanel(
    LPCTSTR lpszPanelName,  
    HICON hIcon = 0,  
    CRuntimeClass* pRTI = NULL);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszPanelName`  
 一个指针，指向新的功能区面板的名称。  
  
 [in] `hIcon`  
 新的功能区面板的默认图标的句柄。  
  
 [in] `pRTI`  
 自定义功能区面板的运行时类信息的指针。  
  
### <a name="return-value"></a>返回值  
 如果此方法已成功，则将新功能区面板的指针否则为`NULL`如果未创建面板。  
  
### <a name="remarks"></a>备注  
 如果你想要创建一个自定义功能区面板，则必须指定在其运行时类信息`pRTI`。 自定义功能区面板类必须派生自`CMFCRibbonPanel`类。  
  
 若要显示功能区元素的空间不足时，将显示功能区面板中的默认图标。  
  
### <a name="example"></a>示例  
 下面的示例演示如何使用`AddPanel`中的方法`CMFCRibbonCategory`类。  
  
 [!code-cpp[NVC_MFC_RibbonApp #&10;](../../mfc/reference/codesnippet/cpp/cmfcribboncategory-class_1.cpp)]  
  
##  <a name="cmfcribboncategory"></a>CMFCRibbonCategory::CMFCRibbonCategory  
 构造并初始化[CMFCRibbonCategory](../../mfc/reference/cmfcribboncategory-class.md)对象。  
  
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
 [in] `pParenrRibbonBar`  
 功能区类别在父功能区栏的指针。  
  
 [in] `lpszName`  
 功能区类别的名称。  
  
 [in] `uiSmallImagesResID`  
 功能区类别中的功能区元素使用的小图像的图像列表的资源 ID。  
  
 [in] `uiLargeImagesResID`  
 功能区类别中的功能区元素使用的大型图像的图像列表的资源 ID。  
  
 [in] `sizeSmallImage`  
 默认的功能区类别中的功能区元素的小图像的大小。  
  
 [in] `sizeLargeImage`  
 默认功能区类别中的功能区元素的大图像的大小。  
  
##  <a name="copyfrom"></a>CMFCRibbonCategory::CopyFrom  
 将指定的状态复制[CMFCRibbonCategory](../../mfc/reference/cmfcribboncategory-class.md)与当前[CMFCRibbonCategory](../../mfc/reference/cmfcribboncategory-class.md)对象。  
  
```  
virtual void CopyFrom(CMFCRibbonCategory& src);
```  
  
### <a name="parameters"></a>参数  
 [in] `src`  
 源 `CMFCRibbonCategory` 对象。  
  
### <a name="remarks"></a>备注  
  
##  <a name="findbydata"></a>CMFCRibbonCategory::FindByData  
 检索与指定的数据相关联的功能区元素。  
  
```  
CMFCRibbonBaseElement* FindByData(
    DWORD_PTR dwData,  
    BOOL bVisibleOnly = TRUE) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `dwData`  
 与功能区元素关联的数据。  
  
 [in] `bVisibleOnly`  
 `TRUE`若要在搜索; 中包括的快速访问功能区元素`FALSE`若要排除在搜索中的快速访问功能区元素。  
  
### <a name="return-value"></a>返回值  
 如果此方法已成功，则为功能区元素的指针否则为`NULL`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="findbyid"></a>CMFCRibbonCategory::FindByID  
 检索与指定的命令 ID 相关联的功能区元素  
  
```  
CMFCRibbonBaseElement* FindByID(
    UINT uiCmdID,  
    BOOL bVisibleOnly = TRUE) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `uiCmdID`  
 与功能区元素相关联的命令 ID。  
  
 [in] `bVisibleOnly`  
 `TRUE`若要在搜索; 中包括的快速访问功能区元素`FALSE`若要排除在搜索中的快速访问功能区元素。  
  
### <a name="return-value"></a>返回值  
 如果此方法已成功，则为功能区元素的指针否则为`NULL`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="findpanelwithelem"></a>CMFCRibbonCategory::FindPanelWithElem  
 检索包含指定的功能区元素的功能区面板。  
  
```  
CMFCRibbonPanel* FindPanelWithElem(const CMFCRibbonBaseElement* pElement);
```  
  
### <a name="parameters"></a>参数  
 [in] `pElement`  
 指向功能区元素的指针。  
  
### <a name="return-value"></a>返回值  
 如果此方法已成功，则功能区面板的指针否则为`NULL`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getcontextid"></a>CMFCRibbonCategory::GetContextID  
 检索功能区类别的上下文 ID。  
  
```  
UINT GetContextID() const;  
```  
  
### <a name="return-value"></a>返回值  
 功能区类别的上下文 ID。  
  
### <a name="remarks"></a>备注  
 如果功能区类别不是一个上下文功能区类别，上下文 ID 为 0。  
  
##  <a name="getdata"></a>CMFCRibbonCategory::GetData  
 检索与功能区类别相关联的用户定义的数据。  
  
```  
DWORD_PTR GetData() const;  
```  
  
### <a name="return-value"></a>返回值  
 用户定义的数据与功能区类别相关联。  
  
##  <a name="getdroppeddown"></a>CMFCRibbonCategory::GetDroppedDown  
 检索指向当前具有其弹出菜单的显示功能区元素的指针。  
  
```  
CMFCRibbonBaseElement* GetDroppedDown();
```  
  
### <a name="return-value"></a>返回值  
 如果此方法已成功，则为功能区元素的指针否则为`NULL`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getelements"></a>CMFCRibbonCategory::GetElements  
 检索在功能区类别中的所有功能区元素。  
  
```  
void GetElements(
    CArray <CMFCRibbonBaseElement*, CMFCRibbonBaseElement*>& arElements);
```  
  
### <a name="parameters"></a>参数  
 [in, out] `arElements`  
 引用[CArray](../../mfc/reference/carray-class.md)的功能区元素。  
  
### <a name="remarks"></a>备注  
 设计用于快速访问工具栏的功能区元素包括在数组中。  
  
##  <a name="getelementsbyid"></a>CMFCRibbonCategory::GetElementsByID  
 检索与指定的命令 ID 相关联的所有功能区元素  
  
```  
void GetElementsByID(
    UINT uiCmdID,  
    CArray <CMFCRibbonBaseElement*, CMFCRibbonBaseElement*>& arElements);
```  
  
### <a name="parameters"></a>参数  
 [in] `uiCmdID`  
 与功能区元素相关联的命令 ID。  
  
 [in, out] `arElements`  
 引用[CArray](../../mfc/reference/carray-class.md)的功能区元素。  
  
### <a name="remarks"></a>备注  
 设计用于快速访问工具栏的功能区元素包括在数组中。  
  
##  <a name="getfirstvisibleelement"></a>CMFCRibbonCategory::GetFirstVisibleElement  
 检索属于功能区类别的第一个可见元素。  
  
```  
CMFCRibbonBaseElement* GetFirstVisibleElement() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向第一个可见元素;可能是`NULL`如果类别不具有任何可见元素。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getfocused"></a>CMFCRibbonCategory::GetFocused  
 返回焦点元素。  
  
```  
CMFCRibbonBaseElement* GetFocused();
```  
  
### <a name="return-value"></a>返回值  
 指向具有焦点的元素的指针或`NULL`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="gethighlighted"></a>CMFCRibbonCategory::GetHighlighted  
 返回一个突出显示的元素。  
  
```  
CMFCRibbonBaseElement* GetHighlighted();
```  
  
### <a name="return-value"></a>返回值  
 突出显示元素的指针或`NULL`如果突出不显示任何元素。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getimagecount"></a>CMFCRibbonCategory::GetImageCount  
 检索功能区类别中包含的指定的图像列表中的映像的数量。  
  
```  
int GetImageCount(BOOL bIsLargeImage) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `bIsLargeImage`  
 `TRUE`对于大型图像列表中; 中的映像数`FALSE`的小图像列表中的图像数。  
  
### <a name="return-value"></a>返回值  
 指定的图像列表中的图像数。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getimagesize"></a>CMFCRibbonCategory::GetImageSize  
 检索指定的图像列表包含在功能区类别中的图像的大小。  
  
```  
CSize GetImageSize(BOOL bIsLargeImage) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `bIsLargeImage`  
 `TRUE`对于大型图像; 的大小`FALSE`的较小的图像的大小。  
  
### <a name="return-value"></a>返回值  
 在指定的图像列表中的图像的大小。  
  
### <a name="remarks"></a>备注  
 检索到的大小包括全局映像比例因子。  
  
##  <a name="getitemidslist"></a>CMFCRibbonCategory::GetItemIDsList  
 检索包含在功能区类别中的功能区元素的命令 Id。  
  
```  
void GetItemIDsList(
    CList<UINT, UINT>& lstItems,  
    BOOL bHiddenOnly = FALSE) const;  
```  
  
### <a name="parameters"></a>参数  
 [out] `lstItems`  
 功能区类别中的功能区元素的命令 Id 的列表。  
  
 [in] `bHiddenOnly`  
 `TRUE`若要排除的功能区类别; 中的功能区面板上显示的功能区元素`FALSE`在功能区类别中包括所有功能区元素。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getlargeimages"></a>CMFCRibbonCategory::GetLargeImages  
 检索包含在功能区类别中的大型映像的列表。  
  
```  
CMFCToolBarImages& GetLargeImages();
```  
  
### <a name="return-value"></a>返回值  
 功能区类别中包含的大型映像的列表。  
  
##  <a name="getlastvisibleelement"></a>CMFCRibbonCategory::GetLastVisibleElement  
 检索最后一个功能区类别所属的可见元素。  
  
```  
CMFCRibbonBaseElement* GetLastVisibleElement() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向最后一个可见元素;可能是`NULL`如果类别不具有任何可见元素。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getmaxheight"></a>CMFCRibbonCategory::GetMaxHeight  
 检索包含在功能区类别中的功能区面板的最大高度。  
  
```  
int GetMaxHeight(CDC* pDC);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 功能区面板的设备上下文的指针。  
  
### <a name="return-value"></a>返回值  
 功能区类别中包含的功能区面板最大高度。  
  
### <a name="remarks"></a>备注  
 检索到的值包括功能区面板的顶部和底部边距的高度。  
  
##  <a name="getname"></a>CMFCRibbonCategory::GetName  
 检索功能区类别的名称。  
  
```  
LPCTSTR GetName() const;  
```  
  
### <a name="return-value"></a>返回值  
 功能区类别的名称。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getpanel"></a>CMFCRibbonCategory::GetPanel  
 返回指向功能区面板，它位于指定索引处的指针。  
  
```  
CMFCRibbonPanel* GetPanel(int nIndex);
```  
  
### <a name="parameters"></a>参数  
 [in] `nIndex`  
 功能区面板的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 指针，指向功能区面板中，它位于指定索引处。  
  
### <a name="remarks"></a>备注  
 如果引发异常`nIndex`超出范围。  
  
##  <a name="getpanelcount"></a>CMFCRibbonCategory::GetPanelCount  
 返回功能区类别中的功能区面板的数目。  
  
```  
int GetPanelCount() const;  
```  
  
### <a name="return-value"></a>返回值  
 功能区中的面板功能区类别数。  
  
##  <a name="getpanelfrompoint"></a>CMFCRibbonCategory::GetPanelFromPoint  
 如果指定的点位于，检索到功能区面板的指针。  
  
```  
CMFCRibbonPanel* GetPanelFromPoint(CPoint point) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `point`  
 X 和 y 坐标相对于窗口的左上角的指针。  
  
### <a name="return-value"></a>返回值  
 如果此方法已成功，则功能区面板的指针否则为`NULL`。  
  
### <a name="remarks"></a>备注  
 仅在功能区类别中包含的功能区面板进行测试。  
  
##  <a name="getpanelindex"></a>CMFCRibbonCategory::GetPanelIndex  
 检索指定的功能区面板的从零开始索引。  
  
```  
int GetPanelIndex(const CMFCRibbonPanel* pPanel) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `pPanel`  
 指向功能区面板的指针。  
  
### <a name="return-value"></a>返回值  
 如果此方法已成功，则将指定的功能区面板的从零开始的索引否则为-1。  
  
### <a name="remarks"></a>备注  
 仅在功能区类别中包含的功能区面板中搜索。  
  
##  <a name="getparentbutton"></a>CMFCRibbonCategory::GetParentButton  
 检索功能区类别的父功能区元素。  
  
```  
CMFCRibbonBaseElement* GetParentButton() const;  
```  
  
### <a name="return-value"></a>返回值  
 返回指向父功能区元素的指针或`NULL`如果没有父元素。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getparentmenubar"></a>CMFCRibbonCategory::GetParentMenuBar  
 将指针返回到父菜单栏的`CMFCRibbonCategory`对象。  
  
```  
CMFCRibbonPanelMenuBar* GetParentMenuBar() const;  
```  
  
### <a name="return-value"></a>返回值  
 返回的内容`m_pParentMenuBar`受保护的成员。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getparentribbonbar"></a>CMFCRibbonCategory::GetParentRibbonBar  
 检索功能区类别的父功能区栏。  
  
```  
CMFCRibbonBar* GetParentRibbonBar() const;  
```  
  
### <a name="return-value"></a>返回值  
 功能区类别在父功能区栏的指针。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getrect"></a>CMFCRibbonCategory::GetRect  
 检索功能区类别显示矩形。  
  
```  
CRect GetRect() const;  
```  
  
### <a name="return-value"></a>返回值  
 功能区类别显示矩形。  
  
### <a name="remarks"></a>备注  
 功能区类别的显示矩形不包括类别选项卡。  
  
##  <a name="getsmallimages"></a>CMFCRibbonCategory::GetSmallImages  
 检索包含在功能区类别中的小图像的列表。  
  
```  
CMFCToolBarImages& GetSmallImages();
```  
  
### <a name="return-value"></a>返回值  
 功能区类别中包含的小图像的列表。  
  
##  <a name="gettabcolor"></a>CMFCRibbonCategory::GetTabColor  
 返回功能区类别选项卡的当前颜色。  
  
```  
AFX_RibbonCategoryColor GetTabColor() const;  
```  
  
### <a name="return-value"></a>返回值  
 功能区类别选项卡的当前颜色。  
  
### <a name="remarks"></a>备注  
 返回的值可以是下列枚举值之一︰  
  
-   AFX_CategoryColor_Red  
  
-   AFX_CategoryColor_Orange  
  
-   AFX_CategoryColor_Yellow  
  
-   AFX_CategoryColor_Green  
  
-   AFX_CategoryColor_Blue  
  
-   AFX_CategoryColor_Indigo  
  
-   AFX_CategoryColor_Violet  
  
##  <a name="gettabrect"></a>CMFCRibbonCategory::GetTabRect  
 检索功能区类别选项卡显示矩形。  
  
```  
CRect GetTabRect() const;  
```  
  
### <a name="return-value"></a>返回值  
 功能区类别选项卡显示矩形。  
  
### <a name="remarks"></a>备注  
  
##  <a name="gettexttopline"></a>CMFCRibbonCategory::GetTextTopLine  
 检索在功能区类别中显示图像的大小的功能区按钮上的文本的垂直位置。  
  
```  
int GetTextTopLine() const;  
```  
  
### <a name="return-value"></a>返回值  
 垂直文本，以像素为单位，在显示大型映像的功能区按钮上的位置。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getvisibleelements"></a>CMFCRibbonCategory::GetVisibleElements  
 检索属于功能区类别的所有可见元素。  
  
```  
void GetVisibleElements(
    CArray <CMFCRibbonBaseElement*,  
    CMFCRibbonBaseElement*>& arElements);
```  
  
### <a name="parameters"></a>参数  
 `arElements`  
 所有可见元素的数组。  
  
### <a name="remarks"></a>备注  
  
##  <a name="highlightpanel"></a>CMFCRibbonCategory::HighlightPanel  
 突出显示了指定功能区面板。  
  
```  
CMFCRibbonPanel* HighlightPanel(
    CMFCRibbonPanel* pHLPanel,  
    CPoint point);
```  
  
### <a name="parameters"></a>参数  
 [in] `pHLPanel`  
 指针，指向功能区面板，以突出显示。  
  
 [in] `point`  
 X 和 y 坐标相对于窗口的左上角的指针。  
  
### <a name="return-value"></a>返回值  
 指向以前突出显示功能区面板;否则为`NULL`如果没有功能区面板突出显示时，调用此方法。  
  
### <a name="remarks"></a>备注  
 突出显示功能区面板的详细信息，请参阅[CMFCRibbonPanel::Highlight](../../mfc/reference/cmfcribbonpanel-class.md#highlight)。  
  
##  <a name="hittest"></a>CMFCRibbonCategory::HitTest  
 如果指定的点位于，检索指向功能区元素的指针。  
  
```  
CMFCRibbonBaseElement* HitTest(
    CPoint point,  
    BOOL bCheckPanelCaption = FALSE) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `point`  
 将鼠标指针相对于窗口的左上角的 x 和 y 坐标。  
  
 [in] `bCheckPanelCaption`  
 `TRUE`若要测试功能区面板标题;`FALSE`要排除的功能区面板标题。  
  
### <a name="return-value"></a>返回值  
 如果此方法已成功，则为功能区元素的指针否则为`NULL`。  
  
### <a name="remarks"></a>备注  
 仅在功能区类别中包含的功能区元素进行测试。  
  
##  <a name="hittestex"></a>CMFCRibbonCategory::HitTestEx  
 如果指定的点位于它，检索的功能区元素的从零开始索引。  
  
```  
int HitTestEx(CPoint point) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `point`  
 将鼠标指针相对于窗口的左上角的 x 和 y 坐标。  
  
### <a name="return-value"></a>返回值  
 如果此方法已成功，则功能区元素的从零开始的索引否则为-1。  
  
### <a name="remarks"></a>备注  
 仅在功能区类别中包含的功能区元素进行测试。  
  
##  <a name="hittestscrollbuttons"></a>CMFCRibbonCategory::HitTestScrollButtons  
 如果一个点之内一个功能区类别左或向右滚动按钮，返回一个指向该按钮。  
  
```  
CMFCRibbonBaseElement* HitTestScrollButtons(CPoint point) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `point`  
 要测试的点。  
  
### <a name="return-value"></a>返回值  
 如果`point`内左侧的边框或向右滚动按钮的功能区类别，将指针返回到该按钮，或者否则，返回`NULL`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="isactive"></a>CMFCRibbonCategory::IsActive  
 指示是否功能区类别为功能区栏上的活动类别。  
  
```  
BOOL IsActive() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果功能区类别为该活动的类别。否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 活动的功能区类别将显示其功能区面板。  
  
##  <a name="isvisible"></a>CMFCRibbonCategory::IsVisible  
 表示功能区类别是否可见。  
  
```  
BOOL IsVisible() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果功能区类别为可见，则否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 可见的功能区类别显示类别选项卡。  
  
##  <a name="iswindows7look"></a>CMFCRibbonCategory::IsWindows7Look  
 指示父功能区是否有 Windows 7 查找 （矩形的小型应用程序按钮）。  
  
```  
BOOL IsWindows7Look() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果父功能区中有 Windows 7 查找;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="notifycontrolcommand"></a>CMFCRibbonCategory::NotifyControlCommand  
 WM_NOTIFY 命令消息传递到所有`CMFCRibbonPanel`中的元素`CMFCRibbonCategory`直到处理该消息。  
  
```  
virtual BOOL NotifyControlCommand(
    BOOL bAccelerator,  
    int nNotifyCode,  
    WPARAM wParam,  
    LPARAM lParam);
```  
  
### <a name="parameters"></a>参数  
 [in] `bAccelerator`  
 `TRUE`如果此命令源自快捷键，或`FALSE`否则为。  
  
 [in] `nNotifyCode`  
 通知代码中。  
  
 [in] `wParam`  
 消息的 WPARAM 字段。  
  
 [in] `lParam`  
 消息的 LPARAM 字段。  
  
### <a name="return-value"></a>返回值  
 返回`TRUE`如果消息已得到处理，或`FALSE`如果不是。  
  
### <a name="remarks"></a>备注  
  
##  <a name="oncancelmode"></a>CMFCRibbonCategory::OnCancelMode  
 在所有的取消模式时，调用`CMFCRibbonPanel`元素`CMFCRibbonCategory`。  
  
```  
virtual void OnCancelMode();
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="ondraw"></a>CMFCRibbonCategory::OnDraw  
 由框架用于绘制功能区类别调用。  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 功能区类别的设备上下文的指针。  
  
### <a name="remarks"></a>备注  
  
##  <a name="ondrawimage"></a>CMFCRibbonCategory::OnDrawImage  
 由框架在功能区类别上绘制指定的图像调用。  
  
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
 [in] `pDC`  
 图像的设备上下文的指针。  
  
 [in] `rect`  
 显示的图像的矩形。  
  
 [in] `pElement`  
 指向包含所需图像的功能区元素的指针。  
  
 [in] `bIsLargeImage`  
 `TRUE`如果图像大小与大不同。`FALSE`如果图像是小尺寸。  
  
 [in] `nImageIndex`  
 功能区类别中包含的映像数组中的图像的从零开始索引。  
  
 [in] `bCenter`  
 `TRUE`若要居中显示矩形; 中的图像`FALSE`中显示矩形的左上角绘制图像。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果此方法已成功，则否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="ondrawmenuborder"></a>CMFCRibbonCategory::OnDrawMenuBorder  
 由框架来绘制边框的弹出菜单调用。  
  
```  
virtual void OnDrawMenuBorder(
    CDC* pDC,  
    CMFCRibbonPanelMenuBar* pMenuBar);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 未使用此参数。  
  
 [in] `pMenuBar`  
 未使用此参数。  
  
### <a name="remarks"></a>备注  
 默认情况下此方法没有任何效果。 重写此方法以绘制边框的弹出菜单。  
  
##  <a name="onkey"></a>CMFCRibbonCategory::OnKey  
 当用户按下键盘按钮时由框架调用。  
  
```  
virtual BOOL OnKey(UINT nChar);
```  
  
### <a name="parameters"></a>参数  
 `nChar`  
 用户按下的键虚拟键代码。  
  
### <a name="remarks"></a>备注  
  
##  <a name="onlbuttondown"></a>CMFCRibbonCategory::OnLButtonDown  
 由框架来检索下指定的点的功能区元素，当用户按下鼠标左键时调用。  
  
```  
virtual CMFCRibbonBaseElement* OnLButtonDown(CPoint point);
```  
  
### <a name="parameters"></a>参数  
 [in] `point`  
 将鼠标指针相对于窗口的左上角的 x 和 y 坐标。  
  
### <a name="return-value"></a>返回值  
 如果此方法已成功，则为功能区元素的指针否则为`NULL`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="onlbuttonup"></a>CMFCRibbonCategory::OnLButtonUp  
 由框架调用时，同时用户释放鼠标左键和鼠标指针位于功能区类别。  
  
```  
virtual void OnLButtonUp(CPoint point);
```  
  
### <a name="parameters"></a>参数  
 [in] `point`  
 X 和 y 坐标相对于窗口的左上角的指针。  
  
### <a name="remarks"></a>备注  
  
##  <a name="onmousemove"></a>CMFCRibbonCategory::OnMouseMove  
 当指针在功能区栏上移动以便更新功能区类别显示由框架调用。  
  
```  
virtual void OnMouseMove(CPoint point);
```  
  
### <a name="parameters"></a>参数  
 [in] `point`  
 X 和 y 坐标相对于窗口的左上角的指针。  
  
### <a name="remarks"></a>备注  
  
##  <a name="onrtlchanged"></a>CMFCRibbonCategory::OnRTLChanged  
 在布局更改方向时由框架调用。  
  
```  
virtual void OnRTLChanged(BOOL bIsRTL);
```  
  
### <a name="parameters"></a>参数  
 [in] `bIsRTL`  
 `TRUE`如果布局，则从右到左;`FALSE`如果是从左到右的布局。  
  
### <a name="remarks"></a>备注  
 此方法调整所有功能区面板和功能区类别中包含的功能区元素的布局。  
  
##  <a name="onscrollhorz"></a>CMFCRibbonCategory::OnScrollHorz  
 执行滚动操作使得沿水平方向的功能区类别。  
  
```  
virtual BOOL OnScrollHorz(
    BOOL bScrollLeft,  
    int nScrollOffset = 0);
```  
  
### <a name="parameters"></a>参数  
 [in] `bScrollLeft`  
 `TRUE`若要滚动到左侧，`FALSE`要滚动到右侧。  
  
 [in] `nScrollOffset`  
 滚动距离 （像素）。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果在水平方向; 移功能区类别否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="onupdatecmdui"></a>CMFCRibbonCategory::OnUpdateCmdUI  
 调用`OnUpdateCmdUI`中的每个成员函数`CMFCRibbonPanel`元素`CMFCRibbonCategory`启用或禁用它们中的用户界面元素。  
  
```  
virtual void OnUpdateCmdUI(
    CMFCRibbonCmdUI* pCmdUI,  
    CFrameWnd* pTarget,  
    BOOL bDisableIfNoHndler);
```  
  
### <a name="parameters"></a>参数  
 [in] `pCmdUI`  
 指向`CMFCRibbonCmdUI`对象，它指定哪些用户界面元素才可用，以及哪些是被禁用。  
  
 [in] `pTarget`  
 指针，指向窗口中，用于控制启用或禁用的用户界面元素。  
  
 [in] `bDisableIfNoHndler`  
 `TRUE`若要禁用的用户界面项，如果没有处理程序中的消息映射; 定义否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="recalclayout"></a>CMFCRibbonCategory::RecalcLayout  
 调整功能区类别上的所有控件的布局。  
  
```  
virtual void RecalcLayout(CDC* pDC);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 功能区类别的设备上下文的指针。  
  
### <a name="remarks"></a>备注  
  
##  <a name="removepanel"></a>CMFCRibbonCategory::RemovePanel  
 从功能区类别中删除功能区面板。  
  
```cpp  
BOOL RemovePanel(
    int nIndex,  
    BOOL bDelete = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `nIndex`  
 要移除的面板索引号。 通过调用获得[CMFCRibbonCategory::GetPanelIndex](#getpanelindex)方法。  
  
 [in] `bDelete`  
 `TRUE`若要从内存; 中删除面板对象`FALSE`移除面板对象而不删除它。  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 `TRUE`；否则为 `FALSE`。  
  
##  <a name="repospanels"></a>CMFCRibbonCategory::ReposPanels  
 调整功能区类别中包含的功能区面板上的所有控件的布局。  
  
```  
virtual void ReposPanels(CDC* pDC);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 功能区类别中包含的功能区面板的设备上下文的指针。  
  
### <a name="remarks"></a>备注  
  
##  <a name="setcollapseorder"></a>CMFCRibbonCategory::SetCollapseOrder  
 定义折叠的功能区类别功能区面板的顺序。  
  
```  
void SetCollapseOrder(const CArray<int,int>& arCollapseOrder);
```  
  
### <a name="parameters"></a>参数  
 [in] `arCollapseOrder`  
 指定的折叠顺序。 该数组包含功能区面板的从零开始的索引。  
  
### <a name="remarks"></a>备注  
 库定义了折叠顺序。 但是，您可以通过提供与指定的折叠顺序的索引列表类别自定义此行为。  
  
 当该类别检测到它已可折叠功能区面板时，它会查找指定的列表中的下一个元素。 如果列表为空，或者您没有指定足够的元素，该类别使用内部算法。  
  
 例如，类别有三个功能区面板，并且可以折叠几次直到所有面板都处于完全折叠状态。 您可以设置以下折叠顺序︰ 0、 0、 2、 2。 在这种情况下，类别将折叠面板 0 两次，面板 2 的两倍。 具有索引为 1 的面板将保持未折叠。  
  
### <a name="example"></a>示例  
 下面的示例演示如何使用`SetCollapseOrder`中的方法`CMFCRibbonCategory`类。 该示例演示如何构造数组，以便折叠顺序，以及如何折叠顺序设置为功能区类别。  
  
 [!code-cpp[NVC_MFC_RibbonApp #&13;](../../mfc/reference/codesnippet/cpp/cmfcribboncategory-class_2.cpp)]  
  
##  <a name="setdata"></a>CMFCRibbonCategory::SetData  
 设置要与功能区类别相关联的用户定义数据。  
  
```  
void SetData(DWORD_PTR dwData);
```  
  
### <a name="parameters"></a>参数  
 [in] `dwData`  
 用户定义的数据。  
  
##  <a name="setkeys"></a>CMFCRibbonCategory::SetKeys  
 将快捷键提示分配给功能区类别。  
  
```  
void SetKeys(LPCTSTR lpszKeys);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszKeys`  
 快捷键提示文本。  
  
### <a name="remarks"></a>备注  
 当用户按下 alt 或 F10 键，将显示键提示。  
  
##  <a name="setname"></a>CMFCRibbonCategory::SetName  
 将名称和快捷键提示分配给功能区类别。  
  
```  
void SetName(LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszName`  
 名称和快捷键的功能区类别的提示。  
  
### <a name="remarks"></a>备注  
 若要设置为功能区类别快捷键提示，请追加跟快捷键提示字符换行转义序列`lpszName`。  
  
##  <a name="settabcolor"></a>CMFCRibbonCategory::SetTabColor  
 设置功能区类别的颜色。  
  
```  
void SetTabColor(AFX_RibbonCategoryColor color);
```  
  
### <a name="parameters"></a>参数  
 [in] `color`  
 指定功能区类别的新颜色。  
  
### <a name="remarks"></a>备注  
 颜色可以是下列值之一︰  
  
-   AFX_CategoryColor_None  
  
-   AFX_CategoryColor_Red  
  
-   AFX_CategoryColor_Orange  
  
-   AFX_CategoryColor_Yellow  
  
-   AFX_CategoryColor_Green  
  
-   AFX_CategoryColor_Blue  
  
-   AFX_CategoryColor_Indigo  
  
-   AFX_CategoryColor_Violet  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CObject 类](../../mfc/reference/cobject-class.md)

