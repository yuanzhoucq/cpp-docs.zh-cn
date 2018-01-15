---
title: "CMFCRibbonLinkCtrl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonLinkCtrl
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::CMFCRibbonLinkCtrl
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::CopyFrom
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::GetCompactSize
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::GetLink
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::GetRegularSize
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::GetToolTipText
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::IsDrawTooltipImage
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::OnDraw
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::OnDrawMenuImage
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::OnMouseMove
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::OnSetIcon
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::OpenLink
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::SetLink
dev_langs: C++
helpviewer_keywords:
- CMFCRibbonLinkCtrl [MFC], CMFCRibbonLinkCtrl
- CMFCRibbonLinkCtrl [MFC], CopyFrom
- CMFCRibbonLinkCtrl [MFC], GetCompactSize
- CMFCRibbonLinkCtrl [MFC], GetLink
- CMFCRibbonLinkCtrl [MFC], GetRegularSize
- CMFCRibbonLinkCtrl [MFC], GetToolTipText
- CMFCRibbonLinkCtrl [MFC], IsDrawTooltipImage
- CMFCRibbonLinkCtrl [MFC], OnDraw
- CMFCRibbonLinkCtrl [MFC], OnDrawMenuImage
- CMFCRibbonLinkCtrl [MFC], OnMouseMove
- CMFCRibbonLinkCtrl [MFC], OnSetIcon
- CMFCRibbonLinkCtrl [MFC], OpenLink
- CMFCRibbonLinkCtrl [MFC], SetLink
ms.assetid: 77ae1941-e0ab-4a9d-911e-1752d34c079b
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3007c98629b83e6302556582220684075d5049b6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcribbonlinkctrl-class"></a>CMFCRibbonLinkCtrl 类
实现位于功能区上的超链接。 当单击此超链接时，可以打开网页。  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCRibbonLinkCtrl : public CMFCRibbonButton  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCRibbonLinkCtrl::CMFCRibbonLinkCtrl](#cmfcribbonlinkctrl)|构造并初始化一个 `CMFCRibbonLinkCtrl` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCRibbonLinkCtrl::CopyFrom](#copyfrom)|（重写 `CMFCRibbonButton::CopyFrom`。）|  
|[CMFCRibbonLinkCtrl::GetCompactSize](#getcompactsize)|(重写[cmfcribbonbutton:: Getcompactsize](../../mfc/reference/cmfcribbonbutton-class.md#getcompactsize)。)|  
|[CMFCRibbonLinkCtrl::GetLink](#getlink)|返回超链接的值。|  
|[CMFCRibbonLinkCtrl::GetRegularSize](#getregularsize)|(重写[cmfcribbonbutton:: Getregularsize](../../mfc/reference/cmfcribbonbutton-class.md#getregularsize)。)|  
|[CMFCRibbonLinkCtrl::GetToolTipText](#gettooltiptext)|(重写[cmfcribbonbutton:: Gettooltiptext](../../mfc/reference/cmfcribbonbutton-class.md#gettooltiptext)。)|  
|[CMFCRibbonLinkCtrl::IsDrawTooltipImage](#isdrawtooltipimage)|（重写 `CMFCRibbonButton::IsDrawTooltipImage`。）|  
|[CMFCRibbonLinkCtrl::OnDraw](#ondraw)|(重写[cmfcribbonbutton:: Ondraw](../../mfc/reference/cmfcribbonbutton-class.md#ondraw)。)|  
|[CMFCRibbonLinkCtrl::OnDrawMenuImage](#ondrawmenuimage)|(重写[cmfcribbonbaseelement:: Ondrawmenuimage](../../mfc/reference/cmfcribbonbaseelement-class.md#ondrawmenuimage)。)|  
|[CMFCRibbonLinkCtrl::OnMouseMove](#onmousemove)|（重写 `CMFCRibbonButton::OnMouseMove`。）|  
|[CMFCRibbonLinkCtrl::OnSetIcon](#onseticon)||  
|[CMFCRibbonLinkCtrl::OpenLink](#openlink)|将打开超链接中指定的 Web 页。|  
|[CMFCRibbonLinkCtrl::SetLink](#setlink)|设置超链接的值。|  
  
## <a name="remarks"></a>备注  
 创建一个超链接后，将其添加到面板通过调用[cmfcribbonpanel:: Add](../../mfc/reference/cmfcribbonpanel-class.md#add)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md) [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md) [CMFCRibbonLinkCtrl](../../mfc/reference/cmfcribbonlinkctrl-class.md)  
  
## <a name="requirements"></a>惠?  
 **标头：** afxRibbonLinkCtrl.h  
  
##  <a name="cmfcribbonlinkctrl"></a>CMFCRibbonLinkCtrl::CMFCRibbonLinkCtrl  
 构造并初始化[CMFCRibbonLinkCtrl](../../mfc/reference/cmfcribbonlinkctrl-class.md)对象。  
  
```  
CMFCRibbonLinkCtrl(
    UINT nID,  
    LPCTSTR lpszText,  
    LPCTSTR lpszLink);
```  
  
### <a name="parameters"></a>参数  
 [in] `nID`  
 指定在单击链接控件时执行的命令的命令 ID。  
  
 [in] `lpszText`  
 指定要在链接控件上显示的标签。  
  
 [in] `lpszLink`  
 指定与链接控件关联的超链接。  
  
### <a name="example"></a>示例  
 下面的示例演示如何使用的构造函数`CMFCRibbonLinkCtrl`类。 此代码片段属于[功能区的小工具示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_RibbonGadgets#1](../../mfc/reference/codesnippet/cpp/cmfcribbonlinkctrl-class_1.cpp)]  
  
##  <a name="copyfrom"></a>CMFCRibbonLinkCtrl::CopyFrom  

  
```  
virtual void CopyFrom(const CMFCRibbonBaseElement& src);
```  
  
### <a name="parameters"></a>参数  
 [in] `src`  
  
### <a name="remarks"></a>备注  
  
##  <a name="getcompactsize"></a>CMFCRibbonLinkCtrl::GetCompactSize  

  
```  
virtual CSize GetCompactSize(CDC* pDC);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="getlink"></a>CMFCRibbonLinkCtrl::GetLink  
 返回超链接的值。  
  
```  
LPCTSTR GetLink() const;  
```  
  
### <a name="return-value"></a>返回值  
 超链接的当前值。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getregularsize"></a>CMFCRibbonLinkCtrl::GetRegularSize  

  
```  
virtual CSize GetRegularSize(CDC* pDC);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="gettooltiptext"></a>CMFCRibbonLinkCtrl::GetToolTipText  

  
```  
virtual CString GetToolTipText() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="ondrawmenuimage"></a>CMFCRibbonLinkCtrl::OnDrawMenuImage  

  
```  
virtual BOOL OnDrawMenuImage(CDC*, CRect);
```  
  
### <a name="parameters"></a>参数  
 [in] `CDC*`  
 [in] `CRect`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="isdrawtooltipimage"></a>CMFCRibbonLinkCtrl::IsDrawTooltipImage  

  
```  
virtual BOOL IsDrawTooltipImage() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="ondraw"></a>CMFCRibbonLinkCtrl::OnDraw  

  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
  
### <a name="remarks"></a>备注  
  
##  <a name="onmousemove"></a>CMFCRibbonLinkCtrl::OnMouseMove  

  
```  
virtual void OnMouseMove(CPoint point);
```  
  
### <a name="parameters"></a>参数  
 [in] `point`  
  
### <a name="remarks"></a>备注  
  
##  <a name="onseticon"></a>CMFCRibbonLinkCtrl::OnSetIcon  

  
```  
virtual void OnSetIcon();
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="openlink"></a>CMFCRibbonLinkCtrl::OpenLink  
 将打开超链接中指定的 Web 页。  
  
```  
BOOL OpenLink();
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果成功，则打开关联的 Web 页否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 会打开一个网页，使用相应的超链接`CMFCRibbonLinkCtrl`对象。  
  
##  <a name="setlink"></a>CMFCRibbonLinkCtrl::SetLink  
 设置超链接的值。  
  
```  
void SetLink(LPCTSTR lpszLink);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszLink`  
 指定的超链接文本。  
  
## <a name="see-also"></a>请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonButton 类](../../mfc/reference/cmfcribbonbutton-class.md)
