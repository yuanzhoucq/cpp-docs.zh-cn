---
title: CMFCRibbonUndoButton 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
- CMFCRibbonUndoButton [MFC], CMFCRibbonUndoButton
- CMFCRibbonUndoButton [MFC], AddUndoAction
- CMFCRibbonUndoButton [MFC], CleanUpUndoList
- CMFCRibbonUndoButton [MFC], GetActionNumber
- CMFCRibbonUndoButton [MFC], HasMenu
ms.assetid: 5c42adf7-871d-4239-901e-47ae7fb816fc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 11c83332c12daa6753add0618367b90f8c759532
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/05/2018
ms.locfileid: "37848763"
---
# <a name="cmfcribbonundobutton-class"></a>CMFCRibbonUndoButton 类
`CMFCRibbonUndoButton`类实现包含最新的用户命令的下拉列表按钮。 用户可以从要重做或撤消它们的下拉列表选择一个或多个最新的命令。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCRibbonUndoButton : public CMFCRibbonGallery  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCRibbonUndoButton::CMFCRibbonUndoButton](#cmfcribbonundobutton)|构造一个新`CMFCRibbonUndoButton`通过使用指定的命令 ID、 文本标签和映像从父对象的图像列表对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCRibbonUndoButton::AddUndoAction](#addundoaction)|将新的操作添加到的操作的列表。|  
|[CMFCRibbonUndoButton::CleanUpUndoList](#cleanupundolist)|清除操作列表中，这是下拉列表。|  
|[CMFCRibbonUndoButton::GetActionNumber](#getactionnumber)|确定用户从下拉列表中选择的项的数目。|  
|[CMFCRibbonUndoButton::HasMenu](#hasmenu)|指示对象是否包含一个菜单。|  
  
## <a name="remarks"></a>备注  
 `CMFCRibbonUndoButton`类使用堆栈来表示下拉列表。  
  
## <a name="example"></a>示例  
 下面的示例演示如何构造的对象`CMFCRibbonUndoButton`类，并将新的操作添加到的操作的列表。 此代码片段属于[功能区的小工具示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_RibbonGadgets#2](../../mfc/reference/codesnippet/cpp/cmfcribbonundobutton-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonGallery](../../mfc/reference/cmfcribbongallery-class.md)  
  
 [CMFCRibbonUndoButton](../../mfc/reference/cmfcribbonundobutton-class.md)  
  
## <a name="requirements"></a>要求  
 **标头：** afxribbonundobutton.h  
  
##  <a name="addundoaction"></a>  CMFCRibbonUndoButton::AddUndoAction  
 将新的操作添加到的操作的列表。  
  
```  
void AddUndoAction(LPCTSTR lpszLabel);
```  
  
### <a name="parameters"></a>参数  
 [in]*lpszLabel*  
 将显示在下拉列表中的操作标签。  
  
##  <a name="cleanupundolist"></a>  CMFCRibbonUndoButton::CleanUpUndoList  
 清除操作列表中，这是下拉列表。  
  
```  
void CleanUpUndoList();
```  
  
##  <a name="cmfcribbonundobutton"></a>  CMFCRibbonUndoButton::CMFCRibbonUndoButton  
 构造一个新`CMFCRibbonUndoButton`通过使用指定的命令 ID、 文本标签和映像从父对象的图像列表对象。  
  
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
 [in]*nID*  
 指定命令标识符。  
  
 [in]*lpszText*  
 指定按钮的文本标签。  
  
 [in]*nSmallImageIndex*  
 中的图像列表的按钮的小图像的父对象的从零开始索引。  
  
 [in]*nLargeImageIndex*  
 从零开始的索引中的父对象的图像列表的按钮的大图像。  
  
 [in]*hIcon*  
 句柄可用作按钮的图像的图标。  
  
##  <a name="getactionnumber"></a>  CMFCRibbonUndoButton::GetActionNumber  
 确定用户从下拉列表中选择的项的数目。  
  
```  
int GetActionNumber() const;  
```  
  
### <a name="return-value"></a>返回值  
 用户选择的项目数。  
  
##  <a name="hasmenu"></a>  CMFCRibbonUndoButton::HasMenu  
 指示对象是否包含一个菜单。  
  
```  
virtual BOOL HasMenu() const;  
```  
  
### <a name="return-value"></a>返回值  
 始终返回 TRUE。  
  
### <a name="remarks"></a>备注  
  
## <a name="see-also"></a>请参阅  
 [层次结构图表](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonGallery 类](../../mfc/reference/cmfcribbongallery-class.md)   
 [CMFCRibbonButton 类](../../mfc/reference/cmfcribbonbutton-class.md)
