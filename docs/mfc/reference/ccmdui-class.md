---
title: CmDUI 类
ms.date: 09/06/2019
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
ms.openlocfilehash: 3e167d9e305481e05808f5e553222c10abbc88de
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752725"
---
# <a name="ccmdui-class"></a>CmDUI 类

仅在`ON_UPDATE_COMMAND_UI``CCmdTarget`派生类中的处理程序中使用。

## <a name="syntax"></a>语法

```
class CCmdUI
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CCmdUI：：继续路由](#continuerouting)|告诉命令路由机制继续将当前消息路由到处理程序链中。|
|[CmDUI：启用](#enable)|启用或禁用此命令的用户界面项。|
|[CmdUI：：设置检查](#setcheck)|设置此命令的用户界面项的检查状态。|
|[CmdUI：：SetRadio](#setradio)|与成员`SetCheck`函数一样，但在无线电组上运行。|
|[CmdUI：：设置文本](#settext)|设置此命令的用户界面项的文本。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CCmdUI：：m_nID](#m_nid)|用户界面对象的 ID。|
|[CCmdUI：：m_nIndex](#m_nindex)|用户界面对象的索引。|
|[CmDUI：：m_pMenu](#m_pmenu)|指向对象表示的`CCmdUI`菜单。|
|[CmDUI：：m_pOther](#m_pother)|指向发送通知的窗口对象。|
|[CmdUI：：m_pSubMenu](#m_psubmenu)|指向由对象表示的`CCmdUI`包含的子菜单。|

## <a name="remarks"></a>备注

`CCmdUI`没有基类。

当应用程序的用户拉下菜单时，每个菜单项需要知道它是应该显示为已启用还是禁用。 菜单命令的目标通过实现ON_UPDATE_COMMAND_UI处理程序来提供此信息。 对于应用程序中的每个命令用户界面对象，请使用[类向导](mfc-class-wizard.md)或**属性**窗口（**类视图**中）为每个处理程序创建消息映射条目和函数原型。

当菜单拉下时，框架搜索并调用每个ON_UPDATE_COMMAND_UI处理程序，每个处理程序调用`CCmdUI`成员函数，如`Enable`和`Check`，然后框架适当地显示每个菜单项。

菜单项可以替换为控制栏按钮或其他命令用户界面对象，而无需更改处理程序中`ON_UPDATE_COMMAND_UI`的代码。

下表总结了成员函数对各种命令`CCmdUI`用户界面项的影响。

|用户界面项目|启用|设置检查|SetRadio|设置文本|
|--------------------------|------------|--------------|--------------|-------------|
|菜单项|启用或禁用|检查或取消检查|使用点进行检查|设置项目文本|
|工具栏按钮|启用或禁用|选择、取消选择或不确定|与 `SetCheck` 相同|(ぃ続ノ)|
|状态栏窗格|使文本可见或不可见|设置弹出边框或正常边框|与 `SetCheck` 相同|设置窗格文本|
|中法线按钮`CDialogBar`|启用或禁用|选中或取消选中复选框|与 `SetCheck` 相同|设置按钮文本|
|中的正常控制`CDialogBar`|启用或禁用|(ぃ続ノ)|(ぃ続ノ)|设置窗口文本|

有关此类使用的详细信息，请参阅[如何更新用户界面对象](../../mfc/how-to-update-user-interface-objects.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CCmdUI`

## <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="ccmduicontinuerouting"></a><a name="continuerouting"></a>CCmdUI：：继续路由

调用此成员函数告诉命令路由机制继续将当前消息路由到处理程序链中。

```cpp
void ContinueRouting();
```

### <a name="remarks"></a>备注

这是一个高级成员函数，应与返回 FALSE 的ON_COMMAND_EX处理程序结合使用。 有关详细信息，请参阅[技术说明 6](../../mfc/tn006-message-maps.md)。

## <a name="ccmduienable"></a><a name="enable"></a>CmDUI：启用

