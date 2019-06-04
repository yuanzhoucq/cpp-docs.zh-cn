---
title: CSnapInPropertyPageImpl Class
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
ms.openlocfilehash: dd60afc34b1a2de8f86037eb180aab86a9b8afde
ms.sourcegitcommit: ecf274bcfe3a977c48745aaa243e5e731f1fdc5f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2019
ms.locfileid: "66503087"
---
# <a name="csnapinpropertypageimpl-class"></a>CSnapInPropertyPageImpl Class

此类提供用于实现一个管理单元中属性的 page 对象的方法。

> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。

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
|[CSnapInPropertyPageImpl::CancelToClose](#canceltoclose)|更改的状态**确定**并**取消**按钮。|
|[CSnapInPropertyPageImpl::Create](#create)|初始化新创建`CSnapInPropertyPageImpl`对象。|
|[CSnapInPropertyPageImpl::OnApply](#onapply)|由框架调用，当用户单击**立即应用**使用向导类型的属性表时的按钮。|
|[CSnapInPropertyPageImpl::OnHelp](#onhelp)|由框架调用，当用户单击**帮助**使用向导类型的属性表时的按钮。|
|[CSnapInPropertyPageImpl::OnKillActive](#onkillactive)|当前页不再处于活动状态时，由框架调用。|
|[CSnapInPropertyPageImpl::OnQueryCancel](#onquerycancel)|由框架调用，当用户单击**取消**按钮取消发生之前。|
|[CSnapInPropertyPageImpl::OnReset](#onreset)|由框架调用，当用户单击**重置**使用向导类型的属性表时的按钮。|
|[CSnapInPropertyPageImpl::OnSetActive](#onsetactive)|当前页变为活动状态时，由框架调用。|
|[CSnapInPropertyPageImpl::OnWizardBack](#onwizardback)|由框架调用，当用户单击**回**使用向导类型的属性表时的按钮。|
|[CSnapInPropertyPageImpl::OnWizardFinish](#onwizardfinish)|由框架调用，当用户单击**完成**使用向导类型的属性表时的按钮。|
|[CSnapInPropertyPageImpl::OnWizardNext](#onwizardnext)|由框架调用，当用户单击**下一步**使用向导类型的属性表时的按钮。|
|[CSnapInPropertyPageImpl::QuerySiblings](#querysiblings)|将转发到的属性表的所有页的当前消息。|
|[CSnapInPropertyPageImpl::SetModified](#setmodified)|调用以激活或停用**立即应用**按钮。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CSnapInPropertyPageImpl::m_psp](#m_psp)|Windows`PROPSHEETPAGE`结构，可由`CSnapInPropertyPageImpl`对象。|

## <a name="remarks"></a>备注

`CSnapInPropertyPageImpl` 提供了一个管理单元中属性的 page 对象的基本实现。 管理单元在属性页的基本功能使用多个不同的接口实现的并将类型映射。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CDialogImplBase`

`CSnapInPropertyPageImpl`

## <a name="requirements"></a>要求

**标头：** atlsnap.h

##  <a name="canceltoclose"></a>  CSnapInPropertyPageImpl::CancelToClose

发生了不可恢复的更改建立到的模式属性表页中的数据之后，请调用此函数。

```
void CancelToClose();
```

### <a name="remarks"></a>备注

此函数将更改**确定**按钮**关闭**并禁用**取消**按钮。 此更改不能取消更改是永久的所做的修改用户的警报。

`CancelToClose`成员函数中不起作用的无模式属性表，因为无模式属性表不具有**取消**默认情况下的按钮。

##  <a name="csnapinpropertypageimpl"></a>  CSnapInPropertyPageImpl::CSnapInPropertyPageImpl

构造 `CSnapInPropertyPageImpl` 对象。

```
CSnapInPropertyPageImpl(LPCTSTR lpszTitle = NULL);
```

### <a name="parameters"></a>参数

*lpszTitle*<br/>
[in]属性页的标题。

### <a name="remarks"></a>备注

若要初始化的基础结构，请调用[CSnapInPropertyPageImpl::Create](#create)。

##  <a name="create"></a>  CSnapInPropertyPageImpl::Create

调用此函数可初始化的属性页的基础结构。

```
HPROPSHEETPAGE Create();
```

### <a name="return-value"></a>返回值

句柄`PROPSHEETPAGE`结构，它包含新创建的属性表的属性。

### <a name="remarks"></a>备注

首先应调用[CSnapInPropertyPageImpl::CSnapInPropertyPageImpl](#csnapinpropertypageimpl)之前调用此函数。

##  <a name="m_psp"></a>  CSnapInPropertyPageImpl::m_psp

`m_psp` 是一种结构的成员将存储的特征`PROPSHEETPAGE`。

```
PROPSHEETPAGE m_psp;
```

### <a name="remarks"></a>备注

使用此结构在构造之后初始化的属性页的外观。

此结构，包括其成员的列表的详细信息请参阅[PROPSHEETPAGE](/windows/desktop/api/prsht/ns-prsht-propsheetpagea_v3) Windows SDK 中。

##  <a name="onapply"></a>  CSnapInPropertyPageImpl::OnApply

当用户单击时调用此成员函数**确定**或**立即应用**按钮。

```
BOOL OnApply();
```

### <a name="return-value"></a>返回值

如果接受所做的更改; 非零值否则为 0。

### <a name="remarks"></a>备注

之前`OnApply`可以调用由框架，您必须调用`SetModified`并将其参数设置为 TRUE。 这将激活**立即应用**按钮只要用户的属性页上进行了更改。

重写此成员函数以指定您的程序在用户单击时采取什么操作**立即应用**按钮。 重写时，该函数应返回以接受更改的 TRUE 和 FALSE 可阻止更改未生效。

默认实现`OnApply`，则返回 TRUE。

##  <a name="onhelp"></a>  CSnapInPropertyPageImpl::OnHelp

当用户单击时调用此成员函数**帮助**属性页的按钮。

```
void OnHelp();
```

### <a name="remarks"></a>备注

重写此成员函数以显示属性页的帮助。

##  <a name="onkillactive"></a>  CSnapInPropertyPageImpl::OnKillActive

当页不再是活动的页面时调用此成员函数。

```
BOOL OnKillActive();
```

### <a name="return-value"></a>返回值

如果数据更新成功，则非零值否则为 0。

### <a name="remarks"></a>备注

重写此成员函数以执行特殊的数据验证任务。

##  <a name="onquerycancel"></a>  CSnapInPropertyPageImpl::OnQueryCancel

当用户单击时调用此成员函数**取消**按钮，然后在取消之前操作发生。

```
BOOL OnQueryCancel();
```

### <a name="return-value"></a>返回值

非零值，允许取消操作;否则为 0。

### <a name="remarks"></a>备注

重写此成员函数以指定程序在用户单击时采取的操作**取消**按钮。

默认实现`OnQueryCancel`，则返回 TRUE。

##  <a name="onreset"></a>  CSnapInPropertyPageImpl::OnReset

当用户单击时调用此成员函数**取消**按钮。

```
void OnReset();
```

### <a name="remarks"></a>备注

当调用此函数时，更改为以前单击的用户所做的所有属性页**立即应用**按钮将被放弃，且属性表保留焦点。

重写此成员函数以指定在用户单击时，程序采用何种操作**取消**按钮。

##  <a name="onsetactive"></a>  CSnapInPropertyPageImpl::OnSetActive

用户选择和成为活动页的页时调用此成员函数。

```
BOOL OnSetActive();
```

### <a name="return-value"></a>返回值

如果页已成功设置活动状态，则非零值否则为 0。

### <a name="remarks"></a>备注

重写此成员函数以激活页面时执行任务。 进行任何其他处理之前，此成员函数的重写应调用的默认版本。

默认实现，则返回 TRUE。

##  <a name="onwizardback"></a>  CSnapInPropertyPageImpl::OnWizardBack

当用户单击时调用此成员函数**回**向导中的按钮。

```
BOOL OnWizardBack();
```

### <a name="return-value"></a>返回值

- 若要自动前进到前一页为 0。

- 为-1 以避免页面更改。

若要跳转到下一个以外的页面，请返回对话框中显示的标识符。

### <a name="remarks"></a>备注

重写此成员函数以指定用户时必须采取某种操作**回**单击按钮。

##  <a name="onwizardfinish"></a>  CSnapInPropertyPageImpl::OnWizardFinish

当用户单击时调用此成员函数**完成**向导中的按钮。

```
BOOL OnWizardFinish();
```

### <a name="return-value"></a>返回值

属性表被销毁时在向导完成; 如果非零值否则为零。

### <a name="remarks"></a>备注

重写此成员函数以指定用户时必须采取某种操作**完成**单击按钮。

##  <a name="onwizardnext"></a>  CSnapInPropertyPageImpl::OnWizardNext

当用户单击时调用此成员函数**下一步**向导中的按钮。

```
BOOL OnWizardNext();
```

### <a name="return-value"></a>返回值

- 若要自动前进到下一步的页为 0。

- 为-1 以避免页面更改。

若要跳转到下一个以外的页面，请返回对话框中显示的标识符。

### <a name="remarks"></a>备注

重写此成员函数以指定用户时必须采取某种操作**下一步**单击按钮。

##  <a name="querysiblings"></a>  CSnapInPropertyPageImpl::QuerySiblings

调用此成员函数以将消息转发到属性表中每一页。

```
LRESULT QuerySiblings(WPARAM wParam, LPARAM lParam);
```

### <a name="parameters"></a>参数

*wParam*<br/>
[in]指定消息相关的其他信息。

*lParam*<br/>
[in]指定消息相关的其他信息。

### <a name="return-value"></a>返回值

如果不应将消息转发到下一步的属性页; 非零值否则为零。

### <a name="remarks"></a>备注

如果页时返回非零值，则属性表不到后续页面发送消息。

##  <a name="setmodified"></a>  CSnapInPropertyPageImpl::SetModified

调用此成员函数可启用或禁用**立即应用**按钮时，根据是否属性页中的设置应该应用到相应的外部对象。

```
void SetModified(BOOL bChanged = TRUE);
```

### <a name="parameters"></a>参数

*bChanged*<br/>
[in]若要指示自上次应用;，已修改的属性页设置如果为 FALSE，以指示已应用，或应忽略的属性页设置。

### <a name="remarks"></a>备注

属性表保留页的"更新"，它是跟踪，请为其调用了的属性页`SetModified( TRUE )`。 **立即应用**将始终启用按钮，如果调用`SetModified( TRUE )`的页面之一。 **立即应用**调用时，将禁用按钮`SetModified( FALSE )`一个页面，但如果没有任何其他页是"更新。

## <a name="see-also"></a>请参阅

[类概述](../../atl/atl-class-overview.md)
