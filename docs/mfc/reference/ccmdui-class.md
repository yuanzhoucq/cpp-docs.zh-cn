---
title: CCmdUI 类
ms.date: 11/04/2016
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
ms.openlocfilehash: c1d44638779f9b5caf052106ac172110d309b69f
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58770884"
---
# <a name="ccmdui-class"></a>CCmdUI 类

仅在`ON_UPDATE_COMMAND_UI`处理程序中的`CCmdTarget`-派生的类。

## <a name="syntax"></a>语法

```
class CCmdUI
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CCmdUI::ContinueRouting](#continuerouting)|告知继续路由处理程序链中向下的当前消息的命令传送机制。|
|[CCmdUI::Enable](#enable)|启用或禁用此命令的用户界面项。|
|[CCmdUI::SetCheck](#setcheck)|设置此命令的用户界面项的复选状态。|
|[CCmdUI::SetRadio](#setradio)|如`SetCheck`成员函数，但对单选组。|
|[CCmdUI::SetText](#settext)|设置此命令的用户界面项的文本。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CCmdUI::m_nID](#m_nid)|用户界面对象的 ID。|
|[CCmdUI::m_nIndex](#m_nindex)|用户界面对象的索引。|
|[CCmdUI::m_pMenu](#m_pmenu)|指向菜单由表示`CCmdUI`对象。|
|[CCmdUI::m_pOther](#m_pother)|指向以发送通知的窗口对象。|
|[CCmdUI::m_pSubMenu](#m_psubmenu)|指向包含子菜单由表示`CCmdUI`对象。|

## <a name="remarks"></a>备注

`CCmdUI` 没有基类。

当应用程序的用户从下一个菜单，每个菜单项需要知道是否应显示为已启用或禁用。 菜单命令的目标来实现的 ON_UPDATE_COMMAND_UI 处理提供此信息。 对于每个应用程序中的命令用户界面对象，使用属性窗口创建每个处理程序的消息映射条目和函数原型。

请求，则菜单上，该框架搜索，并调用每个 ON_UPDATE_COMMAND_UI 处理程序，每个处理程序调用`CCmdUI`之类的成员函数`Enable`和`Check`，framework 然后相应地显示每个菜单项。

菜单项可以替换为与控件条按钮或其他命令用户界面对象而无需更改代码内的`ON_UPDATE_COMMAND_UI`处理程序。

下表总结了影响`CCmdUI`的成员函数具有对各种命令用户界面项。

|用户界面项|启用|SetCheck|SetRadio|SetText|
|--------------------------|------------|--------------|--------------|-------------|
|Menu item|启用或禁用|选中或取消选中|使用一个圆点的检查|设置项文本|
|工具栏按钮|启用或禁用|选中后，请取消选择，或不确定|与 `SetCheck` 相同|（不适用于）|
|状态栏窗格|使文本可见或不可见|设置弹出或正常边框|与 `SetCheck` 相同|设置窗格文本|
|中的普通按钮 `CDialogBar`|启用或禁用|选中或取消选中复选框|与 `SetCheck` 相同|设置按钮文本|
|在正常控制 `CDialogBar`|启用或禁用|（不适用于）|（不适用于）|设置窗口文本|

有关使用此类的详细信息，请参阅[如何更新用户界面对象](../../mfc/how-to-update-user-interface-objects.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CCmdUI`

## <a name="requirements"></a>要求

**标头:** afxwin.h

##  <a name="continuerouting"></a>  CCmdUI::ContinueRouting

调用此成员函数以告知继续路由处理程序链中向下的当前消息的命令传送机制。

```
void ContinueRouting();
```

### <a name="remarks"></a>备注

这是应返回 FALSE 的 ON_COMMAND_EX 处理程序结合使用的高级的成员函数。 有关详细信息，请参阅[技术备注 6](../../mfc/tn006-message-maps.md)。

##  <a name="enable"></a>  CCmdUI::Enable

调用此成员函数可启用或禁用此命令的用户界面项。

```
virtual void Enable(BOOL bOn = TRUE);
```

### <a name="parameters"></a>参数

*bOn*<br/>
为 true 以启用该项目，为 FALSE，则将其禁用。

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

指针 (的`CMenu`类型) 到菜单由表示`CCmdUI`对象。

```
CMenu* m_pMenu;
```

### <a name="remarks"></a>备注

如果此项不是一个菜单，则为 NULL。

##  <a name="m_psubmenu"></a>  CCmdUI::m_pSubMenu

指针 (的`CMenu`类型) 到包含子菜单由表示`CCmdUI`对象。

```
CMenu* m_pSubMenu;
```

### <a name="remarks"></a>备注

如果此项不是一个菜单，则为 NULL。 如果子菜单弹出窗口中， *m_nID*包含弹出菜单中的第一项的 ID。 有关详细信息，请参阅[技术说明 21](../../mfc/tn021-command-and-message-routing.md)。

##  <a name="m_pother"></a>  CCmdUI::m_pOther

指针 (类型的`CWnd`) 到窗口对象，如工具或状态栏中，发送通知。

```
CWnd* m_pOther;
```

### <a name="remarks"></a>备注

如果该项是一个菜单或非 NULL`CWnd`对象。

##  <a name="setcheck"></a>  CCmdUI::SetCheck

调用此成员函数可将此命令的用户界面项设置为相应的复选状态。

```
virtual void SetCheck(int nCheck = 1);
```

### <a name="parameters"></a>参数

*nCheck*<br/>
指定要设置的复选状态。 如果 0，取消选中;如果 1，检查;，如果 2，将设置不确定。

### <a name="remarks"></a>备注

此成员函数适用于菜单项和工具栏按钮。 不确定状态仅适用于工具栏按钮。

##  <a name="setradio"></a>  CCmdUI::SetRadio

调用此成员函数可将此命令的用户界面项设置为相应的复选状态。

```
virtual void SetRadio(BOOL bOn = TRUE);
```

### <a name="parameters"></a>参数

*bOn*<br/>
为 true 以启用项;否则为 FALSE。

### <a name="remarks"></a>备注

此成员函数的运行方式和一样`SetCheck`，只不过它对用户界面项作为单选按钮组的一部分进行操作。 除非是项目本身保持单选按钮组行为，取消选中组中的其他项不自动。

##  <a name="settext"></a>  CCmdUI::SetText

调用此成员函数以设置此命令的用户界面项的文本。

```
virtual void SetText(LPCTSTR lpszText);
```

### <a name="parameters"></a>参数

*lpszText*<br/>
指向一个文本字符串的指针。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#48](../../mfc/codesnippet/cpp/ccmdui-class_3.cpp)]

## <a name="see-also"></a>请参阅

[MFC 示例 MDI](../../overview/visual-cpp-samples.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget 类](../../mfc/reference/ccmdtarget-class.md)
