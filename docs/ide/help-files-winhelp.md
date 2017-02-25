---
title: "帮助文件 (WinHelp) | Microsoft Docs"
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
  - "文件类型 [C++], WinHelp 文件"
ms.assetid: 4fdcbd66-66b0-4866-894a-fd7b4c2557e4
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 帮助文件 (WinHelp)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

当通过选择“区分上下文的帮助”复选框，然后在 MFC 应用程序向导的[高级功能](../mfc/reference/advanced-features-mfc-application-wizard.md)页中选择“WinHelp 格式”，向应用程序添加 WinHelp 类型的帮助支持时创建下列文件。  
  
|文件名|目录位置|解决方案资源管理器位置|说明|  
|---------|----------|-----------------|--------|  
|*Projname*.hpj|*Projname*\\hlp|源文件|由帮助编译器用来创建程序或控件的帮助文件的帮助项目文件。|  
|*Projname*.rtf|*Projname*\\hlp|帮助文件|包含可编辑的模板主题和有关自定义 .hpj 文件的信息。|  
|*Projname*.cnt|*Projname*\\hlp|帮助文件|为 Windows 帮助中的**“目录”**窗口提供结构。|  
|Makehelp.bat|*Projname*|源文件|由系统用来在编译项目时生成帮助项目。|  
|Print.rtf|*Projname*\\hlp|帮助文件|项目包括打印支持（默认）时创建。  描述打印命令和对话框。|  
|\*.bmp|*Projname*\\hlp|资源文件|包含生成的不同帮助文件主题的图像。|  
  
 通过在 MFC ActiveX 控件向导的[应用程序设置](../mfc/reference/application-settings-mfc-activex-control-wizard.md)选项卡中选择“生成帮助文件”，可以为 MFC ActiveX 控件项目添加 WinHelp 支持。  当为 MFC ActiveX 控件添加帮助支持时，下列文件被添加到项目中：  
  
|文件名|目录位置|解决方案资源管理器位置|说明|  
|---------|----------|-----------------|--------|  
|*Projname*.hpj|*Projname*\\hlp|源文件|由帮助编译器用来创建程序或控件的帮助文件的项目文件。|  
|*Projname*.rtf|*Projname*\\hlp|Project|包含可编辑的模板主题和有关自定义 .hpj 文件的信息。|  
|Makehelp.bat|*Projname*|源文件|由系统用来在编译项目时生成帮助项目。|  
|Bullet.bmp|*Projname*|资源文件|由标准帮助文件主题用来表示项目符号列表。|  
  
## 请参阅  
 [为 Visual C\+\+ 项目创建的文件类型](../ide/file-types-created-for-visual-cpp-projects.md)