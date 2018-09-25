---
title: 实现接口向导 | Microsoft Docs
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
ms.openlocfilehash: 3e5d48688d271330c1cbcbac69f2e0b0c60ccbe8
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45713747"
---
# <a name="implement-interface-wizard"></a>实现接口向导
本向导实现 COM 对象的接口。 Visual Studio 和 Windows 提供的 COM 库中包含许多接口的实现。 创建某个对象的实例时，接口实现即与该对象相关联，并提供该对象提供的服务。  
  
有关接口和实现的讨论，请参阅 Windows SDK 中的[接口和接口实现](/windows/desktop/com/interfaces-and-interface-implementations)。  
  
- **实现接口的位置**

   指定从中创建接口的类型库的位置。  
  
   |选项|描述|  
   |------------|-----------------|  
   |**Project**|类型库是项目的一部分。|  
   |**Registry**|在系统中注册类型库。 “可用类型库”中列出了已注册的类型库。|  
   |**文件**|类型库不必在系统中进行注册，但必须包含在文件中。 必须在“位置”中提供文件位置。|  
  
- **可用类型库**

   显示包含可实现的接口定义的可用类型库。 如果在“实现接口的位置”下单击“文件”，则此框无法更改。  
  
- **位置**

   显示“可用类型库”列表中当前选择的类型库的位置。 如果在“实现接口的位置”下选择了“文件”，请单击省略号按钮以找到包含要使用的类型库的文件。  
  
- **接口**

   显示其定义包含在“可用类型库”框中当前选定的类型库中的接口。  
  
   > [!NOTE]
   > “接口”框中不显示与选定对象已实现的接口同名的接口。  
  
   |传输按钮|描述|  
   |---------------------|-----------------|  
   |**>**|将当前在“接口”列表中选择的接口名称添加到“实现接口”列表中。|  
   |**>>**|将“接口”列表中可用的所有接口名称添加到“实现接口”列表中。|  
   |**\<**|删除当前在“实现接口”列表中所选的接口名称。|  
   |**\<\<**|删除当前在“实现接口”列表中列出的所有接口名称。|  
  
- **实现接口**

   显示已选择在对象上实现的接口名称。  
  
   > [!NOTE]
   > 如果包含从 `IDispatch` 派生的多个接口，或者尝试实现从类中已有的另一个接口派生的接口，则必须消除 COM_MAP 项的歧义。 有关详细信息，请参阅 [COM_INTERFACE_ENTRY2](../atl/reference/com-interface-entry-macros.md#com_interface_entry2)。  
  
## <a name="see-also"></a>请参阅  
 [实现接口](../ide/implementing-an-interface-visual-cpp.md)