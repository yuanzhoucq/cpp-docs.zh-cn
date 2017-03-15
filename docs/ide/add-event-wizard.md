---
title: "添加事件向导 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.codewiz.event.overview"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "添加事件向导 [C++]"
ms.assetid: bdd2a7bb-13d5-44d7-abc9-e785ba4e05ce
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 添加事件向导
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

该向导将事件添加到 MFC ActiveX 控件项目。  可以指定自己的事件，可以自定义典型的常用事件，也可以从常用事件列表中选择。  
  
 **事件名称**  
 设置自动化客户端用来从类请求事件的名称。  输入名称或从列表中选择名称。  
  
 **事件类型**  
 指示要添加的事件类型。  仅当从“事件名称”列表中选择时可用。  
  
|选项|说明|  
|--------|--------|  
|**常用**|指定将为该类实现的常用事件，如单击按钮。  常用事件在 Microsoft 基础类 \(MFC\) 库中定义。|  
|**自定义**|指定提供自己的事件实现。|  
  
 **内部名称**  
 设置发送事件的成员函数名。  仅对自定义事件可用。  该名称基于“事件名称”。  如果要提供不同于“事件名称”的名称，可以更改内部名称。  
  
 **参数类型**  
 设置“参数名”的类型。  从列表中选择类型。  
  
 **参数名**  
 设置通过事件传递的参数的名称。  键入名称后，必须单击“添加”将其添加到参数列表中。  
  
 单击“添加”后，参数名出现在**“参数列表”**中。  
  
> [!NOTE]
>  如果提供参数名并在单击“添加”前单击“完成”，则不会将此参数添加到事件中。  必须查找该方法并手动插入参数。**参数列表**  
  
 **添加**  
 将“参数名”中指定的参数及其类型添加到**“参数列表”**中。  必须单击“添加”才能将参数添加到列表中。  
  
 **移除**  
 从列表中移除在**“参数列表”**中选择的参数。  
  
 **参数列表**  
 显示当前为方法添加的所有参数及其类型。  向导在您添加参数的同时更新**“参数列表”**以显示每个参数及其类型。  
  
## 请参阅  
 [添加事件](../ide/adding-an-event-visual-cpp.md)