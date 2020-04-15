---
title: CSnapInPropertyPageImpl 类
ms.date: 11/04/2016
f1_keywords:
- CSnapInPropertyPageImpl
- ATLSNAP/ATL::CSnapInPropertyPageImpl
- ATLSNAP/ATL::CSnapInPropertyPageImpl::CSnapInPropertyPageImpl
- ATLSNAP/ATL::CSnapInPropertyPageImpl::CancelToClose
- ATLSNAP/ATL::CSnapInPropertyPageImpl::Create
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnApply
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnHelp
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnKillActive
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnQueryCancel
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnReset
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnSetActive
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnWizardBack
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnWizardFinish
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnWizardNext
- ATLSNAP/ATL::CSnapInPropertyPageImpl::QuerySiblings
- ATLSNAP/ATL::CSnapInPropertyPageImpl::SetModified
- ATLSNAP/ATL::CSnapInPropertyPageImpl::m_psp
helpviewer_keywords:
- snap-ins, property pages
- snap-ins
- property pages, ATL
- CSnapInPropertyPageImpl class
ms.assetid: 75bdce5a-985e-4166-bd44-493132e023c4
ms.openlocfilehash: ae64c212520510a443fbb2b8adc99243e8f8843a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330703"
---
# <a name="csnapinpropertypageimpl-class"></a>CSnapInPropertyPageImpl 类

