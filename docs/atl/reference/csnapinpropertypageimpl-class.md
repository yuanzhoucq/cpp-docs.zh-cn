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
ms.openlocfilehash: abf4cf5804f6ef7335192feb298f1a4a06f841e4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496400"
---
# <a name="csnapinpropertypageimpl-class"></a>CSnapInPropertyPageImpl 类

此类提供用于实现管理单元属性页对象的方法。

> [!IMPORTANT]
>  此类及其成员不能用于在 Windows 运行时中执行的应用程序。

## <a name="syntax"></a>语法

```
CSnapInPropertyPageImpl : public CDialogImplBase
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CSnapInPropertyPageImpl::CSnapInPropertyPageImpl](#csnapinpropertypageimpl)|构造函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CSnapInPropertyPageImpl::CancelToClose](#canceltoclose)|更改 **"确定" 和 "** **取消**" 按钮的状态。|
|[CSnapInPropertyPageImpl::Create](#create)|初始化新创建`CSnapInPropertyPageImpl`的对象。|
|[CSnapInPropertyPageImpl::OnApply](#onapply)|当用户在使用向导类型的属性表时单击 "**立即应用**" 按钮时, 由框架调用。|
|[CSnapInPropertyPageImpl::OnHelp](#onhelp)|当用户在使用向导类型的属性表时单击 "**帮助**" 按钮时, 由框架调用。|
|[CSnapInPropertyPageImpl::OnKillActive](#onkillactive)|当当前页不再处于活动状态时由框架调用。|
|[CSnapInPropertyPageImpl::OnQueryCancel](#onquerycancel)|当用户单击 "**取消**" 按钮, 并在取消之前发生之前, 由框架调用。|
|[CSnapInPropertyPageImpl::OnReset](#onreset)|当用户在使用向导类型的属性表时单击 "**重置**" 按钮时, 由框架调用。|
|[CSnapInPropertyPageImpl::OnSetActive](#onsetactive)|当当前页处于活动状态时由框架调用。|
|[CSnapInPropertyPageImpl::OnWizardBack](#onwizardback)|当用户在使用向导类型的属性表时单击 "**后退**" 按钮时, 由框架调用。|
|[CSnapInPropertyPageImpl::OnWizardFinish](#onwizardfinish)|当用户在使用向导类型的属性表时单击 "**完成**" 按钮时, 由框架调用。|
|[CSnapInPropertyPageImpl::OnWizardNext](#onwizardnext)|当用户在使用向导类型的属性表时单击 "**下一步**" 按钮时, 由框架调用。|
|[CSnapInPropertyPageImpl::QuerySiblings](#querysiblings)|将当前消息转发到属性表的所有页。|
|[CSnapInPropertyPageImpl::SetModified](#setmodified)|调用以激活或停用 "**立即应用**" 按钮。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CSnapInPropertyPageImpl::m_psp](#m_psp)|对象`CSnapInPropertyPageImpl`使用`PROPSHEETPAGE`的 Windows 结构。|

## <a name="remarks"></a>备注

`CSnapInPropertyPageImpl`提供管理单元属性页对象的基本实现。 管理单元属性页的基本功能是使用多种不同的接口和映射类型实现的。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CDialogImplBase`

`CSnapInPropertyPageImpl`

## <a name="requirements"></a>要求

**标头:** atlsnap

##  <a name="canceltoclose"></a>CSnapInPropertyPageImpl::CancelToClose

对模式属性表的页中的数据进行了无法恢复的更改后, 调用此函数。

```
void CancelToClose();
```

### <a name="remarks"></a>备注

此函数将更改 **"确定"** 按钮以**关闭**并禁用 "**取消**" 按钮。 此更改提醒用户, 更改是永久性的, 无法取消修改。

此`CancelToClose`成员函数在无模式属性表中不执行任何操作, 因为无模式属性表默认情况下没有 "**取消**" 按钮。

