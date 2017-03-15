---
title: "使用手动访问器 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "访问器 [C++], 手动"
  - "命令处理, OLE DB 模板"
  - "手动访问器"
ms.assetid: 29f00a89-0240-482b-8413-4120b9644672
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 使用手动访问器
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

当处理未知命令时要做四项操作：  
  
-   确定参数  
  
-   执行命令  
  
-   确定输出列  
  
-   查看是否有多个返回行集合  
  
 若要用 OLE DB 使用者模板实现此目标，请使用 `CManualAccessor` 类并遵循以下步骤：  
  
1.  打开一个 `CCommand` 对象，并将 `CManualAccessor` 用作模板参数。  
  
    ```  
    CCommand<CManualAccessor, CRowset, CMultipleResults> rs;  
    ```  
  
2.  查询会话中的 **IDBSchemaRowset** 接口，并使用过程参数行集合。  如果 **IDBSchemaRowset** 接口不可用，则查询 `ICommandWithParameters` 接口。  调用 `GetParameterInfo` 以获取信息。  如果两个接口都不可用，则可以假定没有参数。  
  
3.  对于每个参数，调用 `AddParameterEntry` 以添加参数并对其进行设置。  
  
4.  打开行集合，但要将绑定参数设置为 **false**。  
  
5.  调用 `GetColumnInfo` 以检索输出列。  使用 `AddBindEntry` 将输出列添加到绑定中。  
  
6.  调用 `GetNextResult` 以确定是否有更多的可用行集合。  重复步骤 2 到 5。  
  
 有关手动访问器的示例，请参见 [DBVIEWER](http://msdn.microsoft.com/zh-cn/07620f99-c347-4d09-9ebc-2459e8049832) 示例中的 **CDBListView::CallProcedure**。  
  
## 请参阅  
 [使用访问器](../../data/oledb/using-accessors.md)