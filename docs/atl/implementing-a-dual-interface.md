---
title: 实现双接口 （ATL）
ms.date: 11/04/2016
helpviewer_keywords:
- IDispatchImpl class, implementing dual interfaces
- dual interfaces, implementing
ms.assetid: d1da3633-b445-4dcd-8a0a-3efdafada3ea
ms.openlocfilehash: a85597adad045bee3edb5cc3ed63c72a22fa08fe
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319470"
---
# <a name="implementing-a-dual-interface"></a>实现双接口

您可以使用[IDispatchImpl](../atl/reference/idispatchimpl-class.md)类实现双接口，该类提供双接口中`IDispatch`方法的默认实现。 有关详细信息，请参阅 [Implementing the IDispatch Interface](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface)。

要使用此类：

- 在类型库中定义双接口。

- 从 （`IDispatchImpl`传递有关接口的信息和类型库作为模板参数） 派生类。

- 向 COM 映射添加条目（或条目）以通过`QueryInterface`公开双接口。

- 在类中实现接口的可 v 可部分。

- 确保包含接口定义的类型库在运行时对对象可用。

## <a name="atl-simple-object-wizard"></a>ATL 简单对象向导

如果要创建新接口和新类来实现它，可以使用[ATL 添加类对话框](../ide/add-class-dialog-box.md)，然后使用[ATL 简单对象向导](../atl/reference/atl-simple-object-wizard.md)。

## <a name="implement-interface-wizard"></a>实现接口向导

如果您有现有接口，则可以使用[实现接口向导](../atl/reference/adding-a-new-interface-in-an-atl-project.md)将必要的基类、COM 映射条目和骨架方法实现添加到现有类。

> [!NOTE]
> 您可能需要调整生成的基类，以便类型库的主要版本号和次要版本号作为模板参数传递给`IDispatchImpl`基类。 实现接口向导不检查类型库版本号。

## <a name="implementing-idispatch"></a>实现 IDispatch

只要具有描述相应`IDispatchImpl`双接口的类型库，就可以使用基类通过在 COM 映射中指定适当的条目（使用[COM_INTERFACE_ENTRY2](reference/com-interface-entry-macros.md#com_interface_entry2)或[COM_INTERFACE_ENTRY_IID](reference/com-interface-entry-macros.md#com_interface_entry_iid)宏）来提供不相关接口的实现。 例如，`IDispatch`以这种方式实现接口很常见。 ATL 简单对象向导和实现界面向导都假定您打算以这种方式实现`IDispatch`，因此它们将添加适当的条目到地图中。

> [!NOTE]
> ATL 提供[IDispEventImpl](../atl/reference/idispeventimpl-class.md)和[IDispEventSimple](../atl/reference/idispeventsimpleimpl-class.md)类，可帮助您实现解接口，而无需包含兼容双接口定义的类型库。

## <a name="see-also"></a>另请参阅

[双接口和 ATL](../atl/dual-interfaces-and-atl.md)
