---
title: CCmdUI 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CCmdUI
- AFXWIN/CCmdUI
- AFXWIN/CCmdUI::ContinueRouting
- AFXWIN/CCmdUI::Enable
- AFXWIN/CCmdUI::SetCheck
- AFXWIN/CCmdUI::SetRadio
- AFXWIN/CCmdUI::SetText
- AFXWIN/CCmdUI::m_nID
- AFXWIN/CCmdUI::m_nIndex
- AFXWIN/CCmdUI::m_pMenu
- AFXWIN/CCmdUI::m_pOther
- AFXWIN/CCmdUI::m_pSubMenu
dev_langs:
- C++
helpviewer_keywords:
- CCmdUI [MFC], ContinueRouting
- CCmdUI [MFC], Enable
- CCmdUI [MFC], SetCheck
- CCmdUI [MFC], SetRadio
- CCmdUI [MFC], SetText
- CCmdUI [MFC], m_nID
- CCmdUI [MFC], m_nIndex
- CCmdUI [MFC], m_pMenu
- CCmdUI [MFC], m_pOther
- CCmdUI [MFC], m_pSubMenu
ms.assetid: 04eaaaf5-f510-48ab-b425-94665ba24766
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3dd417872ab4009a9e0f6c06fc0958f5780de477
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2018
ms.locfileid: "36954147"
---
# <a name="ccmdui-class"></a>CCmdUI 类
只能在使用`ON_UPDATE_COMMAND_UI`中的处理程序`CCmdTarget`-派生类。  
  
## <a name="syntax"></a>语法  
  
