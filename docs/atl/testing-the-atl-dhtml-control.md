---
title: "Testing the ATL DHTML Control | Microsoft Docs"
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
  - "DHTML controls"
  - "DHTML controls, 测试"
  - "HTML 控件, 测试"
  - "testing controls"
ms.assetid: 0e4b4358-80ce-4505-8b06-ef4f30b1d1f0
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Testing the ATL DHTML Control
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

创建了项目后，可以生成并测试示例控件。  进行这些操作之前，请使用选件类视图和解决方案资源管理器检查该项目。  项目的元素在 [标识DHTML控件项目的元素](../atl/identifying-the-elements-of-the-dhtml-control-project.md)更详细地介绍。  
  
#### 生成并测试ATL DHTML控件  
  
1.  生成项目。  从**“生成”**菜单中单击**“生成解决方案”**。  
  
2.  在生成完成后，打开"测试容器。  有关如何访问测试容器的信息，请参见 [测试属性和事件与测试容器](../mfc/testing-properties-and-events-with-test-container.md)。  
  
3.  在测试容器中，从 **Edit** 菜单上，单击 **Insert New Control**。  
  
4.  在 **Insert Control** 对话框中，选择您的控件从列表框。  请记住，其名称基于您在ATL控件向导指示的短名称。  单击**“确定”**。  
  
5.  检查该控件。  监视它有滚动条。  使用控件的句柄调整该控件激活滚动条。  
  
6.  测试控件的按钮。  背景色更改为按钮表示的颜色。  
  
7.  关闭测试容器。  
  
 接下来，尝试 [修改DHTML控件](../atl/modifying-the-atl-dhtml-control.md)。  
  
## 请参阅  
 [支持 DHTML 控件](../atl/atl-support-for-dhtml-controls.md)