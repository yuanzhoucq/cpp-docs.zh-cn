---
title: "CMFCToolBarComboBoxButton 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCToolBarComboBoxButton
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::CMFCToolBarComboBoxButton
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::AddItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::AddSortedItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::Compare
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::CreateEdit
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::DeleteItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::FindItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetByCmd
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetComboBox
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetCount
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetCountAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetCurSel
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetCurSelAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetEditCtrl
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetItemAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetItemData
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetItemDataAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetItemDataPtrAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetText
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetTextAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::IsCenterVert
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::IsFlatMode
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::RemoveAllItems
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::SelectItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::SelectItemAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::SetCenterVert
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::SetDropDownHeight
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::SetFlatMode
dev_langs:
- C++
helpviewer_keywords:
- CMFCToolBarComboBoxButton class
ms.assetid: 32fa39f7-8e4e-4f0a-a31d-7b540d969a6c
caps.latest.revision: 30
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 43369e8869f9dd58543016bd74547b24fbe183a5
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="cmfctoolbarcomboboxbutton-class"></a>CMFCToolBarComboBoxButton 类
包含一个组合框控件的工具栏按钮 ( [CComboBox 类](../../mfc/reference/ccombobox-class.md))。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCToolBarComboBoxButton : public CMFCToolBarButton  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCToolBarComboBoxButton::CMFCToolBarComboBoxButton](#cmfctoolbarcomboboxbutton)|构造一个 `CMFCToolBarComboBoxButton`。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCToolBarComboBoxButton::AddItem](#additem)|将项添加到组合框列表的末尾。|  
|[CMFCToolBarComboBoxButton::AddSortedItem](#addsorteditem)|将项添加到组合框列表。 通过指定列表中项的顺序`Compare`。|  
|[CMFCToolBarComboBoxButton::Compare](#compare)|比较两个项。 调用排序项`AddSortedItems`将添加到组合框列表。|  
|[CMFCToolBarComboBoxButton::CreateEdit](#createedit)|创建新的编辑控件的组合框按钮。|  
|[CMFCToolBarComboBoxButton::DeleteItem](#deleteitem)|从组合框列表中删除项。|  
|[CMFCToolBarComboBoxButton::FindItem](#finditem)|返回包含指定的字符串的项的索引。|  
|[CMFCToolBarComboBoxButton::GetByCmd](#getbycmd)|将指针返回到组合框按钮替换为指定的命令 id。|  
|[CMFCToolBarComboBoxButton::GetComboBox](#getcombobox)|返回一个指向该组合框控件嵌入到组合框按钮。|  
|[CMFCToolBarComboBoxButton::GetCount](#getcount)|在组合框列表返回的项数。|  
|[CMFCToolBarComboBoxButton::GetCountAll](#getcountall)|查找组合框按钮具有指定的命令 id。 在组合框列表，该按钮的返回项的数目。|  
|[CMFCToolBarComboBoxButton::GetCurSel](#getcursel)|返回所选的项的索引中组合框列表。|  
|[CMFCToolBarComboBoxButton::GetCurSelAll](#getcurselall)|查找组合框按钮都有指定的命令 ID，并返回组合框列表，该按钮的选定项的索引。|  
|[CMFCToolBarComboBoxButton::GetEditCtrl](#geteditctrl)|返回的指针嵌入在组合框按钮的编辑控件。|  
|[CMFCToolBarComboBoxButton::GetItem](#getitem)|返回与组合框中指定索引相关联的字符串框列表。|  
|[CMFCToolBarComboBoxButton::GetItemAll](#getitemall)|查找组合框按钮都有指定的命令 ID，并返回与该按钮使组合框列表中的索引相关联的字符串。|  
|[CMFCToolBarComboBoxButton::GetItemData](#getitemdata)|返回与组合框中指定索引相关联的 32 位值框列表。|  
|[CMFCToolBarComboBoxButton::GetItemDataAll](#getitemdataall)|查找组合框按钮都有指定的命令 ID，并返回与该按钮使组合框列表中的索引相关联的 32 位值。|  
|[CMFCToolBarComboBoxButton::GetItemDataPtrAll](#getitemdataptrall)|查找组合框按钮具有指定的命令 id。 检索的 32 位值关联的该按钮，然后将返回 32 位值作为指针使组合框列表中的索引。|  
|[CMFCToolBarComboBoxButton::GetText](#gettext)|返回从组合框的编辑控件的文本。|  
|[CMFCToolBarComboBoxButton::GetTextAll](#gettextall)|查找组合框按钮都有指定的命令 ID，并从该按钮的编辑控件中返回的文本。|  
|[CMFCToolBarComboBoxButton::IsCenterVert](#iscentervert)|确定应用程序中的组合框按钮是居中还是与工具栏的顶部对齐。|  
|[CMFCToolBarComboBoxButton::IsFlatMode](#isflatmode)|确定应用程序中的组合框按钮是否具有平面外观。|  
|[CMFCToolBarComboBoxButton::RemoveAllItems](#removeallitems)|删除所有项从列表框中，并编辑组合框控件。|  
|[CMFCToolBarComboBoxButton::SelectItem](#selectitem)|按照其索引、 32 位值或字符串，组合框中选择一项，并通知有关所选的组合框控件。|  
|[CMFCToolBarComboBoxButton::SelectItemAll](#selectitemall)|查找组合框按钮具有指定的命令 id。 调用`SelectItem`可以根据其字符串、 索引或 32 位值该按钮的组合框中选择的项。|  
|[CMFCToolBarComboBoxButton::SetCenterVert](#setcentervert)|指定是否在应用程序的组合框按钮的垂直居中位置或与工具栏的顶部对齐。|  
|[CMFCToolBarComboBoxButton::SetDropDownHeight](#setdropdownheight)|设置下拉列表框的高度。|  
|[CMFCToolBarComboBoxButton::SetFlatMode](#setflatmode)|指定应用程序中的组合框按钮是否具有平面外观。|  
  
## <a name="remarks"></a>备注  
 若要将组合框按钮添加到工具栏，请按照下列步骤︰  
  
 1. 在父级工具栏资源中保留该按钮的虚拟资源 ID。  
  
 2. 构造`CMFCToolBarComboBoxButton`对象。  
  
 3. 在处理该消息处理程序`AFX_WM_RESETTOOLBAR`消息，请将虚拟按钮替换为新的组合框按钮通过使用[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)。  
  
 有关详细信息，请参阅[演练︰ 将控件在工具栏上](../../mfc/walkthrough-putting-controls-on-toolbars.md)。 组合框工具栏按钮的示例，请参阅示例项目 VisualStudioDemo。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用各种方法`CMFCToolBarComboBoxButton`类。 该示例演示如何启用编辑和组合框、 在应用程序中设置的垂直位置的组合框按钮、 列表框的高度时设置下，删除在该应用程序中设置组合框按钮的平面样式外观和设置组合框按钮的编辑框中的文本。 此代码段属于[Visual Studio 演示示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo #&36;](../../mfc/codesnippet/cpp/cmfctoolbarcomboboxbutton-class_1.cpp)]  
[!code-cpp[NVC_MFC_VisualStudioDemo #&37;](../../mfc/codesnippet/cpp/cmfctoolbarcomboboxbutton-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)  
  
## <a name="requirements"></a>要求  
 **标头︰** afxtoolbarcomboboxbutton.h  
  
##  <a name="additem"></a>CMFCToolBarComboBoxButton::AddItem  
 将唯一项追加到列表框中。  
  
```  
virtual INT_PTR AddItem(
    LPCTSTR lpszItem,  
    DWORD_PTR dwData=0);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszItem`  
 要添加到列表框中的项的文本。  
  
 [in] `dwData`  
 与要添加到列表框中的项关联的数据。  
  
### <a name="return-value"></a>返回值  
 在列表框中的最后一项的索引。  
  
### <a name="remarks"></a>备注  
 列表框样式进行排序时，不要使用此方法。  
  
 如果项文本已在列表框中，新的数据存储与现有项。 项搜索不区分大小写。  
  
##  <a name="addsorteditem"></a>CMFCToolBarComboBoxButton::AddSortedItem  
 将某项添加到列表框中，以便由定义[比较](#compare)方法。  
  
```  
virtual INT_PTR AddSortedItem(
    LPCTSTR lpszItem,  
    DWORD_PTR dwData=0);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszItem`  
 要添加到列表框中的项的文本。  
  
 [in] `dwData`  
 与要添加到列表框中的项关联的数据。  
  
### <a name="return-value"></a>返回值  
 已添加到列表框中项的索引。  
  
### <a name="remarks"></a>备注  
 使用此函数将项添加到的列表框中以特定的顺序。  
  
##  <a name="canbestretched"></a>CMFCToolBarComboBoxButton::CanBeStretched  
 指示是否可以更改该组合框按钮的大小。  
  
```  
virtual BOOL CanBeStretched() const;  
```  
  
### <a name="return-value"></a>返回值  
 返回 `TRUE`。  
  
##  <a name="cmfctoolbarcomboboxbutton"></a>CMFCToolBarComboBoxButton::CMFCToolBarComboBoxButton  
 构造[CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)对象。  
  
```  
CMFCToolBarComboBoxButton(
    UINT uiID,  
    int iImage,  
    DWORD dwStyle=CBS_DROPDOWNLIST,  
    int iWidth=0);
```  
  
### <a name="parameters"></a>参数  
 [in] `uiID`  
 新建按钮的命令 ID。  
  
 [in] `iImage`  
 与新建按钮关联的图像的图像索引。  
  
 [in] `dwStyle`  
 新建按钮的样式。  
  
 [in] `iWidth`  
 以像素为单位的新建按钮的宽度。  
  
### <a name="remarks"></a>备注  
 默认宽度为 150 个像素。  
  
 工具栏按钮样式的列表，请参阅[工具栏控件样式](../../mfc/reference/toolbar-control-styles.md)  
  
##  <a name="cleardata"></a>CMFCToolBarComboBoxButton::ClearData  
 删除用户定义的数据。  
  
```  
virtual void ClearData();
```  
  
### <a name="remarks"></a>备注  
 默认情况下此方法没有任何效果。 如果你想要删除用户定义的任何数据，重写此方法在派生类中。  
  
##  <a name="compare"></a>CMFCToolBarComboBoxButton::Compare  
 比较两个字符串。  
  
```  
virtual int Compare(
    LPCTSTR lpszItem1,  
    LPCTSTR lpszItem2);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszItem1`  
 要比较的第一个字符串。  
  
 [in] `lpszItem2`  
 要比较的第二个字符串。  
  
### <a name="return-value"></a>返回值  
 一个值，指示区分大小写的字符串之间按字典顺序关系。 下表列出了可能的值︰  
  
|值|说明|  
|-----------|-----------------|  
|\<0|第一个字符串是否小于第二个。|  
|0|第一个字符串等于第二个。|  
|>0|第一个字符串大于第二个。|  
  
### <a name="remarks"></a>备注  
 重写此方法可以更改项的列表框中的排序方式。  
  
 比较是区分大小写。  
  
 这种方法称为只能从[AddSortedItem](#addsorteditem)方法。  
  
##  <a name="copyfrom"></a>CMFCToolBarComboBoxButton::CopyFrom  
 将指定的状态复制`CMFCToolBarComboBoxButton`与当前对象。  
  
```  
virtual void CopyFrom(const CMFCToolBarButton& src);
```  
  
### <a name="parameters"></a>参数  
 [in] `src`  
 源 `CMFCToolBarComboBoxButton` 对象。  
  
##  <a name="createcombo"></a>CMFCToolBarComboBoxButton::CreateCombo  
 创建用于组合框按钮的新组合框。  
  
```  
virtual CComboBox* CreateCombo(
    CWnd* pWndParent,  
    const CRect& rect);
```  
  
### <a name="parameters"></a>参数  
 [in] `pWndParent`  
 指向按钮的父窗口的指针。  
  
 [in] `rect`  
 组合框的边框。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，则新的组合框指向的指针否则为`NULL`。  
  
##  <a name="createedit"></a>CMFCToolBarComboBoxButton::CreateEdit  
 创建一个新的编辑框的组合框按钮。  
  
```  
virtual CMFCToolBarComboBoxEdit* CreateEdit(
    CWnd* pWndParent,  
    const CRect& rect,  
    DWORD dwEditStyle);
```  
  
### <a name="parameters"></a>参数  
 [in] `pWndParent`  
 指向按钮的父窗口的指针。  
  
 [in] `rect`  
 新的编辑框的绑定矩形。  
  
 [in] `dwEditStyle`  
 控制新的编辑框的样式。  
  
### <a name="return-value"></a>返回值  
 如果此方法已成功，则指向新的指针的编辑框否则为`NULL`。  
  
### <a name="remarks"></a>备注  
 创建一个新的编辑框的组合框按钮时，框架将调用此方法。 重写此方法可以更改如何[CMFCToolBarComboBoxEdit](../../mfc/reference/cmfctoolbarcomboboxedit-class.md)创建。  
  
##  <a name="deleteitem"></a>CMFCToolBarComboBoxButton::DeleteItem  
 从列表框中删除指定的项。  
  
```  
BOOL DeleteItem(int iIndex);  
BOOL DeleteItem(DWORD_PTR dwData);  
  BOOL DeleteItem(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>参数  
 [in] `iIndex`  
 要删除的项的从零开始的索引。  
  
 [in] `dwData`  
 与要删除的项关联的数据。  
  
 [in] `lpszText`  
 要删除的项的文本。 如果有多个具有相同的文本项，将删除的第一项。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果该项已位于并已成功删除;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="duplicatedata"></a>CMFCToolBarComboBoxButton::DuplicateData  
 用户定义的数据相同。  
  
```  
virtual void DuplicateData();
```  
  
### <a name="remarks"></a>备注  
 默认情况下此方法没有任何效果。 如果您想要复制任何用户定义数据，重写此方法在派生类中。  
  
##  <a name="enablewindow"></a>CMFCToolBarComboBoxButton::EnableWindow  
 启用或禁用编辑和组合框。  
  
```  
virtual void EnableWindow(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bEnable`  
 `TRUE`若要启用编辑和组合框中;`FALSE`若要禁用编辑和组合框。  
  
### <a name="remarks"></a>备注  
 禁用时，这些控件不能处于活动状态，并且不能接受用户输入。  
  
##  <a name="exporttomenubutton"></a>CMFCToolBarComboBoxButton::ExportToMenuButton  
 副本指定使用组合框按钮命令的菜单应用程序字符串表中的字符串 id。  
  
```  
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;  
```  
  
### <a name="parameters"></a>参数  
 [out] `menuButton`  
 对菜单按钮的引用。  
  
### <a name="return-value"></a>返回值  
 总是为 `TRUE`。  
  
##  <a name="finditem"></a>CMFCToolBarComboBoxButton::FindItem  
 返回包含指定的字符串的列表框中的第一项的索引。  
  
```  
int FindItem(LPCTSTR lpszText) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszText`  
 要在列表框中搜索文本。  
  
### <a name="return-value"></a>返回值  
 项的索引;或`CB_ERR`如果找不到该项目。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getbycmd"></a>CMFCToolBarComboBoxButton::GetByCmd  
 获取一个指针指向组合框按钮具有指定的命令 id。  
  
```  
static CMFCToolBarComboBoxButton* GetByCmd(
    UINT uiCmd,  
    BOOL bIsFocus=FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `uiCmd`  
 组合框按钮的命令 ID。  
  
 [in] `bIsFocus`  
 `TRUE`只搜索已设定焦点按钮;`FALSE`要搜索的所有按钮。  
  
### <a name="return-value"></a>返回值  
 指向一个组合框按钮;或`NULL`如果找不到按钮。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getcombobox"></a>CMFCToolBarComboBoxButton::GetComboBox  
 返回一个指针，到组合框中组合框按钮。  
  
```  
CComboBox* GetComboBox() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个指向[CComboBox 类](../../mfc/reference/ccombobox-class.md)对象的方法是成功，否则为`NULL`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getcontextmenuid"></a>CMFCToolBarComboBoxButton::GetContextMenuID  
 获取组合框按钮的快捷菜单资源 ID。  
  
```  
UINT GetContextMenuID();
```  
  
### <a name="return-value"></a>返回值  
 快捷菜单上的资源 id。  
  
##  <a name="getcount"></a>CMFCToolBarComboBoxButton::GetCount  
 在列表框中返回的项数。  
  
```  
INT_PTR GetCount() const;  
```  
  
### <a name="return-value"></a>返回值  
 在列表框中的项的数目。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getcountall"></a>CMFCToolBarComboBoxButton::GetCountAll  
 获取具有指定的命令 ID 的组合框按钮的列表框中的项的数目  
  
```  
static int GetCountAll(UINT uiCmd);
```  
  
### <a name="parameters"></a>参数  
 [in] `uiCmd`  
 组合框按钮的命令 ID。  
  
### <a name="return-value"></a>返回值  
 列表框中; 中的项的数目否则为`CB_ERR`如果找不到组合框按钮。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getcursel"></a>CMFCToolBarComboBoxButton::GetCurSel  
 获取列表框中当前选定项的索引。  
  
```  
int GetCurSel() const;  
```  
  
### <a name="return-value"></a>返回值  
 在列表框中; 当前所选的项的索引或`CB_ERR`如果未不选定任何项。  
  
### <a name="remarks"></a>备注  
 列表框索引是从零开始。  
  
##  <a name="getcurselall"></a>CMFCToolBarComboBoxButton::GetCurSelAll  
 返回组合的列表框中当前选定项的索引框按钮具有指定的命令 id。  
  
```  
static int GetCurSelAll(UINT uiCmd);
```  
  
### <a name="parameters"></a>参数  
 [in] `uiCmd`  
 组合框按钮的命令 ID。  
  
### <a name="return-value"></a>返回值  
 在列表框中; 当前所选的项的索引否则为`CB_ERR`如果未选定任何项，或者找不到组合框按钮。  
  
### <a name="remarks"></a>备注  
 列表框索引是从零开始。  
  
##  <a name="geteditctrl"></a>CMFCToolBarComboBoxButton::GetEditCtrl  
 返回一个指针，到编辑框中组合框按钮。  
  
```  
virtual CEdit* GetEditCtrl();
```  
  
### <a name="return-value"></a>返回值  
 在编辑框中，如果此方法已成功，则指向的指针否则为`NULL`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="gethwnd"></a>CMFCToolBarComboBoxButton::GetHwnd  
 返回为组合框的窗口句柄。  
  
```  
virtual HWND GetHwnd();
```  
  
### <a name="return-value"></a>返回值  
 窗口句柄，或`NULL`组合框是否不与 window 对象相关联。  
  
##  <a name="getitem"></a>CMFCToolBarComboBoxButton::GetItem  
 返回与列表框中指定索引处的项关联的字符串。  
  
```  
LPCTSTR GetItem(int iIndex=-1) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `iIndex`  
 列表框中某项的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 指向与项; 关联的字符串的指针否则为`NULL`如果索引参数无效，或者如果索引参数为-1，并且在组合框中不存在所选的项。  
  
### <a name="remarks"></a>备注  
 为-1 索引参数返回当前选定的项的字符串。  
  
##  <a name="getitemall"></a>CMFCToolBarComboBoxButton::GetItemAll  
 返回与具有指定的命令 ID 的组合框按钮的列表框中指定索引处的项关联的字符串  
  
```  
static LPCTSTR GetItemAll(
    UINT uiCmd,  
    int iIndex=-1);
```  
  
### <a name="parameters"></a>参数  
 [in] `uiCmd`  
 组合框按钮的命令 ID。  
  
 [in] `iIndex`  
 在列表框中项的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 如果此方法已成功，则项的字符串指向的指针否则为`NULL`如果索引无效，不是组合框按钮找到，或者如果索引是-1，且在组合框中不存在所选的项。  
  
### <a name="remarks"></a>备注  
 为-1 的索引值返回当前选定的项的字符串。  
  
##  <a name="getitemdata"></a>CMFCToolBarComboBoxButton::GetItemData  
 返回与列表框中的特定索引处的项关联的数据。  
  
```  
DWORD_PTR GetItemData(int iIndex=-1) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `iIndex`  
 在列表框中项的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 与项; 关联的数据或者，如果 0 项不存在。  
  
### <a name="remarks"></a>备注  
 索引参数为-1 返回与当前所选的项相关联的数据。  
  
##  <a name="getitemdataall"></a>CMFCToolBarComboBoxButton::GetItemDataAll  
 返回与具有特定的命令 ID 的组合框按钮的列表框中的特定索引处的项关联的数据  
  
```  
static DWORD_PTR GetItemDataAll(
    UINT uiCmd,  
    int iIndex=-1);
```  
  
### <a name="parameters"></a>参数  
 [in] `uiCmd`  
 组合框按钮的命令 ID。  
  
 [in] `iIndex`  
 在列表框中项的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 如果此方法已成功，则与项相关联的数据否则，如果指定的索引不是有效的则为 0 或 CB_ERR 如果组合框按钮中找不到。  
  
### <a name="remarks"></a>备注  
 索引参数为-1 返回与当前所选的项相关联的数据。  
  
##  <a name="getitemdataptrall"></a>CMFCToolBarComboBoxButton::GetItemDataPtrAll  
 返回与具有特定的命令 ID 的组合框按钮的列表框中的特定索引处的项关联的数据 一个指针为返回此数据。  
  
```  
static void* GetItemDataPtrAll(
    UINT uiCmd,  
    int iIndex=-1);
```  
  
### <a name="parameters"></a>参数  
 [in] `uiCmd`  
 组合框按钮的命令 ID。  
  
 [in] `iIndex`  
 在列表框中项的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 一个指针，如果此方法已成功，则与项目关联如果发生错误，否则为-1 或`NULL`如果找不到组合框按钮。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getprompt"></a>CMFCToolBarComboBoxButton::GetPrompt  
 返回组合框按钮的提示字符串。  
  
```  
virtual CString GetPrompt() const;  
```  
  
### <a name="return-value"></a>返回值  
 中的提示字符串。  
  
### <a name="remarks"></a>备注  
 当前未实现此方法。  
  
##  <a name="gettext"></a>CMFCToolBarComboBoxButton::GetText  
 在编辑框中获取的文本。  
  
```  
LPCTSTR GetText() const;  
```  
  
### <a name="return-value"></a>返回值  
 编辑框中的文本。  
  
### <a name="remarks"></a>备注  
  
##  <a name="gettextall"></a>CMFCToolBarComboBoxButton::GetTextAll  
 获取具有指定的命令 ID 的组合框按钮的编辑框中的文本  
  
```  
static LPCTSTR GetTextAll(UINT uiCmd);
```  
  
### <a name="parameters"></a>参数  
 [in] `uiCmd`  
 特定的组合框按钮的命令 ID。  
  
### <a name="return-value"></a>返回值  
 如果此方法已成功，则编辑框中的文本否则为`NULL`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="hasfocus"></a>CMFCToolBarComboBoxButton::HasFocus  
 指示是否对组合框当前具有焦点。  
  
```  
virtual BOOL HasFocus() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果组合框中当前具有焦点，则否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 此方法也返回`TRUE`如果组合框中的任何子窗口当前具有焦点。  
  
##  <a name="iscentervert"></a>CMFCToolBarComboBoxButton::IsCenterVert  
 返回在应用程序中组合框按钮的垂直位置。  
  
```  
static BOOL IsCenterVert();
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果按钮居中位置;，`FALSE`如果按钮的顶部对齐。  
  
### <a name="remarks"></a>备注  
  
##  <a name="isflatmode"></a>CMFCToolBarComboBoxButton::IsFlatMode  
 返回在应用程序中组合框按钮的平面样式外观。  
  
```  
static BOOL IsFlatMode();
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果按钮具有平面的样式;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 组合框按钮的默认平面样式是`FALSE.`  
  
##  <a name="isownerof"></a>CMFCToolBarComboBoxButton::IsOwnerOf  
 指示指定的句柄是否与组合框按钮，或其子级之一相关联。  
  
```  
virtual BOOL IsOwnerOf(HWND hwnd);
```  
  
### <a name="parameters"></a>参数  
 [in] `hwnd`  
 窗口句柄。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果句柄供电组合框按钮，或从一台其子;否则为`FALSE`。  
  
##  <a name="isribbonbutton"></a>CMFCToolBarComboBoxButton::IsRibbonButton  
 该值指示组合框按钮是否位于功能区面板。  
  
```  
BOOL IsRibbonButton() const;  
```  
  
### <a name="return-value"></a>返回值  
 总是为 `FALSE`。  
  
### <a name="remarks"></a>备注  
 默认情况下，此方法始终返回`FALSE`，这意味着组合框按钮永远不会显示在功能区面板上。  
  
##  <a name="iswindowvisible"></a>CMFCToolBarComboBoxButton::IsWindowVisible  
 返回的可见性状态的组合框按钮。  
  
```  
virtual BOOL IsWindowVisible();
```  
  
### <a name="return-value"></a>返回值  
 组合框按钮的可见性状态。  
  
##  <a name="notifycommand"></a>CMFCToolBarComboBoxButton::NotifyCommand  
 该值指示组合框按钮是否处理消息。  
  
```  
virtual BOOL NotifyCommand(int iNotifyCode);
```  
  
### <a name="parameters"></a>参数  
 [in] `iNotifyCode`  
 与命令关联通知消息。  
  
### <a name="return-value"></a>返回值  
 是否组合框按钮处理的消息。  
  
##  <a name="onaddtocustomizepage"></a>CMFCToolBarComboBoxButton::OnAddToCustomizePage  
 当该按钮添加到由框架调用**自定义**对话框。  
  
```  
virtual void OnAddToCustomizePage();
```  
  
##  <a name="oncalculatesize"></a>CMFCToolBarComboBoxButton::OnCalculateSize  
 调用由框架来计算按钮的大小。  
  
```  
virtual SIZE OnCalculateSize(
    CDC* pDC,  
    const CSize& sizeDefault,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 显示组合框按钮设备上下文。  
  
 [in] `sizeDefault`  
 组合框按钮的默认大小。  
  
 [in] `bHorz`  
 在父级工具栏停靠状态。 `TRUE`当水平停靠工具栏和`FALSE`当垂直停靠工具栏。  
  
### <a name="return-value"></a>返回值  
 一个`SIZE`包含组合框按钮，以像素为单位的维度的结构。  
  
##  <a name="onchangeparentwnd"></a>CMFCToolBarComboBoxButton::OnChangeParentWnd  
 组合框按钮插入到一个新的工具栏中时由框架调用。  
  
```  
virtual void OnChangeParentWnd(CWnd* pWndParent);
```  
  
### <a name="parameters"></a>参数  
 [in] `pWndParent`  
 指向新的父级工具栏的指针。  
  
##  <a name="onclick"></a>CMFCToolBarComboBoxButton::OnClick  
 由框架调用，当用户单击组合框按钮。  
  
```  
virtual BOOL OnClick(
    CWnd* pWnd,  
    BOOL bDelay = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `pWnd`  
 组合框按钮的父窗口的指针。  
  
 [in] `bDelay`  
 保留供派生类中使用。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果该方法处理路由事件。，否则为`FALSE`。  
  
##  <a name="onctlcolor"></a>CMFCToolBarComboBoxButton::OnCtlColor  
 当用户更改父工具栏颜色设置组合框按钮的颜色由框架调用。  
  
```  
virtual HBRUSH OnCtlColor(
    CDC* pDC,  
    UINT nCtlColor);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 显示组合框按钮设备上下文。  
  
 [in] `nCtlColor`  
 未使用。  
  
### <a name="return-value"></a>返回值  
 框架将使用绘制背景的组合框按钮的画笔的句柄。  
  
### <a name="remarks"></a>备注  
 此方法还设置组合框按钮的文本颜色。  
  
##  <a name="ondraw"></a>CMFCToolBarComboBoxButton::OnDraw  
 由框架用于绘制通过使用指定的样式和选项的组合框按钮调用。  
  
```  
virtual void OnDraw(
    CDC* pDC,  
    const CRect& rect,  
    CMFCToolBarImages* pImages,  
    BOOL bHorz = TRUE,  
    BOOL bCustomizeMode = FALSE,  
    BOOL bHighlight = FALSE,  
    BOOL bDrawBorder = TRUE,  
    BOOL bGrayDisabledButtons = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `Pdc`  
 所显示的按钮的设备上下文。  
  
 [in] `rect`  
 该按钮的边框。  
  
 [in] `pImages`  
 与按钮关联的图像集合。  
  
 [in] `bHorz`  
 在父级工具栏停靠状态。 `TRUE`当水平停靠工具栏和`FALSE`当垂直停靠工具栏。  
  
 [in] `bCustomizeMode`  
 应用程序是否在自定义模式。  
  
 [in] `bHighlight`  
 是否要绘制突出显示组合框按钮。  
  
 [in] `bDrawBorder`  
 是否要绘制带有边框组合框按钮。  
  
 [in] `bGrayDisabledButtons`  
 `TRUE`若要绘制阴影禁用的按钮;`FALSE`若要使用已禁用图像集合。  
  
##  <a name="ondrawoncustomizelist"></a>CMFCToolBarComboBoxButton::OnDrawOnCustomizeList  
 由框架调用以在中绘制组合框按钮**命令**窗格**自定义**对话框。  
  
```  
virtual int OnDrawOnCustomizeList(
    CDC* pDC,  
    const CRect& rect,  
    BOOL bSelected);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 显示组合框按钮设备上下文。  
  
 [in] `rect`  
 组合框按钮的边框。  
  
 [in] `bSelected`  
 `TRUE`如果组合框按钮处于选中状态，否则为`FALSE`。  
  
### <a name="return-value"></a>返回值  
 以像素为单位的组合框按钮的宽度。  
  
##  <a name="onglobalfontschanged"></a>CMFCToolBarComboBoxButton::OnGlobalFontsChanged  
 由框架设置组合框按钮字体，应用程序字体更改时调用。  
  
```  
virtual void OnGlobalFontsChanged();
```  
  
##  <a name="onmove"></a>CMFCToolBarComboBoxButton::OnMove  
 由框架在父级工具栏移时改变组合框按钮的位置调用。  
  
```  
virtual void OnMove();
```  
  
##  <a name="onshow"></a>CMFCToolBarComboBoxButton::OnShow  
 隐藏或显示组合框按钮时由框架调用。  
  
```  
virtual void OnShow(BOOL bShow);
```  
  
### <a name="parameters"></a>参数  
 [in] `bShow`  
 是否要隐藏或显示组合框按钮。  
  
##  <a name="onsize"></a>CMFCToolBarComboBoxButton::OnSize  
 由框架后，若要更改组合框按钮的大小，在父级工具栏大小更改时调用。  
  
```  
virtual void OnSize(int iSize);
```  
  
### <a name="parameters"></a>参数  
 [in] `iSize`  
 组合框按钮新宽度。  
  
##  <a name="onupdatetooltip"></a>CMFCToolBarComboBoxButton::OnUpdateToolTip  
 当用户更改组合框按钮的工具提示，由框架调用。  
  
```  
virtual BOOL OnUpdateToolTip(
    CWnd* pWndParent,  
    int iButtonIndex,  
    CToolTipCtrl& wndToolTip,  
    CString& str);
```  
  
### <a name="parameters"></a>参数  
 [in] `pWndParent`  
 组合框按钮的父窗口的指针。  
  
 [in] `iButtonIndex`  
 组合框按钮的 ID。  
  
 [in] `wndToolTip`  
 要将与组合框按钮相关联的工具提示。  
  
 [in] `str`  
 工具提示文本。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果该方法处理路由事件。，否则为`FALSE`。  
  
##  <a name="removeallitems"></a>CMFCToolBarComboBoxButton::RemoveAllItems  
 从列表和编辑框中删除所有项。  
  
```  
void RemoveAllItems();
```  
  
### <a name="remarks"></a>备注  
 删除所有项从列表框中，并编辑一个组合框控件。  
  
##  <a name="selectitem"></a>CMFCToolBarComboBoxButton::SelectItem  
 在列表框中选择一项。  
  
```  
BOOL SelectItem(
    int iIndex,  
    BOOL bNotify=TRUE);  
  
BOOL SelectItem(DWORD_PTR dwData);  
BOOL SelectItem(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>参数  
 [in] `iIndex`  
 在列表框中项的从零开始索引。  
  
 [in] `bNotify`  
 `TRUE`若要通知的组合框按钮的所选内容;否则为`FALSE`。  
  
 [in] `dwData`  
 与列表框中的项关联的数据。  
  
 [in] `lpszText`  
 在列表框中项的文本。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果此方法已成功，则否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="selectitemall"></a>CMFCToolBarComboBoxButton::SelectItemAll  
 具有指定的命令 ID 的组合框按钮的列表框中选择一项  
  
```  
static BOOL SelectItemAll(
    UINT uiCmd,  
    int iIndex);

 
static BOOL SelectItemAll(
    UINT uiCmd,  
    DWORD_PTR dwData);

 
static BOOL SelectItemAll(
    UINT uiCmd,  
    LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>参数  
 [in] `uiCmd`  
 包含列表框中的组合框按钮的命令 ID。  
  
 [in] `iIndex`  
 在列表框中项的从零开始索引。 值为-1 的列表框中删除任何当前所选内容并清除编辑框。  
  
 [in] `dwData`  
 列表框中某项的数据。  
  
 [in] `lpszText`  
 在列表框中项的文本。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果此方法已成功，则否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="serialize"></a>CMFCToolBarComboBoxButton::Serialize  
 从存档读取此对象或将其写入存档。  
  
```  
virtual void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>参数  
 [in, out] `ar`  
 `CArchive`要序列化对象。  
  
### <a name="remarks"></a>备注  
 中的设置`CArchive`对象确定是否此方法读取或写入存档。  
  
##  <a name="setaccdata"></a>CMFCToolBarComboBoxButton::SetACCData  
 填充指定`CAccessibilityData`通过从组合框按钮的可访问性数据的对象。  
  
```  
virtual BOOL SetACCData(
    CWnd* pParent,  
    CAccessibilityData& data);
```  
  
### <a name="parameters"></a>参数  
 [in] `pParent`  
 组合框按钮父窗口。  
  
 [out] `data`  
 一个`CAccessibilityData`接收来自组合框按钮的可访问性数据的对象。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果此方法已成功，则否则为`FALSE`。  
  
##  <a name="setcentervert"></a>CMFCToolBarComboBoxButton::SetCenterVert  
 应用程序中设置组合框按钮的垂直位置。  
  
```  
static void SetCenterVert(BOOL bCenterVert=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bCenterVert`  
 `TRUE`若要居中组合框按钮在工具栏中;`FALSE`对齐到顶部的工具栏组合框按钮。  
  
### <a name="remarks"></a>备注  
 默认情况下，组合框按钮的顶部对齐。  
  
##  <a name="setcontextmenuid"></a>CMFCToolBarComboBoxButton::SetContextMenuID  
 设置组合框按钮的快捷菜单资源 ID。  
  
```  
void SetContextMenuID(UINT uiResID);
```  
  
### <a name="parameters"></a>参数  
 [in] `uiResID`  
 快捷菜单上的资源 id。  
  
##  <a name="setdropdownheight"></a>CMFCToolBarComboBoxButton::SetDropDownHeight  
 向下删除时，请设置列表框的高度。  
  
```  
void SetDropDownHeight(int nHeight);
```  
  
### <a name="parameters"></a>参数  
 [in] `nHeight`  
 以像素为单位的列表框的高度。  
  
### <a name="remarks"></a>备注  
 默认高度为 150 像素。  
  
##  <a name="setflatmode"></a>CMFCToolBarComboBoxButton::SetFlatMode  
 应用程序中设置组合框按钮的平面样式外观。  
  
```  
static void SetFlatMode(BOOL bFlat=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bFlat`  
 `TRUE`用于平面样式外观。否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 组合框按钮的默认平面样式是`FALSE`。  
  
##  <a name="setstyle"></a>CMFCToolBarComboBoxButton::SetStyle  
 设置组合框按钮指定的样式，如果未禁用重绘控件。  
  
```  
virtual void SetStyle(UINT nStyle);
```  
  
### <a name="parameters"></a>参数  
 [in] `nStyle`  
 工具栏样式按位组合 (OR)。  
  
### <a name="remarks"></a>备注  
 工具栏按钮样式的列表，请参阅[工具栏控件样式](../../mfc/reference/toolbar-control-styles.md)  
  
##  <a name="settext"></a>CMFCToolBarComboBoxButton::SetText  
 在编辑框中的组合框按钮设置的文本。  
  
```  
void SetText(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszText`  
 包含用于编辑框的文本的字符串指针。  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBarButton 类](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [CComboBox 类](../../mfc/reference/ccombobox-class.md)   
 [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)   
 [演练︰ 将置于工具栏上的控件](../../mfc/walkthrough-putting-controls-on-toolbars.md)




