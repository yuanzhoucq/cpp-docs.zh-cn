---
title: "CMFCTabToolTipInfo 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCTabToolTipInfo
dev_langs:
- C++
helpviewer_keywords:
- CMFCTabToolTipInfo struct
ms.assetid: 9c3b3fb9-1497-4d59-932b-0da9348dd5e2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4cfb12ca9660259a4451d2841a921a566cf54505
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cmfctabtooltipinfo-structure"></a>CMFCTabToolTipInfo 结构
此结构可提供有关用户悬停的 MDI 选项卡的信息。  
  
## <a name="syntax"></a>语法  
  
```  
struct CMFCTabToolTipInfo  
```  
  
## <a name="members"></a>成员  
  
### <a name="data-members"></a>数据成员  
  
|name|描述|  
|----------|-----------------|  
|[CMFCTabToolTipInfo::m_nTabIndex](#m_ntabindex)|指定的选项卡控件的索引。|  
|[CMFCTabToolTipInfo::m_pTabWnd](#m_ptabwnd)|指向选项卡控件的指针。|  
|[CMFCTabToolTipInfo::m_strText](#m_strtext)|工具提示文本中。|  
  
## <a name="remarks"></a>备注  
 指向的指针`CMFCTabToolTipInfo`作为参数传递结构`AFX_WM_ON_GET_TAB_TOOLTIP`消息。 当启用了 MDI 选项卡并将用户悬停在选项卡控件上时，将生成此消息。  
  
## <a name="example"></a>示例  
 下面的示例演示如何`CMFCTabToolTipInfo`中使用[MDITabsDemo 示例： MFC 选项卡式 MDI 应用程序](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CMFCTabToolTipInfo](../../mfc/reference/cmfctabtooltipinfo-structure.md)  
  
## <a name="requirements"></a>惠?  
 **标头：** afxbasetabctrl.h  
  
##  <a name="m_ntabindex"></a>CMFCTabToolTipInfo::m_nTabIndex  
 指定的选项卡控件的索引。  
  
```  
int m_nTabIndex;  
```  
  
### <a name="remarks"></a>备注  
 用户悬停在其上的选项卡索引。  
  
### <a name="example"></a>示例  
 下面的示例演示如何`m_nTabIndex`中使用[MDITabsDemo 示例： MFC 选项卡式 MDI 应用程序](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]  
  
##  <a name="m_ptabwnd"></a>CMFCTabToolTipInfo::m_pTabWnd  
 指向选项卡控件的指针。  
  
```  
CMFCBaseTabCtrl* m_pTabWnd;  
```  
  
### <a name="example"></a>示例  
 下面的示例演示如何`m_pTabWnd`中使用[MDITabsDemo 示例： MFC 选项卡式 MDI 应用程序](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]  
  
##  <a name="m_strtext"></a>CMFCTabToolTipInfo::m_strText  
 工具提示文本中。  
  
```  
CString m_strText;  
```  
  
### <a name="remarks"></a>备注  
 如果字符串为空，不会显示工具提示。  
  
### <a name="example"></a>示例  
 下面的示例演示如何`m_strText`中使用[MDITabsDemo 示例： MFC 选项卡式 MDI 应用程序](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)
