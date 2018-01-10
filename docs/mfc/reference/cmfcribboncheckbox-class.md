---
title: "CMFCRibbonCheckBox 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
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
dev_langs: C++
helpviewer_keywords:
- CMFCRibbonCheckBox [MFC], CMFCRibbonCheckBox
- CMFCRibbonCheckBox [MFC], GetCompactSize
- CMFCRibbonCheckBox [MFC], GetIntermediateSize
- CMFCRibbonCheckBox [MFC], GetRegularSize
- CMFCRibbonCheckBox [MFC], IsDrawTooltipImage
- CMFCRibbonCheckBox [MFC], OnDraw
- CMFCRibbonCheckBox [MFC], OnDrawMenuImage
- CMFCRibbonCheckBox [MFC], OnDrawOnList
- CMFCRibbonCheckBox [MFC], SetACCData
ms.assetid: 3a6c3891-c8d1-4af0-b954-7b9ab048782a
caps.latest.revision: "30"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bc46d934c99e24b63ef314ef1f63402893c6bb18
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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
  
|名称|描述|  
|----------|-----------------|  
|[CMFCRibbonCheckBox::GetCompactSize](#getcompactsize)|(重写[cmfcribbonbutton:: Getcompactsize](../../mfc/reference/cmfcribbonbutton-class.md#getcompactsize)。)|  
|[CMFCRibbonCheckBox::GetIntermediateSize](#getintermediatesize)|(重写[cmfcribbonbutton:: Getintermediatesize](../../mfc/reference/cmfcribbonbutton-class.md#getintermediatesize)。)|  
|[CMFCRibbonCheckBox::GetRegularSize](#getregularsize)|(重写[cmfcribbonbutton:: Getregularsize](../../mfc/reference/cmfcribbonbutton-class.md#getregularsize)。)|  
|[CMFCRibbonCheckBox::IsDrawTooltipImage](#isdrawtooltipimage)|（重写 `CMFCRibbonButton::IsDrawTooltipImage`。）|  
|[CMFCRibbonCheckBox::OnDraw](#ondraw)|(重写[cmfcribbonbutton:: Ondraw](../../mfc/reference/cmfcribbonbutton-class.md#ondraw)。)|  
|[CMFCRibbonCheckBox::OnDrawMenuImage](#ondrawmenuimage)|(重写[cmfcribbonbaseelement:: Ondrawmenuimage](../../mfc/reference/cmfcribbonbaseelement-class.md#ondrawmenuimage)。)|  
|[CMFCRibbonCheckBox::OnDrawOnList](#ondrawonlist)|（重写 `CMFCRibbonButton::OnDrawOnList`。）|  
|[CMFCRibbonCheckBox::SetACCData](#setaccdata)|(重写[cmfcribbonbutton:: Setaccdata](../../mfc/reference/cmfcribbonbutton-class.md#setaccdata)。)|  
  
## <a name="remarks"></a>备注  
 若要在应用程序中使用 `CMFCRibbonCheckBox`，请向代码添加以下构造函数：  
  
```  
CMFCRibbonCheckBox (UINT nID, LPCTSTR lpszText)  
```  
其中 `nID` 是复选框命令 ID，`lpszText` 是复选框的文本标签。  
  
 可以通过向功能区面板中添加一个复选框[cmfcribbonpanel:: Add](../../mfc/reference/cmfcribbonpanel-class.md#add)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonCheckBox](../../mfc/reference/cmfcribboncheckbox-class.md)  
  
## <a name="requirements"></a>惠?  
 **标头：** afxribboncheckbox.h  
  
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
 构造一个功能区复选框对象。  
  
### <a name="example"></a>示例  
 下面的示例演示如何构造的对象`CMFCRibbonCheckBox`类。  
  
 [!code-cpp[NVC_MFC_RibbonApp#17](../../mfc/reference/codesnippet/cpp/cmfcribboncheckbox-class_1.cpp)]  
  
##  <a name="getcompactsize"></a>CMFCRibbonCheckBox::GetCompactSize  
 重写时，获取复选框的压缩大小。  
  
```  
virtual CSize GetCompactSize(CDC* pDC);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 指向`CDC`与复选框。  
  
### <a name="return-value"></a>返回值  
 返回`CSize`对象，其中包含复选框的压缩大小。  
  
### <a name="remarks"></a>备注  
 如果未重写时，返回复选框的中间的大小。  
  
##  <a name="getintermediatesize"></a>CMFCRibbonCheckBox::GetIntermediateSize  
 获取复选框的中间大小。  
  
```  
virtual CSize GetIntermediateSize(CDC* pDC);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 指向`CDC`与此复选框。  
  
### <a name="return-value"></a>返回值  
 A`CSize`对象，其中包含复选框的中间大小。  
  
### <a name="remarks"></a>备注  
 如果未重写，计算为的默认复选框大小的中间大小 ( `AFX_CHECK_BOX_DEFAULT_SIZE`) 加上的文本大小加上边距。  
  
##  <a name="getregularsize"></a>CMFCRibbonCheckBox::GetRegularSize  
 获取复选框的常规大小。  
  
```  
virtual CSize GetRegularSize(CDC* pDC);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 指向`CDC`对象与此复选框。  
  
### <a name="return-value"></a>返回值  
 返回`CSize`对象，其中包含复选框的常规大小。  
  
### <a name="remarks"></a>备注  
 如果未重写时，返回复选框的中间的大小。  
  
##  <a name="isdrawtooltipimage"></a>CMFCRibbonCheckBox::IsDrawTooltipImage  
 指示是否有关联的复选框的工具提示图像。  
  
```  
virtual BOOL IsDrawTooltipImage() const;  
```  
  
### <a name="return-value"></a>返回值  
 返回`TRUE`如果没有复选框，关联的工具提示图像或`FALSE`如果不是。  
  
### <a name="remarks"></a>备注  
  
##  <a name="ondraw"></a>CMFCRibbonCheckBox::OnDraw  
 由框架调用以绘制使用指定的设备上下文的复选框。  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 指向`CDC`要在其中绘制该复选框。  
  
### <a name="remarks"></a>备注  
  
##  <a name="ondrawmenuimage"></a>CMFCRibbonCheckBox::OnDrawMenuImage  
 由框架调用以绘制菜单图像复选框。  
  
```  
virtual BOOL OnDrawMenuImage(CDC*, CRect);
```  
  
### <a name="parameters"></a>参数  
 [in] `CDC*`  
 指向`CDC`与复选框。  
  
 [in] `CRect`  
 A`CRect`对象，它指定在其中绘制菜单图像的矩形。  
  
### <a name="return-value"></a>返回值  
 返回`TRUE`如果绘制图像，或`FALSE`如果不是。  
  
### <a name="remarks"></a>备注  
 如果未重写，则返回`FALSE`。  
  
##  <a name="ondrawonlist"></a>CMFCRibbonCheckBox::OnDrawOnList  
 由框架调用以绘制命令列表框中的复选框。  
  
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
 距离，以像素为单位，从左侧的列表框中为显示文本内容。  
  
 [in] `rect`  
 复选框显示矩形。  
  
 [in] `bIsSelected`  
 `TRUE`如果选中的复选框，或`FALSE`如果不是。  
  
 [in] `bHighlighted`  
 `TRUE`如果突出显示复选框时，或`FALSE`如果不是。  
  
### <a name="remarks"></a>备注  
  
##  <a name="setaccdata"></a>CMFCRibbonCheckBox::SetACCData  
 设置复选框可访问性数据。  
  
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
 默认情况下此方法设置可访问性数据复选框，始终返回`TRUE`。 重写此方法以设置可访问性数据并返回一个指示成功或失败的值。  
  
## <a name="see-also"></a>请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonPanel 类](../../mfc/reference/cmfcribbonpanel-class.md)
