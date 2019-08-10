---
title: CSplitButton 类
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
ms.openlocfilehash: d493a2d4d1c531250abc1cd60d1d3d5b79dea1b7
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916776"
---
# <a name="csplitbutton-class"></a>CSplitButton 类

`CSplitButton`类表示拆分按钮控件。 当用户单击按钮的主要部分时，拆分按钮控件将执行一个默认行为，而当用户单击按钮的下拉箭头时，控件将显示一个下拉菜单。

## <a name="syntax"></a>语法

```
class CSplitButton : public CButton
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CSplitButton::CSplitButton](#csplitbutton)|构造 `CSplitButton` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CSplitButton::Create](#create)|创建具有指定样式的拆分按钮控件, 并将其附加到`CSplitButton`当前对象。|
|[CSplitButton::SetDropDownMenu](#setdropdownmenu)|设置当用户单击当前拆分按钮控件的下拉箭头时显示的下拉菜单。|

### <a name="protected-methods"></a>受保护的方法

|名称|描述|
|----------|-----------------|
|[CSplitButton::OnDropDown](#ondropdown)|处理用户单击当前拆分按钮控件的下拉箭头时系统发送的 BCN_DROPDOWN 通知。|

## <a name="remarks"></a>备注

此`CSplitButton`类派生自[CButton](../../mfc/reference/cbutton-class.md)类。 拆分按钮控件是其样式为 BS_SPLITBUTTON 的按钮控件。 当用户单击下拉箭头时, 它会显示一个自定义菜单。 有关详细信息, 请参阅[按钮样式](/windows/desktop/Controls/button-styles)中的 BS_SPLITBUTTON 和 BS_DEFSPLITBUTTON 样式。

下图描绘了一个对话框, 其中包含一个页导航控件和一个 (1) 拆分按钮控件。 已单击 (2) 下拉箭头, 并显示了 "(3)" 子菜单。

![具有 splitbutton 和页导航控件的对话框。](../../mfc/reference/media/splitbutton_pager.png "具有 splitbutton 和页导航控件的对话框。")

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

`CSplitButton`

## <a name="requirements"></a>要求

**标头：** afxcmn.h

Windows Vista 和更高版本中支持此类。

有关此类的其他要求, 请参阅[Windows Vista 公共控件的生成要求](../../mfc/build-requirements-for-windows-vista-common-controls.md)。

##  <a name="create"></a>  CSplitButton::Create

创建具有指定样式的拆分按钮控件, 并将其附加到`CSplitButton`当前对象。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*dwStyle*|中要应用于控件的样式的按位组合 (OR)。 有关详细信息, 请参阅[按钮样式](../../mfc/reference/styles-used-by-mfc.md#button-styles)。|
|*rect*|中对包含控件位置和大小的[RECT](/previous-versions/dd162897\(v=vs.85\))结构的引用。|
|*pParentWnd*|中指向[CWnd](../../mfc/reference/cwnd-class.md)对象的非 null 指针, 该对象是控件的父窗口。|
|*nID*|中控件的 ID。|

### <a name="return-value"></a>返回值

如果此方法成功, 则为 TRUE;否则为 FALSE。

##  <a name="csplitbutton"></a>CSplitButton:: CSplitButton

构造 `CSplitButton` 对象。 构造函数的参数指定在用户单击拆分按钮控件的下拉箭头时显示的子菜单。

```
CSplitButton();

CSplitButton(
    UINT nMenuId,
    UINT nSubMenuId)
CSplitButton(CMenu* pMenu)
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*nMenuId*|中菜单栏的资源 ID。|
|*nSubMenuId*|中子菜单的资源 ID。|
|*pMenu*|中指向指定子菜单的[CMenu](../../mfc/reference/cmenu-class.md)对象的指针。 当对象超出范围`CMenu`时`CSplitButton` `CSplitButton` , 对象将删除该对象及其关联的 HMENU。|

### <a name="remarks"></a>备注