调用此成员函数以启用或禁用此命令的用户界面项。

```
virtual void Enable(BOOL bOn = TRUE);
```

### <a name="parameters"></a>参数

*邦*<br/>
TRUE 启用该项目，FALSE 将其禁用。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#46](../../mfc/codesnippet/cpp/ccmdui-class_1.cpp)]

[!code-cpp[NVC_MFCDocView#47](../../mfc/codesnippet/cpp/ccmdui-class_2.cpp)]

## <a name="ccmduim_nid"></a><a name="m_nid"></a>CCmdUI：：m_nID

菜单项、工具栏按钮或`CCmdUI`对象表示的其他用户界面对象的 ID。

```
UINT m_nID;
```

## <a name="ccmduim_nindex"></a><a name="m_nindex"></a>CCmdUI：：m_nIndex

菜单项、工具栏按钮或`CCmdUI`对象表示的其他用户界面对象的索引。

```
UINT m_nIndex;
```

## <a name="ccmduim_pmenu"></a><a name="m_pmenu"></a>CmDUI：：m_pMenu

指向对象表示`CMenu`的菜单的`CCmdUI`指针（类型）。

```
CMenu* m_pMenu;
```

### <a name="remarks"></a>备注

如果项目不是菜单，则为 NULL。

## <a name="ccmduim_psubmenu"></a><a name="m_psubmenu"></a>CmdUI：：m_pSubMenu

指向由对象`CMenu`表示的包含子菜单的`CCmdUI`指针（类型）。

```
CMenu* m_pSubMenu;
```

### <a name="remarks"></a>备注

如果项目不是菜单，则为 NULL。 如果子菜单是弹出窗口 *，m_nID*包含弹出式菜单中第一项的 ID。 有关详细信息，请参阅[技术说明 21](../../mfc/tn021-command-and-message-routing.md)。

## <a name="ccmduim_pother"></a><a name="m_pother"></a>CmDUI：：m_pOther

指向窗口对象的指针`CWnd`（类型 ）（如工具或状态栏）发送通知。

```
CWnd* m_pOther;
```

### <a name="remarks"></a>备注

如果项目是菜单或非`CWnd`对象，则 NULL。

## <a name="ccmduisetcheck"></a><a name="setcheck"></a>CmdUI：：设置检查

调用此成员函数以将此命令的用户界面项设置为相应的检查状态。

```
virtual void SetCheck(int nCheck = 1);
```

### <a name="parameters"></a>参数

*n检查*<br/>
指定要设置的检查状态。 如果为 0，则取消选中;如果为 0，则取消选中。如果为 1，则进行检查;如果为 2，则设置不确定。

### <a name="remarks"></a>备注

此成员函数适用于菜单项和工具栏按钮。 不确定状态仅适用于工具栏按钮。

## <a name="ccmduisetradio"></a><a name="setradio"></a>CmdUI：：SetRadio

调用此成员函数以将此命令的用户界面项设置为相应的检查状态。

```
virtual void SetRadio(BOOL bOn = TRUE);
```

### <a name="parameters"></a>参数

*邦*<br/>
TRUE 以启用项目;否则 FALSE。

### <a name="remarks"></a>备注

此成员函数的操作方式`SetCheck`与 类似，只不过它操作作为无线电组的一部分的用户界面项。 除非项本身维护无线电组行为，否则取消选中组中的其他项不是自动的。

## <a name="ccmduisettext"></a><a name="settext"></a>CmdUI：：设置文本

调用此成员函数以设置此命令的用户界面项的文本。

```
virtual void SetText(LPCTSTR lpszText);
```

### <a name="parameters"></a>参数

*lpszText*<br/>
指向文本字符串的指针。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#48](../../mfc/codesnippet/cpp/ccmdui-class_3.cpp)]

## <a name="see-also"></a>另请参阅

[MFC 样品 MDI](../../overview/visual-cpp-samples.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget 类](../../mfc/reference/ccmdtarget-class.md)
