---
title: 实现双重接口 (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- IDispatchImpl class, implementing dual interfaces
- dual interfaces, implementing
ms.assetid: d1da3633-b445-4dcd-8a0a-3efdafada3ea
ms.openlocfilehash: ecd6a0cc90ca4175c4ae898f2e9aa8bf00508a3e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62262224"
---
# <a name="implementing-a-dual-interface"></a>实现双重接口

您可以实现双重接口使用[IDispatchImpl](../atl/reference/idispatchimpl-class.md)类，该类提供的默认实现`IDispatch`双重接口中的方法。 有关更多信息，请参见 [Implementing the IDispatch Interface](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface)。

若要使用此类：

- 类型库中定义双重接口。

- 您的类派生的专用化`IDispatchImpl`（传递信息有关的接口和类型库作为模板参数）。

- 将一项 （或项） 添加到 COM 映射公开双重接口通过`QueryInterface`。

- 在类中实现的接口 vtable 一部分。

- 请确保在运行时包含接口定义的类型库是可用于您的对象。

## <a name="atl-simple-object-wizard"></a>ATL 简单对象向导

如果你想要创建新的接口和一个新类来实现它，则可以使用[ATL 添加类对话框](../ide/add-class-dialog-box.md)，然后[ATL 简单对象向导](../atl/reference/atl-simple-object-wizard.md)。

## <a name="implement-interface-wizard"></a>实现接口向导

如果有现有的接口，则可以使用[实现接口向导](../atl/reference/adding-a-new-interface-in-an-atl-project.md)将必要的基本类、 COM 映射项和主干方法实现添加到现有类。

> [!NOTE]
>  可能需要调整生成的基类，以便用作模板的参数传递的类型库的主版本号和次版本号应用`IDispatchImpl`基类。 实现接口向导不会为你检查类型库版本号。

## <a name="implementing-idispatch"></a>实现 IDispatch

可以使用`IDispatchImpl`基类，以只需通过 COM 映射中指定的相应条目中提供的调度接口实现 (使用[COM_INTERFACE_ENTRY2](reference/com-interface-entry-macros.md#com_interface_entry2)或[COM_INTERFACE_ENTRY_IID](reference/com-interface-entry-macros.md#com_interface_entry_iid)宏)，只要有一个类型库描述相应的双重接口。 它是相当常见实现`IDispatch`接口这样一来，例如。 ATL 简单对象向导和实现接口向导都假设你想要实现`IDispatch`在这种方式，因此它们将添加适当的条目到映射。

> [!NOTE]
>  ATL 提供[IDispEventImpl](../atl/reference/idispeventimpl-class.md)并[IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md)类可帮助您实现的调度接口，而无需包含兼容的双重接口定义的类型库。

## <a name="see-also"></a>请参阅

[双重接口和 ATL](../atl/dual-interfaces-and-atl.md)
