---
title: "CMFCRibbonComboBox 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonComboBox
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonComboBox class
ms.assetid: 9b29a6a4-cf17-4152-9b13-0bf90784b30d
caps.latest.revision: 35
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
ms.openlocfilehash: 747006ee66445eb312c22d658706e5fe81d2a958
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcribboncombobox-class"></a>CMFCRibbonComboBox 类
`CMFCRibbonComboBox`类实现可以将添加到功能区栏、 功能区面板或功能区弹出菜单的组合框控件。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCRibbonComboBox : public CMFCRibbonEdit  
```  
  
## <a name="members"></a>成员  
  
### <a name="constructors"></a>构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCRibbonComboBox::CMFCRibbonComboBox](#cmfcribboncombobox)|构造 CMFCRibbonComboBox 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CMFCRibbonComboBox::AddItem](#additem)|将唯一项追加到列表框中。|  
|[CMFCRibbonComboBox::DeleteItem](#deleteitem)|从列表框中删除指定的项。|  
|[CMFCRibbonComboBox::EnableDropDownListResize](#enabledropdownlistresize)|指定当将下拉列表框中是否可以更改大小。|  
|[CMFCRibbonComboBox::FindItem](#finditem)|返回与指定的字符串匹配的列表框中的第一项的索引。|  
|[CMFCRibbonComboBox::GetCount](#getcount)|在列表框中返回的项数。|  
|[CMFCRibbonComboBox::GetCurSel](#getcursel)|获取列表框中当前选定项的索引。|  
|[CMFCRibbonComboBox::GetDropDownHeight](#getdropdownheight)|在下拉列表框中时，请获取列表框的高度。|  
|[CMFCRibbonComboBox::GetIntermediateSize](#getintermediatesize)|返回在中间的模式下显示组合框的大小。|  
|[CMFCRibbonComboBox::GetItem](#getitem)|返回与列表框中指定索引处的项关联的字符串。|  
|[CMFCRibbonComboBox::GetItemData](#getitemdata)|返回与列表框中指定索引处的项关联的数据。|  
|[CMFCRibbonComboBox::HasEditBox](#haseditbox)|指示控件是否包含一个编辑框。|  
|[CMFCRibbonComboBox::IsResizeDropDownList](#isresizedropdownlist)|指示可以调整大小的列表框。|  
|[CMFCRibbonComboBox::OnSelectItem](#onselectitem)|当用户在列表框中选择某个项时，由框架调用。|  
|[CMFCRibbonComboBox::RemoveAllItems](#removeallitems)|从列表框中删除所有项目，并清除编辑框。|  
|[CMFCRibbonComboBox::SelectItem](#selectitem)|在列表框中选择一项。|  
|[CMFCRibbonComboBox::SetDropDownHeight](#setdropdownheight)|向下删除时，请设置列表框的高度。|  
  
## <a name="remarks"></a>备注  
 功能区组合框包含结合的静态标签或用户可以编辑的标签的列表框。 您必须指定你想创建功能区组合框中时的类型。  
  
## <a name="example"></a>示例  
 下面的示例演示如何构造的对象`CMFCRibbonComboBox`类、 将项添加到组合框、 组合框中选择一项和向面板中添加一个组合框。  
  
 [!code-cpp[NVC_MFC_RibbonApp #&11;](../../mfc/reference/codesnippet/cpp/cmfcribboncombobox-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)  
  
 [CMFCRibbonComboBox](../../mfc/reference/cmfcribboncombobox-class.md)  
  
## <a name="requirements"></a>要求  
 **标头︰** afxribboncombobox.h  
  
##  <a name="a-nameadditema--cmfcribboncomboboxadditem"></a><a name="additem"></a>CMFCRibbonComboBox::AddItem  
 将唯一项追加到列表框中。  
  
```  
virtual INT_PTR AddItem(
    LPCTSTR lpszItem,  
    DWORD_PTR dwData=0);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszItem`  
 要添加的项的字符串。  
  
 [in] `dwData`  
 与要添加的项关联的数据。  
  
### <a name="return-value"></a>返回值  
 追加的项的从零开始索引。  
  
##  <a name="a-namecmfcribboncomboboxa--cmfcribboncomboboxcmfcribboncombobox"></a><a name="cmfcribboncombobox"></a>CMFCRibbonComboBox::CMFCRibbonComboBox  
 构造 `CMFCRibbonComboBox` 对象。  
  
```  
public:  
CMFCRibbonComboBox(
    UINT nID,  
    BOOL bHasEditBox=TRUE,  
    Int nWidth=-1,  
    LPCTSTR lpszLabel=NULL,  
    Int nImage=-1);

