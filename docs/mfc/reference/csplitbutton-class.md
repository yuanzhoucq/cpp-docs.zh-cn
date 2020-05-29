---
title: C拆分按钮类
ms.date: 11/19/2018
f1_keywords:
- CSplitButton
- AFXCMN/CSplitButton
- AFXCMN/CSplitButton::CSplitButton
- AFXCMN/CSplitButton::Create
- AFXCMN/CSplitButton::SetDropDownMenu
- AFXCMN/CSplitButton::OnDropDown
helpviewer_keywords:
- CSplitButton [MFC], CSplitButton
- CSplitButton [MFC], Create
- CSplitButton [MFC], SetDropDownMenu
- CSplitButton [MFC], OnDropDown
ms.assetid: 6844d0a9-6408-4e44-9b5f-57628ed8bad6
ms.openlocfilehash: 38fceed1cc42ca0aac2e6ddaf145db273c95771d
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753127"
---
# <a name="csplitbutton-class"></a>C拆分按钮类

类`CSplitButton`表示拆分按钮控件。 当用户单击按钮的主要部分时，拆分按钮控件将执行一个默认行为，而当用户单击按钮的下拉箭头时，控件将显示一个下拉菜单。

## <a name="syntax"></a>语法

```
class CSplitButton : public CButton
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[C拆分按钮：：C拆分按钮](#csplitbutton)|构造 `CSplitButton` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CSplit按钮：创建](#create)|创建具有指定样式的拆分按钮控件并将其附加到当前`CSplitButton`对象。|
|[CSplit按钮：：设置下拉菜单](#setdropdownmenu)|设置用户单击当前拆分按钮控件的下拉箭头时显示的下拉菜单。|

### <a name="protected-methods"></a>受保护的方法

|名称|说明|
|----------|-----------------|
|[CSplit按钮："下拉"](#ondropdown)|处理当用户单击当前拆分按钮控件的下拉箭头时系统发送BCN_DROPDOWN通知。|

## <a name="remarks"></a>备注

类`CSplitButton`派生自[CButton](../../mfc/reference/cbutton-class.md)类。 拆分按钮控件是一个按钮控件，其样式为BS_SPLITBUTTON。 当用户单击下拉箭头时，它会显示自定义菜单。 有关详细信息，请参阅[按钮样式](/windows/win32/Controls/button-styles)中的BS_SPLITBUTTON和BS_DEFSPLITBUTTON样式。

下图描绘了一个对话框，其中包含寻呼机控件和 （1） 拆分按钮控件。 已单击 （2） 下拉箭头，并显示 （3） 子菜单。

![具有拆分按钮和页导航控件的对话框。](../../mfc/reference/media/splitbutton_pager.png "具有拆分按钮和页导航控件的对话框。")

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

`CSplitButton`

## <a name="requirements"></a>要求

**标头：** afxcmn.h

此类在 Windows Vista 和更高版本中受支持。

此类的其他要求在 Windows [Vista 通用控件的生成要求中](../../mfc/build-requirements-for-windows-vista-common-controls.md)介绍。

## <a name="csplitbuttoncreate"></a><a name="create"></a>CSplit按钮：创建

创建具有指定样式的拆分按钮控件并将其附加到当前`CSplitButton`对象。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*dwStyle*|[在]要应用于控件的样式的位组合 （OR）。 有关详细信息，请参阅[按钮样式](../../mfc/reference/styles-used-by-mfc.md#button-styles)。|
|*矩形*|[在]对包含控件位置和大小的[RECT](/windows/win32/api/windef/ns-windef-rect)结构的引用。|
|*pparentwnd*|[在]指向作为控件的父窗口的[CWnd](../../mfc/reference/cwnd-class.md)对象的非空指针。|
|*nID*|[在]控件的 ID。|

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE;否则，FALSE。

## <a name="csplitbuttoncsplitbutton"></a><a name="csplitbutton"></a>C拆分按钮：：C拆分按钮

构造 `CSplitButton` 对象。 构造函数的参数指定一个子菜单，当用户单击拆分按钮控件的下拉箭头时显示该子菜单。

```
CSplitButton();

CSplitButton(
    UINT nMenuId,
    UINT nSubMenuId)
CSplitButton(CMenu* pMenu)
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*恩梅努伊*|[在]菜单栏的资源 ID。|
|*nSubMenuId*|[在]子菜单的资源 ID。|
|*pMenu*|[在]指向指定子菜单的[CMenu](../../mfc/reference/cmenu-class.md)对象的指针。 当`CSplitButton`对象超出范围时`CMenu``CSplitButton`，对象将删除该对象及其关联的 HMENU。|

