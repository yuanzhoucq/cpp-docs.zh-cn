---
title: 实现双重接口 (ATL) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDispatchImpl class, implementing dual interfaces
- dual interfaces, implementing
ms.assetid: d1da3633-b445-4dcd-8a0a-3efdafada3ea
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 34cc55e4466dba094bf70e734340b40237207f3c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32356727"
---
# <a name="implementing-a-dual-interface"></a>实现双重接口
你可以实现双重接口使用[IDispatchImpl](../atl/reference/idispatchimpl-class.md)类，该类提供的默认实现`IDispatch`双重接口中的方法。 有关更多信息，请参见 [Implementing the IDispatch Interface](http://msdn.microsoft.com/en-us/0e171f7f-0022-4e9b-ac8e-98192828e945)。  
  
 若要使用此类：  
  
-   在类型库中定义你的双重接口。  
  
-   你的类派生的专用化`IDispatchImpl`（传递信息有关的接口和类型库作为模板自变量）。  
  
-   将一项 （或项） 添加到要公开通过双重接口的 COM 映射`QueryInterface`。  
  
-   类中实现的接口的 vtable 一部分。  
  
-   确保包含接口定义的类型库在运行时对你的对象可用。  
  
## <a name="atl-simple-object-wizard"></a>ATL 简单对象向导  
 如果你想要创建新的接口和实现它的新类，则可以使用[ATL 添加类对话框](../ide/add-class-dialog-box.md)，，然后[ATL 简单对象向导](../atl/reference/atl-simple-object-wizard.md)。  
  
## <a name="implement-interface-wizard"></a>实现接口向导  
 如果你有现有的接口，则可以使用[实现接口向导](../atl/reference/adding-a-new-interface-in-an-atl-project.md)若要向现有类中添加必要的基本类、 COM 映射项和主干方法实现。  
  
> [!NOTE]
>  你可能需要调整生成的基类，这样的类型库的主版本号和次版本号作为模板参数传递给你`IDispatchImpl`基类。 实现接口向导不会为你检查类型库的版本号。  
  
## <a name="implementing-idispatch"></a>实现 IDispatch  
 你可以使用`IDispatchImpl`基类，以只需通过 COM 映射中指定的相应条目中提供的调度接口实现 (使用[COM_INTERFACE_ENTRY2](reference/com-interface-entry-macros.md#com_interface_entry2)或[COM_INTERFACE_ENTRY_IID](reference/com-interface-entry-macros.md#com_interface_entry_iid)宏)，只要具有描述相应的双重接口的类型库。 这是十分常见实现`IDispatch`接口这样一来，例如。 ATL 简单对象向导和实现接口向导同时假定你想要实现`IDispatch`在这种方式，因此它们将添加的相应条目到映射。  
  
> [!NOTE]
>  ATL 提供[IDispEventImpl](../atl/reference/idispeventimpl-class.md)和[IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md)类来帮助你实现的调度接口，而无需包含兼容的双重接口的定义的类型库。  
  
## <a name="see-also"></a>请参阅  
 [双重接口和 ATL](../atl/dual-interfaces-and-atl.md)

