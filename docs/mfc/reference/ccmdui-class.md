---
title: CCmdUI 类
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
ms.openlocfilehash: 42aec2937cd81ebbb50482321b8deae001723d3a
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79424565"
---
# <a name="ccmdui-class"></a>CCmdUI 类

仅在 `CCmdTarget`派生类中的 `ON_UPDATE_COMMAND_UI` 处理程序中使用。

## <a name="syntax"></a>语法

```
class CCmdUI
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CCmdUI：： ContinueRouting](#continuerouting)|告诉命令路由机制继续向下传递处理程序链中的当前消息。|
|[CCmdUI：： Enable](#enable)|启用或禁用此命令的用户界面项。|
|[CCmdUI：： SetCheck](#setcheck)|为此命令设置用户界面项的复选状态。|
|[CCmdUI：： SetRadio](#setradio)|与 `SetCheck` 成员函数类似，但操作的是单选组。|
|[CCmdUI：： SetText](#settext)|为此命令设置用户界面项的文本。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CCmdUI：： m_nID](#m_nid)|用户界面对象的 ID。|
|[CCmdUI：： m_nIndex](#m_nindex)|用户界面对象的索引。|
|[CCmdUI：： m_pMenu](#m_pmenu)|指向 `CCmdUI` 对象表示的菜单。|
|[CCmdUI：： m_pOther](#m_pother)|指向发送通知的窗口对象。|
|[CCmdUI：： m_pSubMenu](#m_psubmenu)|指向由 `CCmdUI` 对象表示的包含的子菜单。|

## <a name="remarks"></a>备注

`CCmdUI` 没有基类。

当应用程序的用户下拉菜单时，每个菜单项都需要知道它是显示为已启用还是已禁用。 菜单命令的目标通过实现 ON_UPDATE_COMMAND_UI 处理程序来提供此信息。 对于应用程序中的每个命令用户界面对象，使用[类向导](mfc-class-wizard.md)或 "**属性**" 窗口（在**类视图**中）为每个处理程序创建消息映射项和函数原型。

当下拉菜单向下移动时，框架会搜索每个 ON_UPDATE_COMMAND_UI 处理程序，并调用每个处理程序 `CCmdUI` 成员函数（如 `Enable` 和 `Check`），然后，框架会相应地显示每个菜单项。

菜单项可以替换为控件条按钮或其他命令用户界面对象，而无需更改 `ON_UPDATE_COMMAND_UI` 处理程序中的代码。

下表总结了 `CCmdUI`的成员函数对各种命令用户界面项的影响。

|用户界面项|启用|SetCheck|SetRadio|SetText|
|--------------------------|------------|--------------|--------------|-------------|
|菜单项|启用或禁用|选中或取消选中|使用点进行检查|设置项文本|
|工具栏按钮|启用或禁用|选择、取消选择或不确定|与 `SetCheck` 相同|(ぃ続ノ)|
|状态栏窗格|使文本可见或不可见|设置弹出框或普通边框|与 `SetCheck` 相同|设置窗格文本|
|`CDialogBar` 中的 "普通" 按钮|启用或禁用|选中或取消选中复选框|与 `SetCheck` 相同|设置按钮文本|
|`CDialogBar` 中的常规控件|启用或禁用|(ぃ続ノ)|(ぃ続ノ)|设置窗口文本|

有关使用此类的详细信息，请参阅[如何更新用户界面对象](../../mfc/how-to-update-user-interface-objects.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CCmdUI`

## <a name="requirements"></a>要求

**标头:** afxwin.h

##  <a name="continuerouting"></a>CCmdUI：： ContinueRouting

调用此成员函数，告诉命令路由机制继续向下传递处理程序链中的当前消息。

```
void ContinueRouting();
```

### <a name="remarks"></a>备注

这是一个高级成员函数，应与返回 FALSE 的 ON_COMMAND_EX 处理程序结合使用。 有关详细信息，请参阅[技术说明 6](../../mfc/tn006-message-maps.md)。

##  <a name="enable"></a>CCmdUI：： Enable

调用此成员函数可以启用或禁用此命令的用户界面项。

```
virtual void Enable(BOOL bOn = TRUE);
```

### <a name="parameters"></a>parameters

*bOn*<br/>
若要启用该项，则为 TRUE; 否则为 FALSE。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#46](../../mfc/codesnippet/cpp/ccmdui-class_1.cpp)]

[!code-cpp[NVC_MFCDocView#47](../../mfc/codesnippet/cpp/ccmdui-class_2.cpp)]

##  <a name="m_nid"></a>CCmdUI：： m_nID

`CCmdUI` 对象表示的菜单项、工具栏按钮或其他用户界面对象的 ID。

```
UINT m_nID;
```

##  <a name="m_nindex"></a>CCmdUI：： m_nIndex

`CCmdUI` 对象表示的菜单项、工具栏按钮或其他用户界面对象的索引。

```
UINT m_nIndex;
```

##  <a name="m_pmenu"></a>CCmdUI：： m_pMenu

由 `CCmdUI` 对象表示的菜单的指针（`CMenu` 类型）。

```
CMenu* m_pMenu;
```

### <a name="remarks"></a>备注

如果项不是菜单，则为 NULL。

##  <a name="m_psubmenu"></a>CCmdUI：： m_pSubMenu

指向由 `CCmdUI` 对象表示的所包含子菜单的指针（`CMenu` 类型）。

```
CMenu* m_pSubMenu;
```

### <a name="remarks"></a>备注

如果项不是菜单，则为 NULL。 如果子菜单是一个弹出窗口， *m_nID*将包含弹出菜单中第一项的 ID。 有关详细信息，请参阅[技术说明 21](../../mfc/tn021-command-and-message-routing.md)。

##  <a name="m_pother"></a>CCmdUI：： m_pOther

发送通知的窗口对象（例如工具或状态栏）的指针（类型为 `CWnd`）。

```
CWnd* m_pOther;
```

### <a name="remarks"></a>备注

如果该项是菜单或非 `CWnd` 的对象，则为 NULL。

##  <a name="setcheck"></a>CCmdUI：： SetCheck

调用此成员函数可将此命令的用户界面项设置为相应的复选状态。

```
virtual void SetCheck(int nCheck = 1);
```

### <a name="parameters"></a>parameters

*n*<br/>
指定要设置的检查状态。 如果为0，则取消选中;如果为1，则检查;如果为2，则设置不确定。

### <a name="remarks"></a>备注

此成员函数适用于菜单项和工具栏按钮。 不确定状态仅适用于工具栏按钮。

##  <a name="setradio"></a>CCmdUI：： SetRadio

调用此成员函数可将此命令的用户界面项设置为相应的复选状态。

```
virtual void SetRadio(BOOL bOn = TRUE);
```

### <a name="parameters"></a>parameters

*bOn*<br/>
若要启用该项，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

此成员函数的操作方式与 `SetCheck`相同，只不过它对作为单选组一部分的用户界面项进行操作。 取消选中组中的其他项不是自动的，除非这些项本身会保留单选按钮行为。

##  <a name="settext"></a>CCmdUI：： SetText

调用此成员函数可设置此命令的用户界面项的文本。

```
virtual void SetText(LPCTSTR lpszText);
```

### <a name="parameters"></a>parameters

*lpszText*<br/>
指向文本字符串的指针。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#48](../../mfc/codesnippet/cpp/ccmdui-class_3.cpp)]

## <a name="see-also"></a>另请参阅

[MFC 示例 MDI](../../overview/visual-cpp-samples.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget 类](../../mfc/reference/ccmdtarget-class.md)
