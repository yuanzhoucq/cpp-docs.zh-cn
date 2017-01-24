---
title: "使用 ActiveX 控件 | Microsoft Docs"
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
  - "ActiveX 控件 [C++], 关于 ActiveX 控件"
  - "控件 [C++], ActiveX"
ms.assetid: 33442173-205d-492f-82c8-9a8105358ec6
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用 ActiveX 控件
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本节中的主题概括介绍如何使用 ActiveX 控件。  
  
 ActiveX 控件是一个 COM 组件，支持与持久性、连接点和宿主相关的标准接口。  这些标准接口定义控件可用来在控件容器中寄宿、交换消息和处理事件的协议。  
  
 作为 COM 服务器，ActiveX 控件具有：  
  
|术语|说明|  
|--------|--------|  
|属性|控件具有表示内部状态并作为 **Get** 和 `Set` 访问器函数实现的成员变量。  在 .idl 文件中，为每个带 propget 标记的访问器方法生成了一个 **Get** 函数，  为每个带 propput 或 propputref IDL 标记的访问器方法生成了一个 `Set` 函数。<br /><br /> 使用[包装类](../../data/ado-rdo/wrapper-classes.md)或 [OLE\/COM 对象查看器](../../data/ado-rdo/using-the-ole-com-object-viewer.md)来确定访问器函数的定义方式。|  
|方法|控件的行为由其公共方法定义。  包装类提供对控件方法的访问。<br /><br /> 如果没有使用包装类（默认），则通过获得指向接口的指针来访问控件的方法。<br /><br /> 公共方法的一个示例是 ADO 数据控件中的 **Refresh** 方法，它更新检索的行集合。|  
|事件|控件可生成事件来通知主机有情况发生。  Button 控件的 `OnClick` 事件即属于这类事件。  按钮被单击时生成 `OnClick` 事件。  如果控件的主机具有该事件的处理程序，则执行该处理程序。|  
|类型库|类型库通知控件容器控件支持哪些属性、方法和事件。  类型库可以作为单独的文件存在（带 .tlb 扩展名），或者在控件内部存在。<br /><br /> 类型库还包含控件的 coclass 信息。  coclass 是用 GUID 标识的 COM 类。  coclass 包含一个或多个由控件定义的接口。<br /><br /> 若要检查类型库，请使用 [OLE\/COM 对象查看器](../../data/ado-rdo/using-the-ole-com-object-viewer.md)。|  
  
 下面的主题描述了 ActiveX 控件的使用：  
  
-   [将控件插入 Visual C\+\+ 应用程序](../../data/ado-rdo/inserting-the-control-into-a-visual-cpp-application.md)  
  
-   [包装类](../../data/ado-rdo/wrapper-classes.md)  
  
-   [创建数据库连接](../../data/ado-rdo/creating-database-connections.md)  
  
-   [在设计时设置控件属性](../../data/ado-rdo/setting-control-properties-at-design-time.md)  
  
-   [设置 ActiveX 控件的事件处理程序](../../data/ado-rdo/setting-event-handlers-on-activex-controls.md)  
  
-   [修改控件的运行时行为](../../data/ado-rdo/modifying-a-control-s-run-time-behavior.md)  
  
-   [重新发布控件](../../data/ado-rdo/redistributing-controls.md)  
  
## 请参阅  
 [数据绑定控件（ADO 和 RDO）](../../data/ado-rdo/data-bound-controls-ado-and-rdo.md)