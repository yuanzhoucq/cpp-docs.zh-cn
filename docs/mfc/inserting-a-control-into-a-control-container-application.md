---
title: "ActiveX 控件容器：将控件插入控件容器应用程序 | Microsoft Docs"
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
  - "ActiveX 控件容器 [C++], 插入控件"
  - "ActiveX 控件 [C++], 添加到项目"
ms.assetid: bbb617ff-872f-43d8-b4d6-c49adb16b148
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ActiveX 控件容器：将控件插入控件容器应用程序
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在访问从 ActiveX 控件容器应用程序中的 ActiveX 控件，可以使用 [插入 ActiveX 控件](../mfc/insert-activex-control-dialog-box.md) 对话框，必须将 ActiveX 控件添加到容器应用程序。  
  
 将 ActiveX 控件添加到容器 ActiveX 控件项目，请参见 [显示和 ActiveX 控件添加到对话框](../mfc/viewing-and-adding-activex-controls-to-a-dialog-box.md)。  
  
 一旦添加控件，则需要将成员变量 \(ActiveX 控件类型\)。对话框类。  有关此过程的更多信息，请参见 [添加成员变量](../ide/adding-a-member-variable-visual-cpp.md)。  
  
 一旦添加成员变量的类，称为"包装类，自动生成并添加到项目中。  使用此类，控件容器和嵌入的控件之间的接口。  
  
## 请参阅  
 [ActiveX 控件容器](../mfc/activex-control-containers.md)