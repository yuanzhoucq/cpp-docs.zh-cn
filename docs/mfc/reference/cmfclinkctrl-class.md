---
title: "CMFCLinkCtrl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCLinkCtrl
- AFXLINKCTRL/CMFCLinkCtrl
- AFXLINKCTRL/CMFCLinkCtrl::SetURL
- AFXLINKCTRL/CMFCLinkCtrl::SetURLPrefix
- AFXLINKCTRL/CMFCLinkCtrl::SizeToContent
- AFXLINKCTRL/CMFCLinkCtrl::OnDrawFocusRect
dev_langs:
- C++
helpviewer_keywords:
- CMFCLinkCtrl class
ms.assetid: 80f3874d-7cc8-410e-9ff1-62a225f5034b
caps.latest.revision: 27
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 8c926c0ef611470b137d2bb897c012a85645c90c
ms.lasthandoff: 02/24/2017

---
# <a name="cmfclinkctrl-class"></a>CMFCLinkCtrl 类
`CMFCLinkCtrl`类按钮显示为超链接，并单击该按钮时调用链接的目标。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCLinkCtrl : public CMFCButton  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCLinkCtrl::SetURL](#seturl)|将指定的 URL 显示为按钮文本。|  
|[CMFCLinkCtrl::SetURLPrefix](#seturlprefix)|设置隐式的协议 (例如，"http:") 的 url。|  
|[CMFCLinkCtrl::SizeToContent](#sizetocontent)|调整大小包含的按钮文本或位图按钮。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|说明|  
|----------|-----------------|  
|[CMFCLinkCtrl::OnDrawFocusRect](#ondrawfocusrect)|绘制聚焦框的按钮之前，由框架调用。|  
  
## <a name="remarks"></a>备注  
 当您单击一个按钮来派生自`CMFCLinkCtrl`类，则框架会将该按钮的 URL 传递以参数形式向`ShellExecute`方法。 则`ShellExecute`方法打开的 url 目标。  
  
## <a name="example"></a>示例  
 下面的示例演示如何设置的大小`CMFCLinkCtrl`对象，以及如何设置 url 和中的工具提示`CMFCLinkCtrl`对象。 此示例摘自[新控件示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_NewControls #&9;](../../mfc/reference/codesnippet/cpp/cmfclinkctrl-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls #&10;](../../mfc/reference/codesnippet/cpp/cmfclinkctrl-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 [CMFCButton](../../mfc/reference/cmfcbutton-class.md)  
  
 [CMFCLinkCtrl](../../mfc/reference/cmfclinkctrl-class.md)  
  
## <a name="requirements"></a>要求  
 **标头︰** afxlinkctrl.h  
  
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
 当您想要使用您自己的代码绘制按钮的聚焦框，重写此方法。  
  
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
 设置隐式的协议 (例如，"http:") 的 url。  
  
```  
void SetURLPrefix(LPCTSTR lpszPrefix);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszPrefix`  
 URL 协议前缀。  
  
### <a name="remarks"></a>备注  
 使用此方法设置的 URL 前缀。 前缀不会显示在按钮的表面，但可以使用它来帮助浏览到的 URL 目标。  
  
##  <a name="sizetocontent"></a>CMFCLinkCtrl::SizeToContent  
 调整大小包含的按钮文本或位图按钮。  
  
```  
virtual CSize SizeToContent(
    BOOL bVCenter=FALSE,  
    BOOL bHCenter=FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bVCenter`  
 `TRUE`若要居中按钮文本和位图顶部和底部的链接控件; 之间的垂直对齐否则为`FALSE`。 默认值为 `FALSE`。  
  
 [in] `bHCenter`  
 `TRUE`若要居中按钮文本和位图水平之间的左侧和右侧的链接控件;否则为`FALSE`。 默认值为 `FALSE`。  
  
### <a name="return-value"></a>返回值  
 一个[CSize](../../atl-mfc-shared/reference/csize-class.md)对象，其中包含链接控件的新大小。  
  
### <a name="remarks"></a>备注  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CLinkCtrl 类](../../mfc/reference/clinkctrl-class.md)   
 [CMFCButton 类](../../mfc/reference/cmfcbutton-class.md)