使用[CSplitButton:: create](#create)方法可创建拆分按钮控件, 并将其附加到`CSplitButton`对象。

##  <a name="ondropdown"></a>CSplitButton:: OnDropDown

处理用户单击当前拆分按钮控件的下拉箭头时系统发送的 BCN_DROPDOWN 通知。

```
afx_msg void OnDropDown(
    NMHDR* pNMHDR,
    LRESULT* pResult);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*pNMHDR*|中指向[NMHDR](/windows/desktop/api/richedit/ns-richedit-nmhdr)结构的指针, 该结构包含有关[BCN_DROPDOWN](/windows/desktop/Controls/bcn-dropdown)通知的信息。|
|*pResult*|弄(未使用; 不返回任何值。)[BCN_DROPDOWN](/windows/desktop/Controls/bcn-dropdown)通知的返回值。|

### <a name="remarks"></a>备注

当用户单击拆分按钮控件上的下拉箭头时, 系统将发送 BCN_DROPDOWN 通知消息, 该`OnDropDown`消息是方法处理的。 但是, 该`CSplitButton`对象不会将 BCN_DROPDOWN 通知转发到包含拆分按钮控件的控件。 因此, 包含控件无法支持自定义操作来响应通知。

若要实现包含控件支持的自定义操作, 请使用样式为 BS_SPLITBUTTON 的[CButton](../../mfc/reference/cbutton-class.md)对象而不`CSplitButton`是对象。 然后在`CButton`对象中为 BCN_DROPDOWN 通知实现处理程序。 有关详细信息, 请参阅[按钮样式](../../mfc/reference/styles-used-by-mfc.md#button-styles)。

若要实现拆分按钮控件本身支持的自定义操作, 请使用[消息反射](../../mfc/tn062-message-reflection-for-windows-controls.md)。 从类派生你自己的`CSplitButton`类并将其命名为, 例如, CMySplitButton。 然后, 将以下消息映射添加到你的应用程序以处理 BCN_DROPDOWN 通知:

```
BEGIN_MESSAGE_MAP(CMySplitButton,
    CSplitButton)
    ON_NOTIFY_REFLECT(BCN_DROPDOWN, &CMySplitButton::OnDropDown)
END_MESSAGE_MAP()
```

##  <a name="setdropdownmenu"></a>CSplitButton:: SetDropDownMenu

设置当用户单击当前拆分按钮控件的下拉箭头时显示的下拉菜单。

```
void SetDropDownMenu(
    UINT nMenuId,
    UINT nSubMenuId);

void SetDropDownMenu(CMenu* pMenu);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*nMenuId*|中菜单栏的资源 ID。|
|*nSubMenuId*|中子菜单的资源 ID。|
|*pMenu*|中指向指定子菜单的[CMenu](../../mfc/reference/cmenu-class.md)对象的指针。 当对象超出范围`CMenu`时`CSplitButton` `CSplitButton` , 对象将删除该对象及其关联的 HMENU。|

### <a name="remarks"></a>备注

*NMenuId*参数标识菜单栏, 它是菜单栏项的水平列表。 *NSubMenuId*参数是从零开始的索引号, 它标识子菜单, 这是与每个菜单栏项关联的菜单项的下拉列表。 例如, 典型的应用程序有一个菜单, 其中包含菜单栏项 "文件"、"编辑" 和 "帮助"。 "文件" 菜单栏项包含一个子菜单, 其中包含菜单项 "打开"、"关闭" 和 "退出"。 单击拆分按钮控件的下拉箭头时, 控件将显示指定的子菜单, 而不是菜单栏。

下图描绘了一个对话框, 其中包含一个页导航控件和一个 (1) 拆分按钮控件。 已单击 (2) 下拉箭头, 并显示了 "(3)" 子菜单。

![具有 splitbutton 和页导航控件的对话框。](../../mfc/reference/media/splitbutton_pager.png "具有 splitbutton 和页导航控件的对话框。")

### <a name="example"></a>示例

下面的代码示例中的第一个语句演示了[CSplitButton:: SetDropDownMenu](#setdropdownmenu)方法。 我们创建了具有 Visual Studio 资源编辑器的菜单, 该编辑器自动命名为菜单栏 ID IDR_MENU1。 *NSubMenuId*参数为零, 表示菜单栏的唯一子菜单。

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/csplitbutton-class_1.cpp)]

## <a name="see-also"></a>请参阅

[CSplitButton 类](../../mfc/reference/csplitbutton-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CButton 类](../../mfc/reference/cbutton-class.md)
