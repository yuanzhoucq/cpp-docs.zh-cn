---
title: CMFCDisableMenuAnimation 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCDisableMenuAnimation
- AFXPOPUPMENU/CMFCDisableMenuAnimation
- AFXPOPUPMENU/CMFCDisableMenuAnimation::Restore
dev_langs:
- C++
helpviewer_keywords:
- CMFCDisableMenuAnimation [MFC], Restore
ms.assetid: c6eb07da-c382-43d6-8028-007f2320e50e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3a7a2449fe65a0b17bf770ea2bfb8f3fe750cba0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="cmfcdisablemenuanimation-class"></a>CMFCDisableMenuAnimation 类
禁用弹出菜单的动画。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCDisableMenuAnimation  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|||  
|-|-|  
|名称|描述|  
|`CMFCDisableMenuAnimation::CMFCDisableMenuAnimation`|构造 `CMFCDisableMenuAnimation` 对象。|  
|`CMFCDisableMenuAnimation::~CMFCDisableMenuAnimation`|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|||  
|-|-|  
|名称|描述|  
|[CMFCDisableMenuAnimation::Restore](#restore)|还原以前的框架用于显示一个弹出菜单的动画。|  
  
### <a name="data-members"></a>数据成员  
  
|||  
|-|-|  
|名称|描述|  
|`CMFCDisableMenuAnimation::m_animType`|存储的以前的弹出菜单动画类型。|  
  
### <a name="remarks"></a>备注  
 使用此帮助器类来临时禁用弹出菜单动画 （例如，当处理鼠标或键盘命令）。  
  
 A`CMFCDisableMenuAnimation`对象禁用弹出菜单动画在其生存期期间。 构造函数将存储在当前的弹出菜单动画类型`m_animType`字段并将当前的动画类型到设置`CMFCPopupMenu::NO_ANIMATION`。 析构函数还原以前的动画类型。  
  
 你可以创建`CMFCDisableMenuAnimation`禁用整个单个函数的弹出菜单动画堆栈上的对象。 如果你想要禁用函数之间的弹出菜单动画，创建`CMFCDisableMenuAnimation`堆上对象，然后删除它，如果你想要还原弹出菜单动画。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用堆栈来临时禁用菜单动画。  
  
 [!code-cpp[NVC_MFC_Misc#1](../../mfc/reference/codesnippet/cpp/cmfcdisablemenuanimation-class_1.h)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CMFCDisableMenuAnimation](../../mfc/reference/cmfcdisablemenuanimation-class.md)  
  
## <a name="requirements"></a>要求  
 **标头：** afxpopupmenu.h  
  
##  <a name="restore"></a>  CMFCDisableMenuAnimation::Restore  
 还原以前的框架用于显示一个弹出菜单的动画。  
  
```  
void Restore ();
```  
  
### <a name="remarks"></a>备注  
 调用此方法`CMFCDisableMenuAnimation`析构函数以还原以前的框架用于显示一个弹出菜单的动画。  
  
## <a name="see-also"></a>请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCPopupMenu 类](../../mfc/reference/cmfcpopupmenu-class.md)
