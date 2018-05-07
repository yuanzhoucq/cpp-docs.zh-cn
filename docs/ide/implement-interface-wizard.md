---
title: 实现接口向导 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.impl.interface.overview
dev_langs:
- C++
helpviewer_keywords:
- Implement Interface Wizard [C++]
ms.assetid: 947c329e-0815-4ca7-835e-c41dfeb75f9e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bf2ddf83b7a03f8d4e01b61f82e46e0d26a5547b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="implement-interface-wizard"></a>实现接口向导
此向导实现 COM 对象的接口。 适用于 Visual Studio 和 Windows 的 COM 库中包括多个接口的实现。 时将创建该对象的实例，并且它提供服务，该对象所提供的接口实现与对象相关联。  
  
 接口和实现的讨论，请参阅[接口和接口实现](http://msdn.microsoft.com/library/windows/desktop/ms694356)Windows SDK 中。  
  
 **实现接口的位置**  
 指定从中创建接口的类型库的位置。  
  
|选项|描述|  
|------------|-----------------|  
|**Project**|类型库是项目的一部分。|  
|**Registry**|在系统中注册的类型库。 已注册的类型库中列出**可用的类型库**。|  
|**文件**|类型库不一定在系统中注册，但包含在文件中。 必须提供文件的位置中**位置**。|  
  
 **可用的类型库**  
 显示包含可以实现的接口定义的可用类型库。 如果你单击**文件**下**实现接口的位置**，此框不可更改。  
  
 **位置**  
 显示的类型库中当前选定位置**可用的类型库**列表。 如果你选择**文件**下**实现接口的位置**，单击省略号按钮以找到包含要使用的类型库的文件。  
  
 **接口**  
 显示其定义中当前选定的类型库中包含的接口**可用的类型库**框。  
  
> [!NOTE]
>  接口具有相同的名称，那些已由所选对象不显示在**接口**框。  
  
|传输按钮|描述|  
|---------------------|-----------------|  
|**>**|将添加到**实现接口**列表中当前选定的接口名称**接口**列表。|  
|**>>**|将添加到**实现接口**列表中可用的所有接口名称**接口**都列表。|  
|**<**|移除中当前选定的接口名称**实现接口**列表。|  
|**<\<**|删除的所有接口名称中当前列出**实现接口**列表。|  
  
 **实现接口**  
 显示您已选择在你的对象上实现的接口的名称。  
  
> [!NOTE]
>  如果包含派生自的多个接口`IDispatch`，或如果您尝试实现一个接口，从已在你的类，另一个接口派生，则你必须区分 COM_MAP 项。 请参阅[COM_INTERFACE_ENTRY2](../atl/reference/com-interface-entry-macros.md#com_interface_entry2)有关详细信息。  
  
## <a name="see-also"></a>请参阅  
 [实现接口](../ide/implementing-an-interface-visual-cpp.md)