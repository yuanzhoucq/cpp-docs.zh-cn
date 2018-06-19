---
title: CMFCRibbonLabel 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCRibbonLabel
- AFXRIBBONLABEL/CMFCRibbonLabel
- AFXRIBBONLABEL/CMFCRibbonLabel::CMFCRibbonLabel
- AFXRIBBONLABEL/CMFCRibbonLabel::SetACCData
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonLabel [MFC], CMFCRibbonLabel
- CMFCRibbonLabel [MFC], SetACCData
ms.assetid: 0346c891-83bf-4f20-b8a1-c84cf2aadced
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fcbc552560325e844cf0812a3002088f829d6c60
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33370117"
---
# <a name="cmfcribbonlabel-class"></a>CMFCRibbonLabel 类
实现功能区的不可单击文本标签。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCRibbonLabel : public CMFCRibbonButton  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCRibbonLabel::CMFCRibbonLabel](#cmfcribbonlabel)|构造并初始化`CMFCRibbonLabel`与指定的文本字符串的对象。|  
|`CMFCRibbonLabel::~CMFCRibbonLabel`|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|`CMFCRibbonLabel::CreateObject`|由框架用于创建此类类型的动态实例。|  
|`CMFCRibbonLabel::GetThisClass`|由框架用于获取指向的指针[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)与此类类型关联的对象。|  
|[CMFCRibbonLabel::SetACCData](#setaccdata)|确定当前的功能区 label 元素的可访问性数据。 (重写[cmfcribbonbutton:: Setaccdata](../../mfc/reference/cmfcribbonbutton-class.md#setaccdata)。)|  
  
### <a name="remarks"></a>备注  
 创建功能区的标签后，将其添加到面板通过调用[cmfcribbonpanel:: Add](../../mfc/reference/cmfcribbonpanel-class.md#add)。  
  
 无法将功能区标签添加到快速访问工具栏。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonLabel](../../mfc/reference/cmfcribbonlabel-class.md)  
  
## <a name="requirements"></a>要求  
 **标头：** afxRibbonLabel.h  
  
##  <a name="cmfcribbonlabel"></a>  CMFCRibbonLabel::CMFCRibbonLabel  
 构造并初始化[CMFCRibbonLabel](../../mfc/reference/cmfcribbonlabel-class.md)显示指定的文本字符串的对象。  
  
```  
CMFCRibbonLabel(
    LPCTSTR lpszText,  
    BOOL bIsMultiLine = FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszText`  
 要在标签中显示的文本。  
  
 [in] `bIsMultiLine`  
 `TRUE` 若要指定标签是多行标签;否则为`FALSE`。  
  
##  <a name="setaccdata"></a>  CMFCRibbonLabel::SetACCData  
 确定当前的功能区 label 元素的可访问性数据。  
  
```  
virtual BOOL SetACCData(
    CWnd* pParent,  
    CAccessibilityData& data);
```  
  
### <a name="parameters"></a>参数  
 [in] `pParent`  
 表示当前的功能区标签的父窗口。  
  
 [out] `data`  
 类型的对象`CAccessibilityData`并且填充了当前的功能区标签可访问性数据。  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果`data`参数已成功填充了当前的功能区标签可访问性数据; 否则为`FALSE`。  
  
## <a name="see-also"></a>请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonButton 类](../../mfc/reference/cmfcribbonbutton-class.md)
