---
title: "CMFCRibbonCheckBox 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonCheckBox
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::CMFCRibbonCheckBox
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::GetCompactSize
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::GetIntermediateSize
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::GetRegularSize
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::IsDrawTooltipImage
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::OnDraw
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::OnDrawMenuImage
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::OnDrawOnList
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::SetACCData
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonCheckBox class
ms.assetid: 3a6c3891-c8d1-4af0-b954-7b9ab048782a
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
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 9efe04a8e79835b8e51b7045cb86ab2dba68b675
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcribboncheckbox-class"></a>CMFCRibbonCheckBox 类
`CMFCRibbonCheckBox` 类实现可添加到功能区面板、快速访问工具栏或弹出菜单的复选框。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCRibbonCheckBox : public CMFCRibbonButton  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCRibbonCheckBox::CMFCRibbonCheckBox](#cmfcribboncheckbox)|构造函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CMFCRibbonCheckBox::GetCompactSize](#getcompactsize)|(重写[CMFCRibbonButton::GetCompactSize](../../mfc/reference/cmfcribbonbutton-class.md#getcompactsize)。)|  
|[CMFCRibbonCheckBox::GetIntermediateSize](#getintermediatesize)|(重写[CMFCRibbonButton::GetIntermediateSize](../../mfc/reference/cmfcribbonbutton-class.md#getintermediatesize)。)|  
|[CMFCRibbonCheckBox::GetRegularSize](#getregularsize)|(重写[CMFCRibbonButton::GetRegularSize](../../mfc/reference/cmfcribbonbutton-class.md#getregularsize)。)|  
|[CMFCRibbonCheckBox::IsDrawTooltipImage](#isdrawtooltipimage)|（重写 `CMFCRibbonButton::IsDrawTooltipImage`。）|  
|[CMFCRibbonCheckBox::OnDraw](#ondraw)|(重写[CMFCRibbonButton::OnDraw](../../mfc/reference/cmfcribbonbutton-class.md#ondraw)。)|  
|[CMFCRibbonCheckBox::OnDrawMenuImage](#ondrawmenuimage)|(重写[CMFCRibbonBaseElement::OnDrawMenuImage](../../mfc/reference/cmfcribbonbaseelement-class.md#ondrawmenuimage)。)|  
|[CMFCRibbonCheckBox::OnDrawOnList](#ondrawonlist)|（重写 `CMFCRibbonButton::OnDrawOnList`。）|  
|[CMFCRibbonCheckBox::SetACCData](#setaccdata)|(重写[CMFCRibbonButton::SetACCData](../../mfc/reference/cmfcribbonbutton-class.md#setaccdata)。)|  
  
## <a name="remarks"></a>备注  
 若要在应用程序中使用 `CMFCRibbonCheckBox`，请向代码添加以下构造函数：  
  
```  
CMFCRibbonCheckBox (UINT nID, LPCTSTR lpszText)  
```  
其中 `nID` 是复选框命令 ID，`lpszText` 是复选框的文本标签。  
  
 可以通过向功能区面板中添加一个复选框[CMFCRibbonPanel::Add](../../mfc/reference/cmfcribbonpanel-class.md#add)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonCheckBox](../../mfc/reference/cmfcribboncheckbox-class.md)  
  
## <a name="requirements"></a>要求  
 **标头︰** afxribboncheckbox.h  
  
##  <a name="cmfcribboncheckbox"></a>CMFCRibbonCheckBox::CMFCRibbonCheckBox  
 功能区复选框对象构造函数  
  
```  
CMFCRibbonCheckBox(
    UINT nID,  
    LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>参数  
 [in] `nID`  
 指定命令 id。  
  
 [in] `lpszText`  
 指定文本标签。  
  
### <a name="return-value"></a>返回值  
 构造一个功能区复选框。  
  
### <a name="example"></a>示例  
 下面的示例演示如何构造的对象`CMFCRibbonCheckBox`类。  
  
 [!code-cpp[NVC_MFC_RibbonApp #&17;](../../mfc/reference/codesnippet/cpp/cmfcribboncheckbox-class_1.cpp)]  
  
##  <a name="getcompactsize"></a>CMFCRibbonCheckBox::GetCompactSize  
 重写时，获取该复选框的压缩大小。  
  
```  
virtual CSize GetCompactSize(CDC* pDC);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 指向`CDC`与该复选框相关联。  
  
### <a name="return-value"></a>返回值  
 返回`CSize`对象，其中包含复选框的压缩大小。  
  
### <a name="remarks"></a>备注  
 如果未重写，将返回复选框的中间大小。  
  
##  <a name="getintermediatesize"></a>CMFCRibbonCheckBox::GetIntermediateSize  
 获取复选框的中间大小。  
  
```  
virtual CSize GetIntermediateSize(CDC* pDC);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 指向`CDC`与此复选框相关联。  
  
### <a name="return-value"></a>返回值  
 一个`CSize`对象，其中包含复选框的中间大小。  
  
### <a name="remarks"></a>备注  
 如果未重写，将计算为默认复选框大小的中间大小 ( `AFX_CHECK_BOX_DEFAULT_SIZE`) 以及文本大小，以及边距。  
  
##  <a name="getregularsize"></a>CMFCRibbonCheckBox::GetRegularSize  
 获取复选框的常规大小。  
  
```  
virtual CSize GetRegularSize(CDC* pDC);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 指向`CDC`与此复选框相关联的对象。  
  
### <a name="return-value"></a>返回值  
 返回`CSize`对象，其中包含复选框的常规大小。  
  
### <a name="remarks"></a>备注  
 如果未重写，将返回复选框的中间大小。  
  
##  <a name="isdrawtooltipimage"></a>CMFCRibbonCheckBox::IsDrawTooltipImage  
 指示是否存在与该复选框相关联的工具提示映像。  
  
```  
virtual BOOL IsDrawTooltipImage() const;  
```  
  
### <a name="return-value"></a>返回值  
 返回`TRUE`如果复选框，与关联的工具提示映像或`FALSE`如果不是。  
  
### <a name="remarks"></a>备注  
  
##  <a name="ondraw"></a>CMFCRibbonCheckBox::OnDraw  
 由框架用于绘制该复选框，使用指定的设备上下文调用。  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 指向`CDC`要在其中绘制该复选框。  
  
### <a name="remarks"></a>备注  
  
##  <a name="ondrawmenuimage"></a>CMFCRibbonCheckBox::OnDrawMenuImage  
 由框架来绘制复选框的菜单图像调用。  
  
```  
virtual BOOL OnDrawMenuImage(CDC*, CRect);
```  
  
### <a name="parameters"></a>参数  
 [in] `CDC*`  
 指向`CDC`与该复选框相关联。  
  
 [in] `CRect`  
 一个`CRect`对象，它指定要在其中进行绘制的菜单图像的矩形。  
  
### <a name="return-value"></a>返回值  
 返回`TRUE`如果已绘制图像，或`FALSE`如果不是。  
  
### <a name="remarks"></a>备注  
 如果未重写，将返回`FALSE`。  
  
##  <a name="ondrawonlist"></a>CMFCRibbonCheckBox::OnDrawOnList  
 调用由框架来绘制命令列表框中的复选框。  
  
```  
virtual void OnDrawOnList(
    CDC* pDC,  
    CString strText,  
    int nTextOffset,  
    CRect rect,  
    BOOL bIsSelected,  
    BOOL bHighlighted);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 要在其中绘制该复选框的设备上下文的指针。  
  
 [in] `strText`  
 显示文本。  
  
 [in] `nTextOffset`  
 以像素为单位，从列表框中显示文本到左侧的距离。  
  
 [in] `rect`  
 复选框显示矩形。  
  
 [in] `bIsSelected`  
 `TRUE`如果选中该复选框，或`FALSE`如果不是。  
  
 [in] `bHighlighted`  
 `TRUE`如果突出显示该复选框时，或`FALSE`如果不是。  
  
### <a name="remarks"></a>备注  
  
##  <a name="setaccdata"></a>CMFCRibbonCheckBox::SetACCData  
 设置复选框的可访问性数据。  
  
```  
virtual BOOL SetACCData(
    CWnd* pParent,  
    CAccessibilityData& data);
```  
  
### <a name="parameters"></a>参数  
 `pParent`  
 父窗口的复选框。  
  
 `data`  
 复选框可访问性数据。  
  
### <a name="return-value"></a>返回值  
 始终返回 `TRUE`。  
  
### <a name="remarks"></a>备注  
 默认情况下此方法设置为复选框，并且始终可访问性数据返回`TRUE`。 重写此方法以设置可访问性数据并返回一个指示成功或失败的值。  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonPanel 类](../../mfc/reference/cmfcribbonpanel-class.md)

