---
title: CMFCToolBarComboBoxButton 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
- CMFCToolBarComboBoxButton [MFC], CMFCToolBarComboBoxButton
- CMFCToolBarComboBoxButton [MFC], AddItem
- CMFCToolBarComboBoxButton [MFC], AddSortedItem
- CMFCToolBarComboBoxButton [MFC], Compare
- CMFCToolBarComboBoxButton [MFC], CreateEdit
- CMFCToolBarComboBoxButton [MFC], DeleteItem
- CMFCToolBarComboBoxButton [MFC], FindItem
- CMFCToolBarComboBoxButton [MFC], GetByCmd
- CMFCToolBarComboBoxButton [MFC], GetComboBox
- CMFCToolBarComboBoxButton [MFC], GetCount
- CMFCToolBarComboBoxButton [MFC], GetCountAll
- CMFCToolBarComboBoxButton [MFC], GetCurSel
- CMFCToolBarComboBoxButton [MFC], GetCurSelAll
- CMFCToolBarComboBoxButton [MFC], GetEditCtrl
- CMFCToolBarComboBoxButton [MFC], GetItem
- CMFCToolBarComboBoxButton [MFC], GetItemAll
- CMFCToolBarComboBoxButton [MFC], GetItemData
- CMFCToolBarComboBoxButton [MFC], GetItemDataAll
- CMFCToolBarComboBoxButton [MFC], GetItemDataPtrAll
- CMFCToolBarComboBoxButton [MFC], GetText
- CMFCToolBarComboBoxButton [MFC], GetTextAll
- CMFCToolBarComboBoxButton [MFC], IsCenterVert
- CMFCToolBarComboBoxButton [MFC], IsFlatMode
- CMFCToolBarComboBoxButton [MFC], RemoveAllItems
- CMFCToolBarComboBoxButton [MFC], SelectItem
- CMFCToolBarComboBoxButton [MFC], SelectItemAll
- CMFCToolBarComboBoxButton [MFC], SetCenterVert
- CMFCToolBarComboBoxButton [MFC], SetDropDownHeight
- CMFCToolBarComboBoxButton [MFC], SetFlatMode
ms.assetid: 32fa39f7-8e4e-4f0a-a31d-7b540d969a6c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ddfa4d26ed0a4328714fbd1a921fe7c204ca3752
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33377361"
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
|[CMFCToolBarComboBoxButton::AddSortedItem](#addsorteditem)|向组合框列表中添加一项。 指定列表中项的顺序`Compare`。|  
|[CMFCToolBarComboBoxButton::Compare](#compare)|比较两个项。 调用排序项`AddSortedItems`将添加到组合框列表。|  
|[CMFCToolBarComboBoxButton::CreateEdit](#createedit)|创建新的编辑控件的组合框按钮。|  
|[CMFCToolBarComboBoxButton::DeleteItem](#deleteitem)|从组合框列表中删除的项。|  
|[CMFCToolBarComboBoxButton::FindItem](#finditem)|返回包含指定的字符串的项的索引。|  
|[CMFCToolBarComboBoxButton::GetByCmd](#getbycmd)|将指针返回到组合框按钮替换为指定的命令 id。|  
|[CMFCToolBarComboBoxButton::GetComboBox](#getcombobox)|返回一个指向组合框控件嵌入到组合框按钮。|  
|[CMFCToolBarComboBoxButton::GetCount](#getcount)|在组合框列表返回项的数目。|  
|[CMFCToolBarComboBoxButton::GetCountAll](#getcountall)|查找组合框按钮具有指定的命令 id。 在组合框列表，该按钮的返回项的数目。|  
|[CMFCToolBarComboBoxButton::GetCurSel](#getcursel)|返回所选的项的索引中组合框列表。|  
|[CMFCToolBarComboBoxButton::GetCurSelAll](#getcurselall)|查找组合框按钮都有指定的命令 ID，并返回组合框列表，该按钮的选定项的索引。|  
|[CMFCToolBarComboBoxButton::GetEditCtrl](#geteditctrl)|在组合框按钮中嵌入的编辑控件中返回的指针。|  
|[CMFCToolBarComboBoxButton::GetItem](#getitem)|返回与组合中的指定索引相关联的字符串框列表。|  
|[CMFCToolBarComboBoxButton::GetItemAll](#getitemall)|查找组合框按钮都有指定的命令 ID，并返回与该按钮的组合框列表中索引相关联的字符串。|  
|[CMFCToolBarComboBoxButton::GetItemData](#getitemdata)|返回与组合中的指定索引相关联的 32 位值框列表。|  
|[CMFCToolBarComboBoxButton::GetItemDataAll](#getitemdataall)|查找组合框按钮都有指定的命令 ID，并返回与该按钮的组合框列表中索引相关联的 32 位值。|  
|[CMFCToolBarComboBoxButton::GetItemDataPtrAll](#getitemdataptrall)|查找组合框按钮具有指定的命令 id。 检索的 32 位值关联的该按钮，并返回 32 位值作为指针使组合框列表中的索引。|  
|[CMFCToolBarComboBoxButton::GetText](#gettext)|返回从组合框编辑控件的文本。|  
|[CMFCToolBarComboBoxButton::GetTextAll](#gettextall)|查找组合框按钮都有指定的命令 ID，并从该按钮的编辑控件中返回的文本。|  
|[CMFCToolBarComboBoxButton::IsCenterVert](#iscentervert)|确定是否在应用程序的组合框按钮居中或与工具栏的顶部对齐。|  
|[CMFCToolBarComboBoxButton::IsFlatMode](#isflatmode)|确定应用程序中的组合框按钮是否具有平面的外观。|  
|[CMFCToolBarComboBoxButton::RemoveAllItems](#removeallitems)|中移除所有项从列表框中字符和编辑控件的组合框。|  
|[CMFCToolBarComboBoxButton::SelectItem](#selectitem)|根据其索引、 32 位值或字符串，组合框中选择一项，并通知有关所选内容的组合框控件。|  
|[CMFCToolBarComboBoxButton::SelectItemAll](#selectitemall)|查找组合框按钮具有指定的命令 id。 调用`SelectItem`以该按钮根据其字符串、 索引或 32 位值的组合框中选择项。|  
|[CMFCToolBarComboBoxButton::SetCenterVert](#setcentervert)|指定应用程序中的组合框按钮是垂直居中还是与工具栏的顶部对齐。|  
|[CMFCToolBarComboBoxButton::SetDropDownHeight](#setdropdownheight)|设置下拉列表框的高度。|  
|[CMFCToolBarComboBoxButton::SetFlatMode](#setflatmode)|指定应用程序中的组合框按钮是否具有平面外观。|  
  
## <a name="remarks"></a>备注  
 将组合框按钮添加到工具栏，请执行以下步骤：  
  
 1. 在父级工具栏资源中保留该按钮的虚拟资源 ID。  
  
 2. 构造`CMFCToolBarComboBoxButton`对象。  
  
 3. 在处理消息处理程序`AFX_WM_RESETTOOLBAR`消息，通过使用新的组合框按钮代替 dummy 按钮[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)。  
  
 有关详细信息，请参阅[演练： 将工具栏上的控件](../../mfc/walkthrough-putting-controls-on-toolbars.md)。 组合框工具栏按钮的示例，请参阅示例项目 VisualStudioDemo。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用各种方法`CMFCToolBarComboBoxButton`类。 该示例演示如何启用编辑和组合框、 在应用程序中设置的垂直位置的组合框按钮、 设置列表框的高度，它将被删除、 在应用程序中设置组合框按钮的平面样式外观并设置中编辑框的组合框按钮的文本。 此代码片段属于[Visual Studio 演示示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#36](../../mfc/codesnippet/cpp/cmfctoolbarcomboboxbutton-class_1.cpp)]  
[!code-cpp[NVC_MFC_VisualStudioDemo#37](../../mfc/codesnippet/cpp/cmfctoolbarcomboboxbutton-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)  
  
## <a name="requirements"></a>要求  
 **标头：** afxtoolbarcomboboxbutton.h  
  
##  <a name="additem"></a>  CMFCToolBarComboBoxButton::AddItem  
 将唯一的项追加到列表框中。  
  
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
 列表框中的最后一项的索引。  
  
### <a name="remarks"></a>备注  
 列表框样式进行排序时，不要使用此方法。  
  
 如果将项文本已在列表框中，新的数据存储与现有的项。 项搜索不区分大小写。  
  
##  <a name="addsorteditem"></a>  CMFCToolBarComboBoxButton::AddSortedItem  
 将项添加到的列表框中定义的顺序[比较](#compare)方法。  
  
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
 已添加到列表框中的项的索引。  
  
### <a name="remarks"></a>备注  
 使用此函数将项添加到的列表框中以特定顺序。  
  
##  <a name="canbestretched"></a>  CMFCToolBarComboBoxButton::CanBeStretched  
 指示是否可以更改该组合框按钮的大小。  
  
```  
virtual BOOL CanBeStretched() const;  
```  
  
### <a name="return-value"></a>返回值  
 返回 `TRUE`。  
  
##  <a name="cmfctoolbarcomboboxbutton"></a>  CMFCToolBarComboBoxButton::CMFCToolBarComboBoxButton  
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
 新建按钮与关联的图像映像索引。  
  
 [in] `dwStyle`  
 新建按钮的样式。  
  
 [in] `iWidth`  
 以像素为单位，新建按钮的宽度。  
  
### <a name="remarks"></a>备注  
 默认宽度为 150 像素。  
  
 工具栏按钮样式的列表，请参阅[工具栏控件样式](../../mfc/reference/toolbar-control-styles.md)  
  
##  <a name="cleardata"></a>  CMFCToolBarComboBoxButton::ClearData  
 删除用户定义的数据。  
  
```  
virtual void ClearData();
```  
  
### <a name="remarks"></a>备注  
 默认情况下此方法没有任何影响。 重写此方法在派生类中的，如果你想要删除用户定义的任何数据。  
  
##  <a name="compare"></a>  CMFCToolBarComboBoxButton::Compare  
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
 一个值，指示在字符串之间的区分大小写字典关系。 下表列出可能的值：  
  
|值|描述|  
|-----------|-----------------|  
|\<0|第一个字符串是否小于第二个。|  
|0|第一个字符串等于第二个。|  
|>0|第一个字符串大于第二个。|  
  
### <a name="remarks"></a>备注  
 重写此方法可以更改项的列表框中的排序方式。  
  
 比较是区分大小写。  
  
 此方法调用只能从[AddSortedItem](#addsorteditem)方法。  
  
##  <a name="copyfrom"></a>  CMFCToolBarComboBoxButton::CopyFrom  
 将复制的指定状态`CMFCToolBarComboBoxButton`与当前对象。  
  
```  
virtual void CopyFrom(const CMFCToolBarButton& src);
```  
  
### <a name="parameters"></a>参数  
 [in] `src`  
 源 `CMFCToolBarComboBoxButton` 对象。  
  
##  <a name="createcombo"></a>  CMFCToolBarComboBoxButton::CreateCombo  
 创建新的组合框的组合框按钮。  
  
```  
virtual CComboBox* CreateCombo(
    CWnd* pWndParent,  
    const CRect& rect);
```  
  
### <a name="parameters"></a>参数  
 [in] `pWndParent`  
 指向按钮的父窗口的指针。  
  
 [in] `rect`  
 组合框绑定矩形。  
  
### <a name="return-value"></a>返回值  
 指向新的组合框如果此方法成功，则否则为`NULL`。  
  
##  <a name="createedit"></a>  CMFCToolBarComboBoxButton::CreateEdit  
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
 新的编辑框控件样式。  
  
### <a name="return-value"></a>返回值  
 指向新编辑框中，如果此方法成功，则否则为`NULL`。  
  
### <a name="remarks"></a>备注  
 创建一个新的编辑框的组合框按钮时，框架将调用此方法。 重写此方法可以更改如何[CMFCToolBarComboBoxEdit](../../mfc/reference/cmfctoolbarcomboboxedit-class.md)创建。  
  
##  <a name="deleteitem"></a>  CMFCToolBarComboBoxButton::DeleteItem  
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
 `TRUE` 如果项是位于并已成功删除;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="duplicatedata"></a>  CMFCToolBarComboBoxButton::DuplicateData  
 用户定义的数据相同。  
  
```  
virtual void DuplicateData();
```  
  
### <a name="remarks"></a>备注  
 默认情况下此方法没有任何影响。 如果你想要将任何用户定义数据复制，重写此方法在派生类。  
  
##  <a name="enablewindow"></a>  CMFCToolBarComboBoxButton::EnableWindow  
 启用或禁用编辑和组合框。  
  
```  
virtual void EnableWindow(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bEnable`  
 `TRUE` 若要启用的编辑和组合框;`FALSE`若要禁用编辑和组合框。  
  
### <a name="remarks"></a>备注  
 禁用时，这些控件不能成为活动状态，并且不能接受用户输入。  
  
##  <a name="exporttomenubutton"></a>  CMFCToolBarComboBoxButton::ExportToMenuButton  
 副本使用组合框按钮命令指定菜单应用程序字符串表中的字符串 id。  
  
```  
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;  
```  
  
### <a name="parameters"></a>参数  
 [out] `menuButton`  
 对菜单按钮的引用。  
  
### <a name="return-value"></a>返回值  
 总是为 `TRUE`。  
  
##  <a name="finditem"></a>  CMFCToolBarComboBoxButton::FindItem  
 返回包含指定的字符串的列表框中的第一项的索引。  
  
```  
int FindItem(LPCTSTR lpszText) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszText`  
 要在列表框中搜索文本。  
  
### <a name="return-value"></a>返回值  
 项; 的索引或`CB_ERR`如果未找到该项目。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getbycmd"></a>  CMFCToolBarComboBoxButton::GetByCmd  
 获取一个指针指向具有指定的命令 id。 组合框按钮  
  
```  
static CMFCToolBarComboBoxButton* GetByCmd(
    UINT uiCmd,  
    BOOL bIsFocus=FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `uiCmd`  
 组合框按钮命令 ID。  
  
 [in] `bIsFocus`  
 `TRUE` 若要只搜索已设定焦点的按钮;`FALSE`要搜索的所有按钮。  
  
### <a name="return-value"></a>返回值  
 组合框按钮; 指向的指针或`NULL`如果找不到按钮。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getcombobox"></a>  CMFCToolBarComboBoxButton::GetComboBox  
 将指针返回到组合框中组合框按钮。  
  
```  
CComboBox* GetComboBox() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向的指针[CComboBox 类](../../mfc/reference/ccombobox-class.md)对象方法是否成功; 否则为`NULL`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getcontextmenuid"></a>  CMFCToolBarComboBoxButton::GetContextMenuID  
 获取组合框按钮的快捷菜单资源 ID。  
  
```  
UINT GetContextMenuID();
```  
  
### <a name="return-value"></a>返回值  
 快捷菜单上的资源 id。  
  
##  <a name="getcount"></a>  CMFCToolBarComboBoxButton::GetCount  
 在列表框中返回的项数。  
  
```  
INT_PTR GetCount() const;  
```  
  
### <a name="return-value"></a>返回值  
 列表框中的项的数目。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getcountall"></a>  CMFCToolBarComboBoxButton::GetCountAll  
 获取具有指定的命令 id。 组合框按钮的列表框中的项的数目  
  
```  
static int GetCountAll(UINT uiCmd);
```  
  
### <a name="parameters"></a>参数  
 [in] `uiCmd`  
 组合框按钮命令 ID。  
  
### <a name="return-value"></a>返回值  
 列表框中; 中的项的数目否则为`CB_ERR`如果找不到组合框按钮。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getcursel"></a>  CMFCToolBarComboBoxButton::GetCurSel  
 在列表框中获取当前选定项的索引。  
  
```  
int GetCurSel() const;  
```  
  
### <a name="return-value"></a>返回值  
 在列表框中; 当前选定项的索引或`CB_ERR`如果未不选定任何项。  
  
### <a name="remarks"></a>备注  
 列表框索引是从零开始。  
  
##  <a name="getcurselall"></a>  CMFCToolBarComboBoxButton::GetCurSelAll  
 返回当前选定项的索引中组合的列表框中具有指定的命令 ID 的框按钮  
  
```  
static int GetCurSelAll(UINT uiCmd);
```  
  
### <a name="parameters"></a>参数  
 [in] `uiCmd`  
 组合框按钮命令 ID。  
  
### <a name="return-value"></a>返回值  
 在列表框中; 当前选定项的索引否则为`CB_ERR`如果未选定任何项，或找不到组合框按钮。  
  
### <a name="remarks"></a>备注  
 列表框索引是从零开始。  
  
##  <a name="geteditctrl"></a>  CMFCToolBarComboBoxButton::GetEditCtrl  
 将指针返回到编辑框中组合框按钮。  
  
```  
virtual CEdit* GetEditCtrl();
```  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则在编辑框中指向的指针否则为`NULL`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="gethwnd"></a>  CMFCToolBarComboBoxButton::GetHwnd  
 返回组合框的窗口句柄。  
  
```  
virtual HWND GetHwnd();
```  
  
### <a name="return-value"></a>返回值  
 窗口句柄，或`NULL`组合框是否不与窗口对象相关联。  
  
##  <a name="getitem"></a>  CMFCToolBarComboBoxButton::GetItem  
 返回与列表框中指定索引处的项关联的字符串。  
  
```  
LPCTSTR GetItem(int iIndex=-1) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `iIndex`  
 列表框中的项的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 指向与项; 关联的字符串的指针否则为`NULL`如果索引参数是无效的或者如果索引参数为-1，并且在组合框中没有未选择的项目。  
  
### <a name="remarks"></a>备注  
 为-1 索引参数返回当前选定的项的字符串。  
  
##  <a name="getitemall"></a>  CMFCToolBarComboBoxButton::GetItemAll  
 返回与具有指定的命令 id。 组合框按钮列表框中指定索引处的项关联的字符串  
  
```  
static LPCTSTR GetItemAll(
    UINT uiCmd,  
    int iIndex=-1);
```  
  
### <a name="parameters"></a>参数  
 [in] `uiCmd`  
 组合框按钮命令 ID。  
  
 [in] `iIndex`  
 列表框中的项的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则项的字符串指向的指针否则为`NULL`该索引无效，组合框按钮是否未找到，或如果索引为-1，并且在组合框中没有未选择的项目。  
  
### <a name="remarks"></a>备注  
 索引值为-1 返回的当前选定的项的字符串。  
  
##  <a name="getitemdata"></a>  CMFCToolBarComboBoxButton::GetItemData  
 返回与列表框中的特定索引处的项关联的数据。  
  
```  
DWORD_PTR GetItemData(int iIndex=-1) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `iIndex`  
 列表框中的项的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 与项; 关联的数据或如果该项不存在则为 0。  
  
### <a name="remarks"></a>备注  
 为-1 索引参数返回与当前所选的项关联的数据。  
  
##  <a name="getitemdataall"></a>  CMFCToolBarComboBoxButton::GetItemDataAll  
 返回与具有特定的命令 id。 组合框按钮的列表框中的特定索引处的项关联的数据  
  
```  
static DWORD_PTR GetItemDataAll(
    UINT uiCmd,  
    int iIndex=-1);
```  
  
### <a name="parameters"></a>参数  
 [in] `uiCmd`  
 组合框按钮命令 ID。  
  
 [in] `iIndex`  
 列表框中的项的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则与项关联的数据否则为 0，如果指定的索引不是有效的或找不到 CB_ERR 如果组合框按钮。  
  
### <a name="remarks"></a>备注  
 为-1 索引参数返回与当前所选的项关联的数据。  
  
##  <a name="getitemdataptrall"></a>  CMFCToolBarComboBoxButton::GetItemDataPtrAll  
 返回与具有特定的命令 id。 组合框按钮的列表框中的特定索引处的项关联的数据 此数据返回为指针。  
  
```  
static void* GetItemDataPtrAll(
    UINT uiCmd,  
    int iIndex=-1);
```  
  
### <a name="parameters"></a>参数  
 [in] `uiCmd`  
 组合框按钮命令 ID。  
  
 [in] `iIndex`  
 列表框中的项的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 一个指针，如果此方法成功，则与项目关联否则为-1，如果发生错误，或`NULL`如果找不到组合框按钮。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getprompt"></a>  CMFCToolBarComboBoxButton::GetPrompt  
 返回组合框按钮提示的字符串。  
  
```  
virtual CString GetPrompt() const;  
```  
  
### <a name="return-value"></a>返回值  
 提示的字符串。  
  
### <a name="remarks"></a>备注  
 当前未实现此方法。  
  
##  <a name="gettext"></a>  CMFCToolBarComboBoxButton::GetText  
 获取编辑框中的文本。  
  
```  
LPCTSTR GetText() const;  
```  
  
### <a name="return-value"></a>返回值  
 编辑框中的文本。  
  
### <a name="remarks"></a>备注  
  
##  <a name="gettextall"></a>  CMFCToolBarComboBoxButton::GetTextAll  
 获取具有指定的命令 id。 组合框按钮的编辑框中的文本  
  
```  
static LPCTSTR GetTextAll(UINT uiCmd);
```  
  
### <a name="parameters"></a>参数  
 [in] `uiCmd`  
 命令 ID 的特定组合框按钮。  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则编辑框中的文本否则为`NULL`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="hasfocus"></a>  CMFCToolBarComboBoxButton::HasFocus  
 指示是否对组合框当前具有焦点。  
  
```  
virtual BOOL HasFocus() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果组合框中当前具有焦点，则否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 此方法也返回`TRUE`如果组合框的任何子窗口当前具有焦点。  
  
##  <a name="iscentervert"></a>  CMFCToolBarComboBoxButton::IsCenterVert  
 返回应用程序中组合框按钮的垂直位置。  
  
```  
static BOOL IsCenterVert();
```  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果为中心的按钮;，`FALSE`如果顶部对齐按钮。  
  
### <a name="remarks"></a>备注  
  
##  <a name="isflatmode"></a>  CMFCToolBarComboBoxButton::IsFlatMode  
 返回应用程序中组合框按钮的平面样式外观。  
  
```  
static BOOL IsFlatMode();
```  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果按钮具有平面样式;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 组合框按钮的默认平面样式是 `FALSE.`  
  
##  <a name="isownerof"></a>  CMFCToolBarComboBoxButton::IsOwnerOf  
 指示指定的句柄是否与组合框按钮，或其某个子级相关联。  
  
```  
virtual BOOL IsOwnerOf(HWND hwnd);
```  
  
### <a name="parameters"></a>参数  
 [in] `hwnd`  
 窗口句柄。  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果句柄供电组合框按钮，或从一台其子;否则为`FALSE`。  
  
##  <a name="isribbonbutton"></a>  CMFCToolBarComboBoxButton::IsRibbonButton  
 指示组合框按钮是否位于功能区面板。  
  
```  
BOOL IsRibbonButton() const;  
```  
  
### <a name="return-value"></a>返回值  
 总是为 `FALSE`。  
  
### <a name="remarks"></a>备注  
 默认情况下，此方法始终返回`FALSE`，这意味着组合框按钮不会显示在功能区面板。  
  
##  <a name="iswindowvisible"></a>  CMFCToolBarComboBoxButton::IsWindowVisible  
 返回的可见性状态的组合框按钮。  
  
```  
virtual BOOL IsWindowVisible();
```  
  
### <a name="return-value"></a>返回值  
 组合框按钮的可见性状态。  
  
##  <a name="notifycommand"></a>  CMFCToolBarComboBoxButton::NotifyCommand  
 该值指示组合框按钮是否处理消息。  
  
```  
virtual BOOL NotifyCommand(int iNotifyCode);
```  
  
### <a name="parameters"></a>参数  
 [in] `iNotifyCode`  
 与命令关联的通知消息。  
  
### <a name="return-value"></a>返回值  
 是否组合框按钮处理的消息。  
  
##  <a name="onaddtocustomizepage"></a>  CMFCToolBarComboBoxButton::OnAddToCustomizePage  
 由框架调用时该按钮添加到**自定义**对话框。  
  
```  
virtual void OnAddToCustomizePage();
```  
  
##  <a name="oncalculatesize"></a>  CMFCToolBarComboBoxButton::OnCalculateSize  
 由框架调用以计算按钮的大小。  
  
```  
virtual SIZE OnCalculateSize(
    CDC* pDC,  
    const CSize& sizeDefault,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 设备上下文，显示组合框按钮。  
  
 [in] `sizeDefault`  
 组合框按钮默认大小。  
  
 [in] `bHorz`  
 在父级工具栏停靠状态。 `TRUE` 工具栏时水平停靠和`FALSE`时垂直停靠工具栏。  
  
### <a name="return-value"></a>返回值  
 A`SIZE`结构，它包含组合框按钮，以像素为单位的尺寸。  
  
##  <a name="onchangeparentwnd"></a>  CMFCToolBarComboBoxButton::OnChangeParentWnd  
 组合框按钮插入到一个新工具栏时，由框架调用。  
  
```  
virtual void OnChangeParentWnd(CWnd* pWndParent);
```  
  
### <a name="parameters"></a>参数  
 [in] `pWndParent`  
 指向新的父工具栏。  
  
##  <a name="onclick"></a>  CMFCToolBarComboBoxButton::OnClick  
 当用户单击组合框按钮时，由框架调用。  
  
```  
virtual BOOL OnClick(
    CWnd* pWnd,  
    BOOL bDelay = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `pWnd`  
 向组合框按钮的父窗口的指针。  
  
 [in] `bDelay`  
 保留供派生类中使用。  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果该方法处理路由事件。，否则为`FALSE`。  
  
##  <a name="onctlcolor"></a>  CMFCToolBarComboBoxButton::OnCtlColor  
 在用户更改设置组合框按钮颜色的父工具栏颜色时，由框架调用。  
  
```  
virtual HBRUSH OnCtlColor(
    CDC* pDC,  
    UINT nCtlColor);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 设备上下文，显示组合框按钮。  
  
 [in] `nCtlColor`  
 未使用。  
  
### <a name="return-value"></a>返回值  
 框架将使用绘制背景的组合框按钮的画笔的句柄。  
  
### <a name="remarks"></a>备注  
 此方法还设置组合框按钮文本颜色。  
  
##  <a name="ondraw"></a>  CMFCToolBarComboBoxButton::OnDraw  
 由框架调用以绘制使用指定的样式和选项的组合框按钮。  
  
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
 设备上下文显示按钮。  
  
 [in] `rect`  
 按钮的边框。  
  
 [in] `pImages`  
 与按钮的图像集合。  
  
 [in] `bHorz`  
 在父级工具栏停靠状态。 `TRUE` 工具栏时水平停靠和`FALSE`时垂直停靠工具栏。  
  
 [in] `bCustomizeMode`  
 应用程序是否在自定义模式。  
  
 [in] `bHighlight`  
 是否要绘制突出显示组合框按钮。  
  
 [in] `bDrawBorder`  
 是否要绘制了一个边框组合框按钮。  
  
 [in] `bGrayDisabledButtons`  
 `TRUE` 若要绘制阴影禁用的按钮;`FALSE`若要使用已禁用图像集合。  
  
##  <a name="ondrawoncustomizelist"></a>  CMFCToolBarComboBoxButton::OnDrawOnCustomizeList  
 由框架在绘制组合框按钮调用**命令**窗格**自定义**对话框。  
  
```  
virtual int OnDrawOnCustomizeList(
    CDC* pDC,  
    const CRect& rect,  
    BOOL bSelected);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 设备上下文，显示组合框按钮。  
  
 [in] `rect`  
 组合框按钮的边框。  
  
 [in] `bSelected`  
 `TRUE` 如果组合框按钮被选中;否则为`FALSE`。  
  
### <a name="return-value"></a>返回值  
 以像素为单位，组合框按钮的宽度。  
  
##  <a name="onglobalfontschanged"></a>  CMFCToolBarComboBoxButton::OnGlobalFontsChanged  
 由框架设置组合框按钮字体，应用程序字体更改时调用。  
  
```  
virtual void OnGlobalFontsChanged();
```  
  
##  <a name="onmove"></a>  CMFCToolBarComboBoxButton::OnMove  
 由框架调用以在父级工具栏移时改变组合框按钮的位置。  
  
```  
virtual void OnMove();
```  
  
##  <a name="onshow"></a>  CMFCToolBarComboBoxButton::OnShow  
 隐藏或显示组合框按钮时，由框架调用。  
  
```  
virtual void OnShow(BOOL bShow);
```  
  
### <a name="parameters"></a>参数  
 [in] `bShow`  
 是否要隐藏或显示组合框按钮。  
  
##  <a name="onsize"></a>  CMFCToolBarComboBoxButton::OnSize  
 由框架调用以在父级工具栏更改大小时更改组合框按钮的大小。  
  
```  
virtual void OnSize(int iSize);
```  
  
### <a name="parameters"></a>参数  
 [in] `iSize`  
 组合框按钮新宽度。  
  
##  <a name="onupdatetooltip"></a>  CMFCToolBarComboBoxButton::OnUpdateToolTip  
 在用户更改组合框按钮的工具提示时，由框架调用。  
  
```  
virtual BOOL OnUpdateToolTip(
    CWnd* pWndParent,  
    int iButtonIndex,  
    CToolTipCtrl& wndToolTip,  
    CString& str);
```  
  
### <a name="parameters"></a>参数  
 [in] `pWndParent`  
 到组合框按钮的父窗口的指针。  
  
 [in] `iButtonIndex`  
 组合框按钮的 ID。  
  
 [in] `wndToolTip`  
 若要将与组合框按钮相关联的工具提示。  
  
 [in] `str`  
 工具提示文本。  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果该方法处理路由事件。，否则为`FALSE`。  
  
##  <a name="removeallitems"></a>  CMFCToolBarComboBoxButton::RemoveAllItems  
 从列表和编辑框中删除所有项。  
  
```  
void RemoveAllItems();
```  
  
### <a name="remarks"></a>备注  
 中移除所有项从列表框中字符和编辑组合框控件。  
  
##  <a name="selectitem"></a>  CMFCToolBarComboBoxButton::SelectItem  
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
 列表框中的项的从零开始索引。  
  
 [in] `bNotify`  
 `TRUE` 若要通知的所选内容; 组合框按钮否则为`FALSE`。  
  
 [in] `dwData`  
 与列表框中的项关联的数据。  
  
 [in] `lpszText`  
 列表框中的项的文本。  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果此方法成功，则否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="selectitemall"></a>  CMFCToolBarComboBoxButton::SelectItemAll  
 具有指定的命令 id。 组合框按钮的列表框中选择项  
  
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
 包含列表框中组合框按钮命令 ID。  
  
 [in] `iIndex`  
 列表框中项的从零开始索引。 值-1 的列表框中删除任何当前所选内容，并清除编辑框。  
  
 [in] `dwData`  
 列表框中的项的数据。  
  
 [in] `lpszText`  
 列表框中的项的文本。  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果此方法成功，则否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="serialize"></a>  CMFCToolBarComboBoxButton::Serialize  
 从存档读取该对象或将其写入存档。  
  
```  
virtual void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>参数  
 [in, out] `ar`  
 `CArchive`要序列化对象。  
  
### <a name="remarks"></a>备注  
 中的设置`CArchive`对象确定此方法是读取还是写入存档。  
  
##  <a name="setaccdata"></a>  CMFCToolBarComboBoxButton::SetACCData  
 填充指定`CAccessibilityData`通过从组合框按钮可访问性数据的对象。  
  
```  
virtual BOOL SetACCData(
    CWnd* pParent,  
    CAccessibilityData& data);
```  
  
### <a name="parameters"></a>参数  
 [in] `pParent`  
 组合框按钮父窗口。  
  
 [out] `data`  
 A`CAccessibilityData`从组合框按钮接收可访问性数据的对象。  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果此方法成功，则否则为`FALSE`。  
  
##  <a name="setcentervert"></a>  CMFCToolBarComboBoxButton::SetCenterVert  
 应用程序中设置组合框按钮的垂直位置。  
  
```  
static void SetCenterVert(BOOL bCenterVert=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bCenterVert`  
 `TRUE` 到中心组合框按钮在工具栏中;`FALSE`对齐到工具栏顶部组合框按钮。  
  
### <a name="remarks"></a>备注  
 默认情况下，组合框按钮对齐到顶部。  
  
##  <a name="setcontextmenuid"></a>  CMFCToolBarComboBoxButton::SetContextMenuID  
 设置组合框按钮的快捷菜单资源 ID。  
  
```  
void SetContextMenuID(UINT uiResID);
```  
  
### <a name="parameters"></a>参数  
 [in] `uiResID`  
 快捷菜单上的资源 id。  
  
##  <a name="setdropdownheight"></a>  CMFCToolBarComboBoxButton::SetDropDownHeight  
 删除向下时，请设置列表框的高度。  
  
```  
void SetDropDownHeight(int nHeight);
```  
  
### <a name="parameters"></a>参数  
 [in] `nHeight`  
 以像素为单位，列表框的高度。  
  
### <a name="remarks"></a>备注  
 默认高度为 150 像素。  
  
##  <a name="setflatmode"></a>  CMFCToolBarComboBoxButton::SetFlatMode  
 应用程序中设置组合框按钮的平面样式外观。  
  
```  
static void SetFlatMode(BOOL bFlat=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bFlat`  
 `TRUE` 用于平面样式外观;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 组合框按钮的默认平面样式是`FALSE`。  
  
##  <a name="setstyle"></a>  CMFCToolBarComboBoxButton::SetStyle  
 设置组合框按钮指定的样式和重绘控件，如果未禁用。  
  
```  
virtual void SetStyle(UINT nStyle);
```  
  
### <a name="parameters"></a>参数  
 [in] `nStyle`  
 工具栏样式的按位组合 (OR)。  
  
### <a name="remarks"></a>备注  
 工具栏按钮样式的列表，请参阅[工具栏控件样式](../../mfc/reference/toolbar-control-styles.md)  
  
##  <a name="settext"></a>  CMFCToolBarComboBoxButton::SetText  
 在编辑框的组合框按钮设置的文本。  
  
```  
void SetText(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszText`  
 为包含编辑框的文本字符串的指针。  
  
## <a name="see-also"></a>请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBarButton 类](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [CComboBox 类](../../mfc/reference/ccombobox-class.md)   
 [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)   
 [演练：将控件置于工具栏上](../../mfc/walkthrough-putting-controls-on-toolbars.md)



