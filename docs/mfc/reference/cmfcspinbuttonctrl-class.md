---
title: "CMFCSpinButtonCtrl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCSpinButtonCtrl
- AFXSPINBUTTONCTRL/CMFCSpinButtonCtrl
- AFXSPINBUTTONCTRL/CMFCSpinButtonCtrl::OnDraw
dev_langs: C++
helpviewer_keywords: CMFCSpinButtonCtrl [MFC], OnDraw
ms.assetid: 8773f259-4d3f-4bca-a71c-09e0c71bc843
caps.latest.revision: "25"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bd6ef1957b1f4994bafa9546581e2588e33d11a7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcspinbuttonctrl-class"></a>CMFCSpinButtonCtrl 类
`CMFCSpinButtonCtrl`类支持绘制数值调节钮控件的可视管理器。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCSpinButtonCtrl : public CSpinButtonCtrl  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|`CMFCSpinButtonCtrl::CMFCSpinButtonCtrl`|默认构造函数。|  
|`CMFCSpinButtonCtrl::~CMFCSpinButtonCtrl`|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCSpinButtonCtrl::OnDraw](#ondraw)|重新绘制当前数值调节钮控件。|  
  
## <a name="remarks"></a>备注  
 若要使用视觉管理器在你的应用程序中绘制数值调节钮控件的所有实例都替换`CSpinButtonCtrl`类，该类具有`CMFCSpinButtonCtrl`类。  
  
## <a name="example"></a>示例  
 下面的示例演示如何创建的对象`CMFCSpinButtonCtrl`类并使用其`Create`方法。  
  
 [!code-cpp[NVC_MFC_RibbonApp#25](../../mfc/reference/codesnippet/cpp/cmfcspinbuttonctrl-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CSpinButtonCtrl](../../mfc/reference/cspinbuttonctrl-class.md)  
  
 [CMFCSpinButtonCtrl](../../mfc/reference/cmfcspinbuttonctrl-class.md)  
  
## <a name="requirements"></a>惠?  
 **标头：** afxspinbuttonctrl.h  
  
##  <a name="ondraw"></a>CMFCSpinButtonCtrl::OnDraw  
 重新绘制当前数值调节钮控件。  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 一个指向设备上下文的指针。  
  
### <a name="remarks"></a>备注  
 框架调用`CMFCSpinButtonCtrl::OnPaint`方法以处理[CWnd::OnPaint](../../mfc/reference/cwnd-class.md#onpaint)消息和方法反过来调用这`CMFCSpinButtonCtrl::OnDraw`方法。 重写此方法以自定义框架绘制数值调节钮控件的方式。  
  
## <a name="see-also"></a>请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCVisualManager 类](../../mfc/reference/cmfcvisualmanager-class.md)
