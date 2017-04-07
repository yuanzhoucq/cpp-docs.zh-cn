---
title: "CMFCRibbonUndoButton 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonUndoButton
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::CMFCRibbonUndoButton
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::AddUndoAction
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::CleanUpUndoList
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::GetActionNumber
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::HasMenu
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonUndoButton class
ms.assetid: 5c42adf7-871d-4239-901e-47ae7fb816fc
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
ms.openlocfilehash: d4406e21a7e2a945965020d85a748b93d66b5682
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcribbonundobutton-class"></a>CMFCRibbonUndoButton 类
`CMFCRibbonUndoButton`类实现一个包含最新的用户命令的下拉列表按钮。 用户可以选择一个或多个最新的命令，从下拉列表，以重做或撤消它们。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCRibbonUndoButton : public CMFCRibbonGallery  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCRibbonUndoButton::CMFCRibbonUndoButton](#cmfcribbonundobutton)|构造一个新`CMFCRibbonUndoButton`通过使用您指定的命令 ID、 文本标签和映像从父对象的图像列表对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CMFCRibbonUndoButton::AddUndoAction](#addundoaction)|操作的列表中添加一个新的操作。|  
|[CMFCRibbonUndoButton::CleanUpUndoList](#cleanupundolist)|清除操作列表中，这是下拉列表。|  
|[CMFCRibbonUndoButton::GetActionNumber](#getactionnumber)|确定用户从下拉列表中选择的项的数目。|  
|[CMFCRibbonUndoButton::HasMenu](#hasmenu)|指示对象是否包含一个菜单。|  
  
## <a name="remarks"></a>备注  
 `CMFCRibbonUndoButton`类使用堆栈来表示的下拉列表。  
  
## <a name="example"></a>示例  
 下面的示例演示如何构造的对象`CMFCRibbonUndoButton`类，并将新的操作添加到操作的列表。 此代码段属于[功能区的小工具示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_RibbonGadgets #&2;](../../mfc/reference/codesnippet/cpp/cmfcribbonundobutton-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonGallery](../../mfc/reference/cmfcribbongallery-class.md)  
  
 [CMFCRibbonUndoButton](../../mfc/reference/cmfcribbonundobutton-class.md)  
  
## <a name="requirements"></a>要求  
 **标头︰** afxribbonundobutton.h  
  
##  <a name="addundoaction"></a>CMFCRibbonUndoButton::AddUndoAction  
 操作的列表中添加一个新的操作。  
  
```  
void AddUndoAction(LPCTSTR lpszLabel);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszLabel`  
 将显示在下拉列表中的操作标签。  
  
##  <a name="cleanupundolist"></a>CMFCRibbonUndoButton::CleanUpUndoList  
 清除操作列表中，这是下拉列表。  
  
```  
void CleanUpUndoList();
```  
  
##  <a name="cmfcribbonundobutton"></a>CMFCRibbonUndoButton::CMFCRibbonUndoButton  
 构造一个新`CMFCRibbonUndoButton`通过使用您指定的命令 ID、 文本标签和映像从父对象的图像列表对象。  
  
```  
CMFCRibbonUndoButton(
    UINT nID,  
    LPCTSTR lpszText,  
    int nSmallImageIndex=-1,  
    int nLargeImageIndex=-1);

 
CMFCRibbonUndoButton(
    UINT nID,  
    LPCTSTR lpszText,  
    HICON hIcon);
```  
  
### <a name="parameters"></a>参数  
 [in] `nID`  
 指定命令标识符。  
  
 [in] `lpszText`  
 指定按钮的文本标签。  
  
 [in] `nSmallImageIndex`  
 该按钮的小图像的父对象的图像列表中的从零开始索引。  
  
 [in] `nLargeImageIndex`  
 从零开始的索引的父对象的图像列表中的按钮的大图像。  
  
 [in] `hIcon`  
 您可以使用作为按钮的图像的图标句柄。  
  
##  <a name="getactionnumber"></a>CMFCRibbonUndoButton::GetActionNumber  
 确定用户从下拉列表中选择的项的数目。  
  
```  
int GetActionNumber() const;  
```  
  
### <a name="return-value"></a>返回值  
 用户选择的项目数。  
  
##  <a name="hasmenu"></a>CMFCRibbonUndoButton::HasMenu  
 指示对象是否包含一个菜单。  
  
```  
virtual BOOL HasMenu() const;  
```  
  
### <a name="return-value"></a>返回值  
 始终返回 `TRUE`。  
  
### <a name="remarks"></a>备注  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonGallery 类](../../mfc/reference/cmfcribbongallery-class.md)   
 [CMFCRibbonButton 类](../../mfc/reference/cmfcribbonbutton-class.md)

