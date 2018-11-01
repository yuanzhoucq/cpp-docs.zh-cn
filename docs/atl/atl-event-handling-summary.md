---
title: ATL 事件处理摘要
ms.date: 11/04/2016
helpviewer_keywords:
- event handling, implementing
ms.assetid: e8b47ef0-0bdc-47ff-9dd6-34df11dde9a2
ms.openlocfilehash: e2b17e7b6849163ee0e8e12696df25169e2773cd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50654865"
---
# <a name="atl-event-handling-summary"></a>ATL 事件处理摘要

一般情况下，处理 COM 事件是一个相对较简单的过程。 有三个主要步骤：

- 在对象上实现事件接口。

- 建议您的对象想要接收事件的事件源。

- 当您的对象不再需要接收事件时，不建议事件源。

## <a name="implementing-the-interface"></a>实现接口

有四个主要方法的实现使用 ATL 接口

|派生自|适用于接口类型|要求您实现所有方法 *|在运行时需要类型库|
|-----------------|---------------------------------|---------------------------------------------|-----------------------------------------|
|接口|Vtable|是|否|
|[IDispatchImpl](../atl/reference/idispatchimpl-class.md)|双|是|是|
|[IDispEventImpl](../atl/reference/idispeventimpl-class.md)|调度接口|否|是|
|[IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md)|调度接口|否|否|

\* 使用 ATL 的支持类时，您永远不会实现所需`IUnknown`或`IDispatch`方法手动。

## <a name="advising-and-unadvising-the-event-source"></a>通知和取消通知事件源

有三种主要方法的通知和取消通知使用 ATL 的事件源

|通知函数|不建议函数|最适合与一起使用|需要跟踪的 cookie|注释|
|---------------------|-----------------------|--------------------------------|---------------------------------------------|--------------|
|[AtlAdvise](reference/connection-point-global-functions.md#atladvise)， [CComPtrBase::Advise](../atl/reference/ccomptrbase-class.md#advise)|[AtlUnadvise](reference/connection-point-global-functions.md#atlunadvise)|Vtable 或双重接口|是|`AtlAdvise` 是一个全局的 ATL 函数。 `CComPtrBase::Advise` 可供[CComPtr](../atl/reference/ccomptr-class.md)并[CComQIPtr](../atl/reference/ccomqiptr-class.md)。|
|[IDispEventSimpleImpl::DispEventAdvise](../atl/reference/idispeventsimpleimpl-class.md#dispeventadvise)|[IDispEventSimpleImpl::DispEventUnadvise](../atl/reference/idispeventsimpleimpl-class.md#dispeventunadvise)|[IDispEventImpl](../atl/reference/idispeventimpl-class.md)或[IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md)|否|参数少于`AtlAdvise`由于基类执行的操作更多的工作。|
|[CComCompositeControl::AdviseSinkMap(TRUE)](../atl/reference/ccomcompositecontrol-class.md#advisesinkmap)|[CComCompositeControl::AdviseSinkMap(FALSE)](../atl/reference/ccomcompositecontrol-class.md#advisesinkmap)|复合控件中的 ActiveX 控件|否|`CComCompositeControl::AdviseSinkMap` 建议所有条目在事件都接收器映射。 相同的函数取消通知项。 会自动调用此方法`CComCompositeControl`类。|
|[CAxDialogImpl::AdviseSinkMap(TRUE)](../atl/reference/caxdialogimpl-class.md#advisesinkmap)|[CAxDialogImpl::AdviseSinkMap(FALSE)](../atl/reference/caxdialogimpl-class.md#advisesinkmap)|在对话框中的 ActiveX 控件|否|`CAxDialogImpl::AdviseSinkMap` 建议和取消通知对话框资源中的所有 ActiveX 控件。 这是为你自动完成。|

## <a name="see-also"></a>请参阅

[事件处理](../atl/event-handling-and-atl.md)<br/>
[支持 IDispEventImpl](../atl/supporting-idispeventimpl.md)