此类提供实现管理单元属性页对象的方法。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
CSnapInPropertyPageImpl : public CDialogImplBase
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[快照财产页页：：CSnapin属性页页](#csnapinpropertypageimpl)|构造函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[快照属性页页：：取消关闭](#canceltoclose)|更改 **"确定**"和 **"取消"** 按钮的状态。|
|[CSnapIn属性页页：：创建](#create)|初始化新创建`CSnapInPropertyPageImpl`的对象。|
|[CSnapin属性页页：：打开应用](#onapply)|当用户使用向导类型的属性表单击"**立即应用"** 按钮时，由框架调用。|
|[CSnapin属性页页：：上帮助](#onhelp)|当用户使用向导类型的属性表单击 **"帮助**"按钮时，由框架调用。|
|[快照财产页页：：在基尔基活动](#onkillactive)|当当前页面不再处于活动状态时，由框架调用。|
|[CSnapin属性页页：：打开查询取消](#onquerycancel)|当用户单击 **"取消"** 按钮时和取消发生之前，由框架调用。|
|[快照属性页页：：打开](#onreset)|当用户使用向导类型的属性表单击 **"重置"** 按钮时，由框架调用。|
|[快照财产页页：：打开活动](#onsetactive)|当当前页面处于活动状态时，由框架调用。|
|[CSnapin属性页页：：在向导背面](#onwizardback)|当用户在使用向导类型的属性表时单击 **"后退**"按钮时，由框架调用。|
|[CSnapin属性页页：：在向导完成](#onwizardfinish)|当用户使用向导类型的属性表单击 **"完成"** 按钮时，由框架调用。|
|[CSnapin属性页页：：在向导下一个](#onwizardnext)|当用户使用向导类型的属性表单击 **"下一步**"按钮时，由框架调用。|
|[CSnapIn属性页：：查询兄弟](#querysiblings)|将当前消息转发到属性表的所有页面。|
|[CSnapin属性页页：：设置修改](#setmodified)|调用以激活或停用"**立即应用"** 按钮。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CSnapIn属性页页：：m_psp](#m_psp)|`CSnapInPropertyPageImpl`对象使用的 Windows`PROPSHEETPAGE`结构。|

## <a name="remarks"></a>备注

`CSnapInPropertyPageImpl`为管理单元属性页对象提供了基本实现。 管理单元属性页的基本功能使用多个不同的接口和映射类型实现。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CDialogImplBase`

`CSnapInPropertyPageImpl`

## <a name="requirements"></a>要求

**标题：** atlsnap.h

## <a name="csnapinpropertypageimplcanceltoclose"></a><a name="canceltoclose"></a>快照属性页页：：取消关闭

对模态属性表页面中的数据进行了不可恢复的更改后，请调用此函数。

```
void CancelToClose();
```

### <a name="remarks"></a>备注

此功能将"**确定"** 按钮更改为 **"关闭**"并禁用 **"取消"** 按钮。 此更改提醒用户更改是永久性的，并且无法取消修改。

成员`CancelToClose`函数在无模式属性表中不执行任何操作，因为默认情况下，无模式属性表没有 **"取消"** 按钮。

## <a name="csnapinpropertypageimplcsnapinpropertypageimpl"></a><a name="csnapinpropertypageimpl"></a>快照财产页页：：CSnapin属性页页

构造 `CSnapInPropertyPageImpl` 对象。

```
CSnapInPropertyPageImpl(LPCTSTR lpszTitle = NULL);
```

### <a name="parameters"></a>参数

*lpszTitle*<br/>
[在]属性页的标题。

### <a name="remarks"></a>备注

要初始化基础结构，请致电[CSnapInPropertypageimpl：：创建](#create)。

## <a name="csnapinpropertypageimplcreate"></a><a name="create"></a>CSnapIn属性页页：：创建

调用此函数以初始化属性页的基础结构。

```
HPROPSHEETPAGE Create();
```

### <a name="return-value"></a>返回值

包含新创建属性`PROPSHEETPAGE`表属性的结构的句柄。

### <a name="remarks"></a>备注

在调用此函数之前，应首先调用[CSnapInpropertypageimpl：：CSnapInPropertypageimpl。](#csnapinpropertypageimpl)

## <a name="csnapinpropertypageimplm_psp"></a><a name="m_psp"></a>CSnapIn属性页页：：m_psp

`m_psp`是其成员存储 的 特性的结构`PROPSHEETPAGE`。

```
PROPSHEETPAGE m_psp;
```

### <a name="remarks"></a>备注

使用此结构在构造属性页后初始化属性页的外观。

有关此结构的详细信息（包括其成员的列表），请参阅 Windows SDK 中的[PROPSHEETPAGE。](/windows/win32/api/prsht/ns-prsht-propsheetpagea_v3)

## <a name="csnapinpropertypageimplonapply"></a><a name="onapply"></a>CSnapin属性页页：：打开应用

当用户单击 **"确定"** 或"**立即应用"** 按钮时，将调用此成员函数。

```
BOOL OnApply();
```

### <a name="return-value"></a>返回值

如果接受更改，则非零;否则 0。

### <a name="remarks"></a>备注

在`OnApply`框架可以调用之前，必须调用`SetModified`其参数并将其设置为 TRUE。 当用户在属性页上进行更改时，这将激活"**立即应用"** 按钮。

覆盖此成员函数，以指定当用户单击"**立即应用"** 按钮时程序执行的操作。 重写时，函数应返回 TRUE 以接受更改和 FALSE，以防止更改生效。

默认实现`OnApply`返回 TRUE。

## <a name="csnapinpropertypageimplonhelp"></a><a name="onhelp"></a>CSnapin属性页页：：上帮助

当用户单击属性页的 **"帮助**"按钮时，将调用此成员函数。

```
void OnHelp();
```

### <a name="remarks"></a>备注

覆盖此成员函数以显示属性页的帮助。

## <a name="csnapinpropertypageimplonkillactive"></a><a name="onkillactive"></a>快照财产页页：：在基尔基活动

当页面不再是活动页时，将调用此成员函数。

```
BOOL OnKillActive();
```

### <a name="return-value"></a>返回值

如果数据已成功更新，则非零;否则 0。

### <a name="remarks"></a>备注

重写此成员函数以执行特殊的数据验证任务。

## <a name="csnapinpropertypageimplonquerycancel"></a><a name="onquerycancel"></a>CSnapin属性页页：：打开查询取消

当用户单击 **"取消"** 按钮并在执行取消操作之前调用此成员函数。

```
BOOL OnQueryCancel();
```

### <a name="return-value"></a>返回值

非零以允许取消操作;否则 0。

### <a name="remarks"></a>备注

覆盖此成员函数以指定程序在用户单击 **"取消"** 按钮时执行的操作。

默认实现`OnQueryCancel`返回 TRUE。

## <a name="csnapinpropertypageimplonreset"></a><a name="onreset"></a>快照属性页页：：打开

当用户单击 **"取消"** 按钮时，将调用此成员函数。

```
void OnReset();
```

### <a name="remarks"></a>备注

调用此函数时，将放弃用户以前单击"**立即应用"** 按钮时所做的所有属性页的更改，并且属性表将保留焦点。

覆盖此成员函数以指定当用户单击 **"取消"** 按钮时程序执行的操作。

## <a name="csnapinpropertypageimplonsetactive"></a><a name="onsetactive"></a>快照财产页页：：打开活动

当用户选择该页并成为活动页时，将调用此成员函数。

```
BOOL OnSetActive();
```

### <a name="return-value"></a>返回值

如果页面已成功设置为活动，则非零;否则 0。

### <a name="remarks"></a>备注

覆盖此成员函数，以在激活页面时执行任务。 在完成任何其他处理之前，应调用默认版本。

默认实现返回 TRUE。

## <a name="csnapinpropertypageimplonwizardback"></a><a name="onwizardback"></a>CSnapin属性页页：：在向导背面

当用户单击向导中的 **"后退"** 按钮时，将调用此成员函数。

```
BOOL OnWizardBack();
```

### <a name="return-value"></a>返回值

- 0 自动前进到上一页。

- -1 以防止页面更改。

要跳转到下一个页面以外的页面，返回要显示的对话框的标识符。

### <a name="remarks"></a>备注

重写此成员函数以指定用户单击 **"后退"** 按钮时必须执行的操作。

## <a name="csnapinpropertypageimplonwizardfinish"></a><a name="onwizardfinish"></a>CSnapin属性页页：：在向导完成

当用户单击向导中的 **"完成"** 按钮时，将调用此成员函数。

```
BOOL OnWizardFinish();
```

### <a name="return-value"></a>返回值

如果属性表在向导完成时销毁，则非零;否则为零。

### <a name="remarks"></a>备注

覆盖此成员函数以指定用户在单击 **"完成"** 按钮时必须执行的操作。

## <a name="csnapinpropertypageimplonwizardnext"></a><a name="onwizardnext"></a>CSnapin属性页页：：在向导下一个

当用户单击向导中的 **"下一步**"按钮时，将调用此成员函数。

```
BOOL OnWizardNext();
```

### <a name="return-value"></a>返回值

- 0 自动前进到下一页。

- -1 以防止页面更改。

要跳转到下一个页面以外的页面，返回要显示的对话框的标识符。

### <a name="remarks"></a>备注

重写此成员函数以指定用户在单击"**下一步**"按钮时必须执行的操作。

## <a name="csnapinpropertypageimplquerysiblings"></a><a name="querysiblings"></a>CSnapIn属性页：：查询兄弟

调用此成员函数将消息转发到属性表中的每个页面。

```
LRESULT QuerySiblings(WPARAM wParam, LPARAM lParam);
```

### <a name="parameters"></a>参数

*wParam*<br/>
[在]指定其他与消息相关的信息。

*lParam*<br/>
[在]指定其他与消息相关的信息。

### <a name="return-value"></a>返回值

如果消息不应转发到下一个属性页，则为非零;否则为零。

### <a name="remarks"></a>备注

如果页面返回非零值，则属性表不会将消息发送到后续页面。

## <a name="csnapinpropertypageimplsetmodified"></a><a name="setmodified"></a>CSnapin属性页页：：设置修改

调用此成员函数以启用或禁用 **"立即应用"** 按钮，具体取决于属性页中的设置是否应应用于相应的外部对象。

```
void SetModified(BOOL bChanged = TRUE);
```

### <a name="parameters"></a>参数

*b 已更改*<br/>
[在]TRUE 以指示自上次应用属性页设置以来已修改属性页设置;FALSE 以指示已应用属性页设置，或应忽略。

### <a name="remarks"></a>备注

属性表跟踪哪些页面是"脏"的，即您为其调用`SetModified( TRUE )`的属性页。 如果调用`SetModified( TRUE )`其中一个页面，则始终启用"**立即应用"** 按钮。 当您调用`SetModified( FALSE )`其中一个页面时，将禁用"**立即应用"** 按钮，但前提是其他页面均未"脏"。

## <a name="see-also"></a>另请参阅

[类概述](../../atl/atl-class-overview.md)
