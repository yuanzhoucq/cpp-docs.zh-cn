---
title: "工具栏控件样式 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- ToolBar control styles
ms.assetid: 0f717eb9-fa32-4263-b852-809238863feb
caps.latest.revision: 16
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
ms.openlocfilehash: 1c50009a50c5b80e007add9de679315df6aecea9
ms.lasthandoff: 02/24/2017

---
# <a name="toolbar-control-styles"></a>工具栏控件样式
[CMFCToolBarButton 类](../../mfc/reference/cmfctoolbarbutton-class.md)都有一组样式标志，用于确定外观和行为按钮。 可以通过调用设置这些标志的组合[CMFCToolBarButton::SetStyle](../../mfc/reference/cmfctoolbarbutton-class.md#setstyle)。 本主题列出了样式标志值及其含义。  
  
## <a name="property-values"></a>属性值  
 下列值确定控件表示的按钮的类型：  
  
 TBBS_BUTTON  
 标准按键（默认）。  
  
 TBBS_CHECKBOX  
 复选框  
  
 TBBS_CHECKGROUP  
 复选框组的开始。  
  
 TBBS_GROUP  
 按钮组的开始。  
  
 TBBS_SEPARATOR  
 分隔符。  
  
 下列值表示控件的当前状态：  
  
 TBBS_CHECKED  
 复选框处于选中状态。  
  
 TBBS_DISABLED  
 控件已禁用。  
  
 TBBS_INDETERMINATE  
 复选框处于不确定状态。  
  
 TBBS_PRESSED  
 按钮处于按下状态。  
  
 下列值将更改按钮在工具栏中的布局：  
  
 TBBS_BREAK  
 将项放置在新行或新列上，无需分隔列。  
  
## <a name="remarks"></a>备注  
 当前样式存储在[CMFCToolBarButton::m_nStyle](../../mfc/reference/cmfctoolbarbutton-class.md#m_nstyle)。 未设置的新值`m_nStyle`直接，因为一些派生的类执行其他处理，当您调用`SetStyles`。  
  
 视觉管理器将确定按钮在每种状态下的外观。 请参阅[可视化管理器](../../mfc/visualization-manager.md)有关详细信息。  
  
## <a name="requirements"></a>要求  
 **标头︰** afxtoolbarbutton.h  
  
## <a name="see-also"></a>另请参阅  
 [宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)   
 [CMFCToolBarButton 类](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [可视化管理器](../../mfc/visualization-manager.md)