protected:  
CMFCRibbonComboBox();
```  
  
### <a name="parameters"></a>参数  
 [in] `nID`  
 组合框的 ID。  
  
 [in] `bHasEditBox`  
 `TRUE`如果您希望控件; 内的编辑框`FALSE`否则为。  
  
 [in] `nWidth`  
 以像素为单位; 组合框的宽度或者-1 表示的默认宽度。  
  
 [in] `lpszLabel`  
 组合框显示标签。  
  
 [in] `nImage`  
 组合框的小图像索引。  
  
### <a name="remarks"></a>备注  
 默认宽度为 108 像素。  
  
##  <a name="a-namedeleteitema--cmfcribboncomboboxdeleteitem"></a><a name="deleteitem"></a>CMFCRibbonComboBox::DeleteItem  
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
 要删除的项的字符串。 如果有多个项目使用相同的字符串，将删除的第一项。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果指定的项已被删除;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameenabledropdownlistresizea--cmfcribboncomboboxenabledropdownlistresize"></a><a name="enabledropdownlistresize"></a>CMFCRibbonComboBox::EnableDropDownListResize  
 指定当将下拉列表框中是否可以更改大小。  
  
```  
void EnableDropDownListResize(BOOL bEnable=FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bEnable`  
 `TRUE`若要启用调整大小;`FALSE`禁用调整大小。  
  
### <a name="remarks"></a>备注  
 调整大小启用时，列表框中将更改调整大小以适合它显示的项。  
  
##  <a name="a-namefinditema--cmfcribboncomboboxfinditem"></a><a name="finditem"></a>CMFCRibbonComboBox::FindItem  
 返回与指定的字符串匹配的列表框中的第一项的索引。  
  
```  
int FindItem(LPCTSTR lpszText) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszText`  
 列表框中某项的字符串。  
  
### <a name="return-value"></a>返回值  
 从零开始的项的索引;否则为-1 找不到该项目。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namegetcounta--cmfcribboncomboboxgetcount"></a><a name="getcount"></a>CMFCRibbonComboBox::GetCount  
 在列表框中返回的项数。  
  
```  
INT_PTR GetCount() const;  
```  
  
### <a name="return-value"></a>返回值  
 列表框中或如果列表框中不包含任何项 0 中的项目数。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namegetcursela--cmfcribboncomboboxgetcursel"></a><a name="getcursel"></a>CMFCRibbonComboBox::GetCurSel  
 获取列表框中当前选定项的索引。  
  
```  
int GetCurSel() const;  
```  
  
### <a name="return-value"></a>返回值  
 在列表框中; 当前选定项的从零开始的索引否则为-1 未选定任何项。  
  
##  <a name="a-namegetdropdownheighta--cmfcribboncomboboxgetdropdownheight"></a><a name="getdropdownheight"></a>CMFCRibbonComboBox::GetDropDownHeight  
 在下拉列表框中时，请获取列表框的高度。  
  
```  
int GetDropDownHeight();
```  
  
### <a name="return-value"></a>返回值  
 以像素为单位的列表框的高度。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namegetintermediatesizea--cmfcribboncomboboxgetintermediatesize"></a><a name="getintermediatesize"></a>CMFCRibbonComboBox::GetIntermediateSize  
 返回在中间的模式下显示组合框的大小。  
  
```  
virtual CSize GetIntermediateSize(CDC* pDC);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 组合框中的设备上下文的指针。  
  
### <a name="return-value"></a>返回值  
 组合框的大小。  
  
### <a name="remarks"></a>备注  
 在显示的小图像时，返回的大小取决于组合框的大小。  
  
##  <a name="a-namegetitema--cmfcribboncomboboxgetitem"></a><a name="getitem"></a>CMFCRibbonComboBox::GetItem  
 返回与列表框中指定索引处的项关联的字符串。  
  
```  
LPCTSTR GetItem(int iIndex) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `iIndex`  
 在列表框中项的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 指向与项; 关联的字符串的指针否则为`NULL`如果索引参数无效，或者如果索引参数为-1，并且没有组合框中选定项。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namegetitemdataa--cmfcribboncomboboxgetitemdata"></a><a name="getitemdata"></a>CMFCRibbonComboBox::GetItemData  
 返回与列表框中指定索引处的项关联的数据。  
  
```  
DWORD_PTR GetItemData(int iIndex) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `iIndex`  
 在列表框中项的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 与项; 关联的数据0 或如果该项不存在，或者如果索引参数为-1，并且在列表框中不存在所选的项。  
  
##  <a name="a-namehaseditboxa--cmfcribboncomboboxhaseditbox"></a><a name="haseditbox"></a>CMFCRibbonComboBox::HasEditBox  
 指示控件是否包含一个编辑框。  
  
```  
BOOL HasEditBox() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果控件包含一个编辑框中;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameisresizedropdownlista--cmfcribboncomboboxisresizedropdownlist"></a><a name="isresizedropdownlist"></a>CMFCRibbonComboBox::IsResizeDropDownList  
 指示可以调整大小的列表框。  
  
```  
BOOL IsResizeDropDownList() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果可以调整列表框中;否则为`FALSE`。 [CMFCRibbonComboBox::EnableDropDownListResize](#enabledropdownlistresize)  
  
### <a name="remarks"></a>备注  
 您可以启用列表框中调整大小操作通过使用[CMFCRibbonComboBox::EnableDropDownListResize](#enabledropdownlistresize)方法。  
  
##  <a name="a-nameonselectitema--cmfcribboncomboboxonselectitem"></a><a name="onselectitem"></a>CMFCRibbonComboBox::OnSelectItem  
 当用户在列表框中选择某个项时，由框架调用。  
  
```  
virtual void OnSelectItem(int nItem);
```  
  
### <a name="parameters"></a>参数  
 [in] `nItem`  
 选定的项的索引。  
  
### <a name="remarks"></a>备注  
 如果您想要处理用户输入的选择，重写此方法。  
  
##  <a name="a-nameremoveallitemsa--cmfcribboncomboboxremoveallitems"></a><a name="removeallitems"></a>CMFCRibbonComboBox::RemoveAllItems  
 从列表框中删除所有项目，并清除编辑框。  
  
```  
void RemoveAllItems();
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameselectitema--cmfcribboncomboboxselectitem"></a><a name="selectitem"></a>CMFCRibbonComboBox::SelectItem  
 在列表框中选择一项。  
  
```  
BOOL SelectItem(int iIndex);
BOOL SelectItem(DWORD_PTR dwData);

BOOL SelectItem(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>参数  
 [in] `iIndex`  
 在列表框中项的从零开始索引。  
  
 [in] `dwData`  
 与列表框中的项关联的数据。  
  
 [in] `lpszText`  
 列表框中某项的字符串。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果此方法已成功，则否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namesetdropdownheighta--cmfcribboncomboboxsetdropdownheight"></a><a name="setdropdownheight"></a>CMFCRibbonComboBox::SetDropDownHeight  
 向下删除时，请设置列表框的高度。  
  
```  
void SetDropDownHeight(int nHeight);
```  
  
### <a name="parameters"></a>参数  
 [in] `nHeight`  
 以像素为单位的列表框的高度。  
  
### <a name="remarks"></a>备注  
 默认高度为 150 像素。  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonEdit 类](../../mfc/reference/cmfcribbonedit-class.md)