### <a name="remarks"></a>备注

使用[CSplitButton：：创建](#create)方法创建拆分按钮控件并将其附加到`CSplitButton`对象。

## <a name="csplitbuttonondropdown"></a><a name="ondropdown"></a>CSplit按钮："下拉"

处理当用户单击当前拆分按钮控件的下拉箭头时系统发送BCN_DROPDOWN通知。

```
afx_msg void OnDropDown(
    NMHDR* pNMHDR,
    LRESULT* pResult);
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*pNMHDR*|[在]指向包含[BCN_DROPDOWN](/windows/win32/Controls/bcn-dropdown)通知信息的[NMHDR](/windows/win32/api/richedit/ns-richedit-nmhdr)结构的指针。|
|*pResult*|[出]（未使用;不返回任何值。[BCN_DROPDOWN](/windows/win32/Controls/bcn-dropdown)通知的返回值。|

### <a name="remarks"></a>备注

当用户单击拆分按钮控件上的下拉箭头时，系统会发送BCN_DROPDOWN通知消息，`OnDropDown`该方法将处理该消息。 但是，`CSplitButton`对象不会将BCN_DROPDOWN通知转发到包含拆分按钮控件的控件。 因此，包含控件不支持响应通知的自定义操作。

要实现包含控件支持的自定义操作，请使用具有BS_SPLITBUTTON样式的[CButton](../../mfc/reference/cbutton-class.md)对象，而不是对象`CSplitButton`。 然后在对象中实现BCN_DROPDOWN通知的`CButton`处理程序。 有关详细信息，请参阅[按钮样式](../../mfc/reference/styles-used-by-mfc.md#button-styles)。

要实现拆分按钮控件本身支持的自定义操作，请使用[消息反射](../../mfc/tn062-message-reflection-for-windows-controls.md)。 从`CSplitButton`类派生您自己的类并将其命名，例如，CMySplitButton。 然后向应用程序添加以下消息映射以处理BCN_DROPDOWN通知：

```
BEGIN_MESSAGE_MAP(CMySplitButton,
    CSplitButton)
    ON_NOTIFY_REFLECT(BCN_DROPDOWN, &CMySplitButton::OnDropDown)
END_MESSAGE_MAP()
```

## <a name="csplitbuttonsetdropdownmenu"></a><a name="setdropdownmenu"></a>CSplit按钮：：设置下拉菜单

设置用户单击当前拆分按钮控件的下拉箭头时显示的下拉菜单。

```cpp
void SetDropDownMenu(
    UINT nMenuId,
    UINT nSubMenuId);

void SetDropDownMenu(CMenu* pMenu);
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*恩梅努伊*|[在]菜单栏的资源 ID。|
|*nSubMenuId*|[在]子菜单的资源 ID。|
|*pMenu*|[在]指向指定子菜单的[CMenu](../../mfc/reference/cmenu-class.md)对象的指针。 当`CSplitButton`对象超出范围时`CMenu``CSplitButton`，对象将删除该对象及其关联的 HMENU。|

### <a name="remarks"></a>备注

*nMenuId*参数标识菜单栏，菜单栏是菜单栏项的水平列表。 *nSubMenuId*参数是一个基于零的索引编号，用于标识子菜单，即与每个菜单栏项关联的菜单项的下拉列表。 例如，典型的应用程序具有包含菜单栏项的菜单，"文件"、"编辑"和"帮助"。 "文件"菜单栏项有一个子菜单，其中包含菜单项"打开"、"关闭"和"退出"。 单击拆分按钮控件的下拉箭头时，该控件将显示指定的子菜单，而不是菜单栏。

下图描绘了一个对话框，其中包含寻呼机控件和 （1） 拆分按钮控件。 已单击 （2） 下拉箭头，并显示 （3） 子菜单。

![具有拆分按钮和页导航控件的对话框。](../../mfc/reference/media/splitbutton_pager.png "具有拆分按钮和页导航控件的对话框。")

### <a name="example"></a>示例

以下代码示例中的第一个语句演示了[CSplitButton：：SetDropDownMenu](#setdropdownmenu)方法。 我们使用 Visual Studio 资源编辑器创建了菜单，该编辑器自动命名为菜单栏 ID，IDR_MENU1。 *nSubMenuId*参数为零，表示菜单栏的唯一子菜单。

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/csplitbutton-class_1.cpp)]

## <a name="see-also"></a>请参阅

[C拆分按钮类](../../mfc/reference/csplitbutton-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[C按钮类](../../mfc/reference/cbutton-class.md)
