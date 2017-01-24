---
title: "OLE 通用对话框类 | Microsoft Docs"
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
  - "vc.classes.ole"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActiveX 类 [C++]"
  - "通用对话框类"
  - "对话框类 [C++], OLE"
  - "OLE 通用对话框类 [C++]"
ms.assetid: 706526ae-f94f-4909-a0f8-6b5fe954fd97
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# OLE 通用对话框类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

这些类将实现许多常用 OLE 的标准 OLE 对话框处理任务。  它们用于 OLE 功能还提供一致的用户界面。  
  
 [COleDialog](../mfc/reference/coledialog-class.md)  
 用于 OLE 对话框由框架包含所有常见的实现。  以用户界面类的所有对话框类从该基类派生。  `COleDialog` 不能被一起使用。  
  
 [COleInsertDialog](../mfc/reference/coleinsertdialog-class.md)  
 查看插入对话框，插入的新链接的或嵌入的 OLE 项标准的用户界面。  
  
 [COlePasteSpecialDialog](../mfc/reference/colepastespecialdialog-class.md)  
 将显示特殊的编辑粘贴命令，对话框实现特定标准的用户界面。  
  
 [COleLinksDialog](../mfc/reference/colelinksdialog-class.md)  
 显示编辑链接标准对话框，用户接口有关链接的更改的信息。  
  
 [COleChangeIconDialog](../mfc/reference/colechangeicondialog-class.md)  
 显示更改图标对话框中，更改的标准图标用户界面与 OLE 嵌入式或链接的项。  
  
 [COleConvertDialog](../mfc/reference/coleconvertdialog-class.md)  
 显示对话框转换，转换的标准 OLE 项用户界面从一个类型到另一个。  
  
 [COlePropertiesDialog](../mfc/reference/colepropertiesdialog-class.md)  
 封装 Windows 公共OLE对话框。  通用 OLE 属性对话框提供一种简便方法来显示和修改一个 OLE 文档项的一些属性与 Windows 标准。  
  
 [COleUpdateDialog](../mfc/reference/coleupdatedialog-class.md)  
 显示更新对话框，更新所有链接的标准的用户界面在文档。  对话框包含一个进度指示器输出指示关闭进程与完成。  
  
 [COleChangeSourceDialog](../mfc/reference/colechangesourcedialog-class.md)  
 显示源更改对话框，将链接的目标或源标准的用户界面。  
  
 [COleBusyDialog](../mfc/reference/colebusydialog-class.md)  
 显示不响应服务器忙碌和的服务器对话框，处理的调用标准的用户界面为正忙应用程序。  通常自动显示 `COleMessageFilter` 实现。  
  
## 请参阅  
 [类概述](../mfc/class-library-overview.md)