---
title: "ActiveX 控件容器：查看和修改控件属性 | Microsoft Docs"
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
  - "ActiveX 控件容器 [C++], 查看和修改属性"
  - "ActiveX 控件 [C++], 属性"
  - "控件 [MFC], 属性"
  - "属性 [MFC], 查看和修改"
  - "资源编辑器, 查看和修改 ActiveX 控件"
ms.assetid: 14ce5152-742b-4e0d-a9ab-c7b456e32918
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ActiveX 控件容器：查看和修改控件属性
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在插入 ActiveX 控件到项目时，查看和更改支持 ActiveX 控件的属性是很有用的。  本文讨论如何使用 Visual C\+\+ 资源编辑器执行此操作。  
  
 如果 ActiveX 控件容器应用程序使用嵌入的控件，当在资源编辑器中时可以查看和修改控件的属性。  在设计时，您可以使用资源编辑器设置属性值。  资源编辑器自动保存在项目资源文件的这些值。  控件的所有实例将使其属性初始化为这些值。  
  
 此过程假定，插入控件到项目中。  有关信息，请参见 [ActiveX 控件容器：插入一个控件表列控件容器应用程序](../mfc/inserting-a-control-into-a-control-container-application.md)。  
  
 演示控件的属性的第一步是将控件实例添加到项目的对话框模板。  
  
### 演示用户控件的属性  
  
1.  在资源视图中，打开 **对话框** 文件夹。  
  
2.  打开主对话框模板。  
  
3.  使用 **插入 ActiveX 控件** 对话框插入 ActiveX 控件。  有关更多信息，请参见 [显示和 ActiveX 控件添加到对话框](../mfc/viewing-and-adding-activex-controls-to-a-dialog-box.md)。  
  
4.  选择对话框上的控件。  
  
5.  在属性窗口中，单击 **属性**按钮。  
  
 使用**属性** 对话框立即修改和测试新属性。  
  
## 请参阅  
 [ActiveX 控件容器](../mfc/activex-control-containers.md)