---
title: "设置 ActiveX 控件的事件处理程序 | Microsoft Docs"
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
  - "ActiveX 控件 [C++], 事件"
  - "事件 [C++], ActiveX 控件"
ms.assetid: c076386f-c78b-4dc9-9201-a544252d5337
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 设置 ActiveX 控件的事件处理程序
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

可以编程方式设置 ActiveX 控件响应事件。  可以在属性中使用 **ControlEvents** 来查看控件中的可用事件和创建事件处理程序。  事件处理通常用于捕获数据源查询中的更改。  更改包括：  
  
-   实现查找。  当控件（如 DBCombo 框）更改值时，捕获更改事件以更新数据控件的查询。  
  
-   实现主从关系。  将两个数据控件添加到对话框中，一个用于主要部分，另一个用于明细部分。  只要第一个数据源更改，第二个数据源的查询就会通过事件处理程序更新。  
  
-   捕获错误。  大部分控件都具有错误事件，您可以为其编写错误处理程序（请参见 [错误捕获](../../data/ado-rdo/error-trapping.md)）。  
  
 有关更多信息，请参见[将消息映射到函数](../../mfc/reference/mapping-messages-to-functions.md)。  
  
## 请参阅  
 [使用 ActiveX 控件](../../data/ado-rdo/using-activex-controls.md)