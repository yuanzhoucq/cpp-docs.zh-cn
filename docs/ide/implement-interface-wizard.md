---
title: "实现接口向导 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.codewiz.impl.interface.overview"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "实现接口向导 [C++]"
ms.assetid: 947c329e-0815-4ca7-835e-c41dfeb75f9e
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 实现接口向导
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

该向导实现 COM 对象的接口。  Visual Studio 和 Windows 附带的 COM 库中包含了许多接口的实现。  当创建对象的实例时，接口实现与该对象关联并提供该对象所提供的服务。  
  
 有关接口和实现的论述，请参见 [!INCLUDE[winsdkshort](../atl/reference/includes/winsdkshort_md.md)] 中的[接口和接口实现](http://msdn.microsoft.com/library/windows/desktop/ms694356)。  
  
 **实现接口的位置**  
 指定类型库的位置，将从该位置创建接口。  
  
|选项|说明|  
|--------|--------|  
|**Project**|类型库是项目的一部分。|  
|**注册表**|类型库已在系统中注册。  已注册的类型库在“可用的类型库”中列出。|  
|**文件**|类型库不一定在系统中注册，但包含在文件中。  必须在“位置”中提供文件的位置。|  
  
 **可用的类型库**  
 显示包含可以实现的接口定义的可用类型库。  如果单击“实现接口的位置”下的“文件”，则该框不可更改。  
  
 **位置**  
 显示“可用的类型库”列表中当前选定的类型库的位置。  如果选择“实现接口的位置”下的“文件”，则单击省略号按钮可定位包含要使用的类型库的文件。  
  
 **接口**  
 显示定义包含在“可用的类型库”框中当前选定的类型库中的接口。  
  
> [!NOTE]
>  与选定对象已实现的那些接口具有相同名称的接口不显示在“接口”框中。  
  
|传输按钮|说明|  
|----------|--------|  
|**\>**|将“接口”列表中当前选定的接口名称添加到“实现接口”列表。|  
|**\>\>**|将“接口”列表中可用的所有接口名称添加到“实现接口”列表。|  
|**\<**|移除“实现接口”列表中当前选定的接口名称。|  
|**\<\<**|移除“实现接口”列表中当前列出的所有接口名称。|  
  
 **实现接口**  
 显示已选定在对象上实现的接口名称。  
  
> [!NOTE]
>  如果包括从 `IDispatch` 派生的多个接口，或者尝试实现从类上的另一个现有接口派生的接口，则必须消除 COM\_MAP 项的歧义。  有关更多信息，请参见 [COM\_INTERFACE\_ENTRY2](../Topic/COM_INTERFACE_ENTRY2.md)。  
  
## 请参阅  
 [实现接口](../ide/implementing-an-interface-visual-cpp.md)