```  
class CCmdUI  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CCmdUI::ContinueRouting](#continuerouting)|告知继续路由当前消息的处理程序项链的命令传送机制。|  
|[CCmdUI::Enable](#enable)|启用或禁用此命令的用户界面项。|  
|[CCmdUI::SetCheck](#setcheck)|设置此命令的用户界面项的复选状态。|  
|[CCmdUI::SetRadio](#setradio)|如`SetCheck`成员函数，但对单选组操作。|  
|[CCmdUI::SetText](#settext)|设置此命令的用户界面项的文本。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CCmdUI::m_nID](#m_nid)|用户界面对象的 ID。|  
|[CCmdUI::m_nIndex](#m_nindex)|用户界面对象的索引。|  
|[CCmdUI::m_pMenu](#m_pmenu)|指向所代表的菜单`CCmdUI`对象。|  
|[CCmdUI::m_pOther](#m_pother)|指向以发送通知的窗口对象。|  
|[CCmdUI::m_pSubMenu](#m_psubmenu)|指向由包含子菜单`CCmdUI`对象。|  
  
## <a name="remarks"></a>备注  
 `CCmdUI` 没有基类。  
  
 当你的应用程序的用户会菜单、 每个菜单项需要知道是否它应显示为已启用或禁用拉取。 菜单命令的目标提供此信息通过实现`ON_UPDATE_COMMAND_UI`处理程序。 对于每个应用程序中的命令用户界面对象，使用属性窗口创建每个处理程序的消息映射条目和函数原型。  
  
 框架在请求，则它菜单，搜索并调用每个`ON_UPDATE_COMMAND_UI`处理程序中，每个处理程序调用`CCmdUI`成员函数如`Enable`和`Check`，框架然后相应地显示每个菜单项。  
  
 菜单项可以将其替换控件条按钮或其他命令的用户界面对象而无需更改的代码内`ON_UPDATE_COMMAND_UI`处理程序。  
  
 下表总结了影响`CCmdUI`的成员函数具有对各种命令用户界面项。  
  
|用户界面项|启用|SetCheck|SetRadio|SetText|  
|--------------------------|------------|--------------|--------------|-------------|  
|Menu item|启用或禁用|选中或取消选中|检查使用的一个点|设置项的文本|  
|工具栏按钮|启用或禁用|选中后，请取消选择，或不确定|与 `SetCheck` 相同|（不适用）|  
|状态栏窗格|使文字可见或不可见|集弹出或正常边框|与 `SetCheck` 相同|设置窗格中的文本|  
|中的普通按钮 `CDialogBar`|启用或禁用|选中或取消选中复选框|与 `SetCheck` 相同|设置按钮文本|  
|在正常控制 `CDialogBar`|启用或禁用|（不适用）|（不适用）|设置窗口文本|  
  
 有关使用此类的详细信息，请参阅[如何更新用户界面对象](../../mfc/how-to-update-user-interface-objects.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `CCmdUI`  
  
## <a name="requirements"></a>要求  
 **标头:** afxwin.h  
  
##  <a name="continuerouting"></a>  CCmdUI::ContinueRouting  
 调用此成员函数以告知继续路由当前消息的处理程序项链的命令传送机制。  
  
```  
void ContinueRouting();
```  
  
### <a name="remarks"></a>备注  
 这是一个高级的成员函数，应与结合使用`ON_COMMAND_EX`处理程序返回**FALSE**。 有关详细信息，请参阅[技术注意 6](../../mfc/tn006-message-maps.md)。  
  
##  <a name="enable"></a>  CCmdUI::Enable  
 调用此成员函数以启用或禁用此命令的用户界面项。  
  
```  
virtual void Enable(BOOL bOn = TRUE);
```  
  
### <a name="parameters"></a>参数  
 *bOn*  
 **TRUE**以启用项， **FALSE**以禁用它。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#46](../../mfc/codesnippet/cpp/ccmdui-class_1.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#47](../../mfc/codesnippet/cpp/ccmdui-class_2.cpp)]  
  
##  <a name="m_nid"></a>  CCmdUI::m_nID  
 菜单项、 工具栏按钮或由其他用户界面对象的 ID`CCmdUI`对象。  
  
```  
UINT m_nID;  
```  
  
##  <a name="m_nindex"></a>  CCmdUI::m_nIndex  
 菜单项、 工具栏按钮或由其他用户界面对象的索引`CCmdUI`对象。  
  
```  
UINT m_nIndex;  
```  
  
##  <a name="m_pmenu"></a>  CCmdUI::m_pMenu  
 指针 (的`CMenu`类型) 所表示的菜单`CCmdUI`对象。  
  
```  
CMenu* m_pMenu;  
```  
  
### <a name="remarks"></a>备注  
 **NULL**如果该项不是一个菜单。  
  
##  <a name="m_psubmenu"></a>  CCmdUI::m_pSubMenu  
 指针 (的`CMenu`类型) 所表示的包含子菜单`CCmdUI`对象。  
  
```  
CMenu* m_pSubMenu;  
```  
  
### <a name="remarks"></a>备注  
 **NULL**如果该项不是一个菜单。 如果子菜单是一个弹出窗口， *m_nID*包含弹出菜单中的第一项的 ID。 有关详细信息，请参阅[技术说明 21](../../mfc/tn021-command-and-message-routing.md)。  
  
##  <a name="m_pother"></a>  CCmdUI::m_pOther  
 指针 (类型的`CWnd`) 到窗口对象，如工具或状态栏中，发送通知。  
  
```  
CWnd* m_pOther;  
```  
  
### <a name="remarks"></a>备注  
 **NULL**项是否菜单或非`CWnd`对象。  
  
##  <a name="setcheck"></a>  CCmdUI::SetCheck  
 调用此成员函数可将此命令的用户界面项设置为相应的复选状态。  
  
```  
virtual void SetCheck(int nCheck = 1);
```  
  
### <a name="parameters"></a>参数  
 *n 检查*  
 指定要设置的复选状态。 如果 0，取消选中;如果 1，检查;，如果月 2 日，将设置不确定。  
  
### <a name="remarks"></a>备注  
 此成员函数适用于菜单项和工具栏按钮。 确定状态仅适用于工具栏按钮。  
  
##  <a name="setradio"></a>  CCmdUI::SetRadio  
 调用此成员函数可将此命令的用户界面项设置为相应的复选状态。  
  
```  
virtual void SetRadio(BOOL bOn = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `bOn`  
 **TRUE**以启用项; 否则为**FALSE**。  
  
### <a name="remarks"></a>备注  
 此成员函数执行操作如`SetCheck`，只不过它充当单选按钮组的一部分的用户界面项上的操作。 取消选中组中的其他项不是自动除非项目本身维护单选按钮组的行为。  
  
##  <a name="settext"></a>  CCmdUI::SetText  
 调用此成员函数以设置此命令的用户界面项的文本。  
  
```  
virtual void SetText(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>参数  
 *lpszText*  
 指向一个文本字符串的指针。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#48](../../mfc/codesnippet/cpp/ccmdui-class_3.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [MFC 示例 MDI](../../visual-cpp-samples.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CCmdTarget 类](../../mfc/reference/ccmdtarget-class.md)
