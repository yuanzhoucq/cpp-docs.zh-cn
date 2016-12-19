---
title: "Implementing a Dual Interface | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "双重接口, 实现"
  - "IDispatchImpl 类, implementing dual interfaces"
ms.assetid: d1da3633-b445-4dcd-8a0a-3efdafada3ea
caps.latest.revision: 12
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Implementing a Dual Interface
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用 [IDispatchImpl](../atl/reference/idispatchimpl-class.md) 选件类，可以实现双重接口，提供 `IDispatch` 方法默认实现在双重接口的。  有关更多信息，请参见 [Implementing the IDispatch Interface](http://msdn.microsoft.com/zh-cn/0e171f7f-0022-4e9b-ac8e-98192828e945)。  
  
 使用此选件类:  
  
-   定义您在类型库中的双绑定接口。  
  
-   从 `IDispatchImpl` 派生您的选件类\(有关接口和类型库的传递信息的专用化用作模板参数）。  
  
-   添加项\(或项\)到COM映射通过 `QueryInterface`显示双绑定接口。  
  
-   实现接口的vtable节中的选件类的。  
  
-   确保该类型包含接口定义的库对您的对象在运行时可用。  
  
## ATL 简单对象向导  
 如果要创建新接口和新选件类实现，则可以使用 [ATL添加选件类对话框](../ide/add-class-dialog-box.md)然后 [ATL简单对象向导](../atl/reference/atl-simple-object-wizard.md)。  
  
## 实现接口向导  
 如果您有现有接口，可用于 [实现接口向导](../atl/reference/adding-a-new-interface-in-an-atl-project.md) 添加必要的基类，COM映射项和主干方法实现到现有选件类。  
  
> [!NOTE]
>  您可能需要调整生成的基类，使该类型库的主版本号和次版本号将作为模板参数对 `IDispatchImpl` 基类。  实现接口向导不检查该类型库版本号。  
  
## 实现IDispatch  
 可以使用 `IDispatchImpl` 基类通过指定相应的项提供调度接口的实现COM映射\(使用 [COM\_INTERFACE\_ENTRY2](../Topic/COM_INTERFACE_ENTRY2.md) 或 [COM\_INTERFACE\_ENTRY\_IID](../Topic/COM_INTERFACE_ENTRY_IID.md) 宏\)，只要您有一个类型描述对应的双重接口的库。  例如它相当常见的实现 `IDispatch` 接口，这样。  ATL简单对象向导并实现接口向导两个假设，您希望此类实现 `IDispatch`，因此，它们将添加相应的项添加到映射。  
  
> [!NOTE]
>  ATL提供 [IDispEventImpl](../atl/reference/idispeventimpl-class.md) 和 [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md) 选件类帮助您实现调度接口，而无需类型包含兼容双重接口定义的库。  
  
## 请参阅  
 [Dual Interfaces and ATL](../atl/dual-interfaces-and-atl.md)