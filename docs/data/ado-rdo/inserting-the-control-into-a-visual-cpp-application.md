---
title: "将控件插入 Visual C++ 应用程序 | Microsoft Docs"
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
  - "ActiveX 控件 [C++], 添加到对话框"
ms.assetid: 7d517735-057b-49e3-8edf-eb087369b5b9
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 将控件插入 Visual C++ 应用程序
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

可以从工具栏或使用[插入 ActiveX 控件](../../mfc/insert-activex-control-dialog-box.md)对话框将 ActiveX 控件插入对话框。  
  
### 从工具箱插入 ActiveX 控件  
  
1.  右击工具箱的空白区域。  
  
2.  在快捷菜单上单击**“自定义工具箱”**，然后选择想要的控件。  
  
3.  将控件拖动到对话框编辑器中的对话框。  
  
### 从对话框编辑器插入 ActiveX 控件  
  
1.  右击对话框。  
  
2.  在快捷菜单上单击[“插入 ActiveX 控件”](../../mfc/insert-activex-control-dialog-box.md)。  
  
    > [!NOTE]
    >  从**“插入 ActiveX 控件”**中将 ActiveX 控件插入项目时，[包装类](../../data/ado-rdo/wrapper-classes.md)不包含在项目中。  您需要创建包装类来自定义控件的功能。  
  
## 请参阅  
 [使用 ActiveX 控件](../../data/ado-rdo/using-activex-controls.md)