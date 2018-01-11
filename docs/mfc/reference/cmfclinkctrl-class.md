---
title: "CMFCLinkCtrl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCLinkCtrl
- AFXLINKCTRL/CMFCLinkCtrl
- AFXLINKCTRL/CMFCLinkCtrl::SetURL
- AFXLINKCTRL/CMFCLinkCtrl::SetURLPrefix
- AFXLINKCTRL/CMFCLinkCtrl::SizeToContent
- AFXLINKCTRL/CMFCLinkCtrl::OnDrawFocusRect
dev_langs: C++
helpviewer_keywords:
- CMFCLinkCtrl [MFC], SetURL
- CMFCLinkCtrl [MFC], SetURLPrefix
- CMFCLinkCtrl [MFC], SizeToContent
- CMFCLinkCtrl [MFC], OnDrawFocusRect
ms.assetid: 80f3874d-7cc8-410e-9ff1-62a225f5034b
caps.latest.revision: "27"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: fc83e5abf09102af8f27b1ee73fc78ed162b9335
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cmfclinkctrl-class"></a>CMFCLinkCtrl 类
`CMFCLinkCtrl`类按钮显示为超链接并单击该按钮时调用链接的目标。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCLinkCtrl : public CMFCButton  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCLinkCtrl::SetURL](#seturl)|将指定的 URL 显示为按钮文本。|  
|[CMFCLinkCtrl::SetURLPrefix](#seturlprefix)|设置的隐式的协议 (例如，"http:") 的 URL。|  
|[CMFCLinkCtrl::SizeToContent](#sizetocontent)|调整大小时，包含按钮文本或位图按钮。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCLinkCtrl::OnDrawFocusRect](#ondrawfocusrect)|绘制聚焦框的按钮之前，由框架调用。|  
  
## <a name="remarks"></a>备注  
 当你单击一个按钮来派生自`CMFCLinkCtrl`类，则框架会将按钮的 URL 传递作为参数传递给`ShellExecute`方法。 则`ShellExecute`方法打开的 URL 目标。  
  
## <a name="example"></a>示例  
 下面的示例演示如何设置的大小`CMFCLinkCtrl`对象，以及如何设置 url 和中的工具提示`CMFCLinkCtrl`对象。 此示例摘自[新控件示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_NewControls#9](../../mfc/reference/codesnippet/cpp/cmfclinkctrl-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#10](../../mfc/reference/codesnippet/cpp/cmfclinkctrl-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 [CMFCButton](../../mfc/reference/cmfcbutton-class.md)  
  
 [CMFCLinkCtrl](../../mfc/reference/cmfclinkctrl-class.md)  
  
## <a name="requirements"></a>惠?  
 **标头：** afxlinkctrl.h  
  
##  <a name="ondrawfocusrect"></a>CMFCLinkCtrl::OnDrawFocusRect  
 绘制聚焦框的按钮之前，由框架调用。  
  
```  
virtual void OnDrawFocusRect(
    CDC* pDC,  
    const CRect& rectClient);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 一个指向设备上下文的指针。  
  
 [in] `rectClient`  
 限定链接控件的矩形。  
  
### <a name="remarks"></a>备注  
 当你想要使用你自己的代码绘制按钮的聚焦框时，重写此方法。  
  
##  <a name="seturl"></a>CMFCLinkCtrl::SetURL  
 将指定的 URL 显示为按钮文本。  
  
```  
void SetURL(LPCTSTR lpszURL);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszURL`  
 要显示的按钮文本。  
  
### <a name="remarks"></a>备注  
  
##  <a name="seturlprefix"></a>CMFCLinkCtrl::SetURLPrefix  
 设置的隐式的协议 (例如，"http:") 的 URL。  
  
```  
void SetURLPrefix(LPCTSTR lpszPrefix);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszPrefix`  
 URL 协议的前缀。  
  
### <a name="remarks"></a>备注  
 使用此方法设置的 URL 前缀。 前缀不会显示在按钮的表面，但可以使用它来帮助浏览到的 URL 目标。  
  
##  <a name="sizetocontent"></a>CMFCLinkCtrl::SizeToContent  
 调整大小时，包含按钮文本或位图按钮。  
  
```  
virtual CSize SizeToContent(
    BOOL bVCenter=FALSE,  
    BOOL bHCenter=FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bVCenter`  
 `TRUE`到中心按钮文本和位图的顶部和底部的链接控件; 之间的垂直对齐否则为`FALSE`。 默认值为 `FALSE`。  
  
 [in] `bHCenter`  
 `TRUE`到中心按钮文本和位图水平之间的左侧和右侧的链接控件;否则为`FALSE`。 默认值为 `FALSE`。  
  
### <a name="return-value"></a>返回值  
 A [CSize](../../atl-mfc-shared/reference/csize-class.md)对象，其中包含链接控件的新大小。  
  
### <a name="remarks"></a>备注  
  
## <a name="see-also"></a>请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CLinkCtrl 类](../../mfc/reference/clinkctrl-class.md)   
 [CMFCButton 类](../../mfc/reference/cmfcbutton-class.md)