##  <a name="csnapinpropertypageimpl"></a>CSnapInPropertyPageImpl::CSnapInPropertyPageImpl

构造 `CSnapInPropertyPageImpl` 对象。

```
CSnapInPropertyPageImpl(LPCTSTR lpszTitle = NULL);
```

### <a name="parameters"></a>参数

*lpszTitle*<br/>
中属性页的标题。

### <a name="remarks"></a>备注

若要初始化基础结构, 请调用[CSnapInPropertyPageImpl:: Create](#create)。

##  <a name="create"></a>CSnapInPropertyPageImpl:: Create

调用此函数可初始化属性页的基础结构。

```
HPROPSHEETPAGE Create();
```

### <a name="return-value"></a>返回值

包含新创建的`PROPSHEETPAGE`属性表的属性的结构的句柄。

### <a name="remarks"></a>备注

在调用此函数之前, 您应该首先调用[CSnapInPropertyPageImpl:: CSnapInPropertyPageImpl](#csnapinpropertypageimpl) 。

##  <a name="m_psp"></a>CSnapInPropertyPageImpl::m_psp

`m_psp`是一个结构, 其成员存储的特征`PROPSHEETPAGE`。

```
PROPSHEETPAGE m_psp;
```

### <a name="remarks"></a>备注

使用此结构可以在构造后初始化属性页的外观。

有关此结构的详细信息 (包括其成员的列表), 请参阅 Windows SDK 中的[PROPSHEETPAGE](/windows/win32/api/prsht/ns-prsht-propsheetpagea_v3) 。

##  <a name="onapply"></a>CSnapInPropertyPageImpl::OnApply

当用户单击 **"确定"** 或 "**立即应用**" 按钮时, 将调用此成员函数。

```
BOOL OnApply();
```

### <a name="return-value"></a>返回值

如果接受更改, 则为非零值;否则为0。

### <a name="remarks"></a>备注

在`OnApply`框架可以调用之前, 必须先调用`SetModified`并将其参数设置为 TRUE。 这将在用户在属性页上进行更改后立即激活 "**立即应用**" 按钮。

重写此成员函数以指定用户单击 "**立即应用**" 按钮时程序采取的操作。 重写时, 函数应返回 TRUE 以接受更改, 并返回 FALSE 以防止更改生效。

的`OnApply`默认实现返回 TRUE。

##  <a name="onhelp"></a>CSnapInPropertyPageImpl::OnHelp

当用户单击属性页的 "**帮助**" 按钮时, 将调用此成员函数。

```
void OnHelp();
```

### <a name="remarks"></a>备注

重写此成员函数以显示属性页的帮助。

##  <a name="onkillactive"></a>  CSnapInPropertyPageImpl::OnKillActive

当页不再是活动页时, 将调用此成员函数。

```
BOOL OnKillActive();
```

### <a name="return-value"></a>返回值

如果成功更新了数据, 则为非零值;否则为0。

### <a name="remarks"></a>备注

重写此成员函数以执行特殊的数据验证任务。

##  <a name="onquerycancel"></a>CSnapInPropertyPageImpl:: OnQueryCancel

当用户单击 "**取消**" 按钮, 并在取消操作发生之前, 将调用此成员函数。

```
BOOL OnQueryCancel();
```

### <a name="return-value"></a>返回值

如果允许取消操作, 则为非零值;否则为0。

### <a name="remarks"></a>备注

重写此成员函数以指定用户单击 "**取消**" 按钮时程序采取的操作。

的`OnQueryCancel`默认实现返回 TRUE。

##  <a name="onreset"></a>CSnapInPropertyPageImpl:: OnReset

当用户单击 "**取消**" 按钮时, 将调用此成员函数。

```
void OnReset();
```

### <a name="remarks"></a>备注

调用此函数时, 将丢弃用户之前单击 "**立即应用**" 按钮所做的所有属性页的更改, 并且属性表将保留焦点。

重写此成员函数以指定用户单击 "**取消**" 按钮时程序采取的操作。

##  <a name="onsetactive"></a>CSnapInPropertyPageImpl::OnSetActive

当用户选择页面并成为活动页面时, 将调用此成员函数。

```
BOOL OnSetActive();
```

### <a name="return-value"></a>返回值

如果成功设置了页面, 则为非零值;否则为0。

### <a name="remarks"></a>备注

当激活某个页面时, 重写此成员函数以执行任务。 此成员函数的重写应在执行任何其他处理之前调用默认版本。

默认实现返回 TRUE。

##  <a name="onwizardback"></a>CSnapInPropertyPageImpl::OnWizardBack

当用户单击向导中的 "**后退**" 按钮时, 将调用此成员函数。

```
BOOL OnWizardBack();
```

### <a name="return-value"></a>返回值

- 0自动前进到上一页。

- -1, 以防页面发生变化。

若要跳转到下一个页面, 请返回要显示的对话框的标识符。

### <a name="remarks"></a>备注

重写此成员函数以指定在单击 "**后退**" 按钮时用户必须执行的某些操作。

##  <a name="onwizardfinish"></a>CSnapInPropertyPageImpl::OnWizardFinish

当用户在向导中单击 "**完成**" 按钮时, 将调用此成员函数。

```
BOOL OnWizardFinish();
```

### <a name="return-value"></a>返回值

如果向导完成时属性表被销毁, 则为非零值;否则为零。

### <a name="remarks"></a>备注

重写此成员函数以指定在单击 "**完成**" 按钮时用户必须执行的某些操作。

##  <a name="onwizardnext"></a>CSnapInPropertyPageImpl::OnWizardNext

当用户在向导中单击 "**下一步**" 按钮时, 将调用此成员函数。

```
BOOL OnWizardNext();
```

### <a name="return-value"></a>返回值

- 0会自动前进到下一页。

- -1, 以防页面发生变化。

若要跳转到下一个页面, 请返回要显示的对话框的标识符。

### <a name="remarks"></a>备注

重写此成员函数以指定在单击 "**下一步**" 按钮时用户必须执行的某些操作。

##  <a name="querysiblings"></a>CSnapInPropertyPageImpl::QuerySiblings

调用此成员函数将消息转发到属性表中的每一页。

```
LRESULT QuerySiblings(WPARAM wParam, LPARAM lParam);
```

### <a name="parameters"></a>参数

*wParam*<br/>
中指定其他消息相关的信息。

*lParam*<br/>
中指定其他消息相关的信息。

### <a name="return-value"></a>返回值

如果不应将消息转发到下一个属性页, 则为非零值;否则为零。

### <a name="remarks"></a>备注

如果页面返回一个非零值, 则该属性表不会将该消息发送到后续页面。

##  <a name="setmodified"></a>CSnapInPropertyPageImpl:: SetModified

调用此成员函数以启用或禁用 "**立即应用**" 按钮, 具体取决于是否应将 "属性" 页中的设置应用于相应的外部对象。

```
void SetModified(BOOL bChanged = TRUE);
```

### <a name="parameters"></a>参数

*bChanged*<br/>
中如果为 TRUE, 则指示自上次应用后修改了属性页设置;若为 FALSE, 则指示属性页设置已应用, 或应忽略。

### <a name="remarks"></a>备注

属性表跟踪哪些页是 "脏的", 即您已调用`SetModified( TRUE )`的属性页。 如果调用`SetModified( TRUE )`某个页面, 将始终启用 "**立即应用**" 按钮。 当你为某个页面调用`SetModified( FALSE )`时, "**立即应用**" 按钮将被禁用, 但前提是所有其他页面均未 "更新"。

## <a name="see-also"></a>请参阅

[类概述](../../atl/atl-class-overview.md)
