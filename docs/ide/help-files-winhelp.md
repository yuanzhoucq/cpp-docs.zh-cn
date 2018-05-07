---
title: 帮助文件 (WinHelp) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- file types [C++], WinHelp files
ms.assetid: 4fdcbd66-66b0-4866-894a-fd7b4c2557e4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 505506c7f3a14a73c6b0c859a70938fee3eed69e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="help-files-winhelp"></a>帮助文件 (WinHelp)
通过选择的帮助支持 WinHelp 类型添加到你的应用程序时，会创建以下文件**上下文相关帮助**复选框，然后选择**WinHelp 格式**中[高级功能](../mfc/reference/advanced-features-mfc-application-wizard.md)MFC 应用程序向导页。  
  
|文件名|目录位置|解决方案资源管理器位置|描述|  
|---------------|------------------------|--------------------------------|-----------------|  
|*Projname*.hpj|*Projname*\hlp|源文件|帮助编译器用于创建你的程序或控件的帮助文件的帮助项目文件。|  
|*Projname*.rtf|*Projname*\hlp|帮助文件|包含模板主题，你可以编辑和自定义.hpj 文件信息。|  
|*Projname*.cnt 文件|*Projname*\hlp|帮助文件|提供的结构**内容**Windows 帮助中的窗口。|  
|Makehelp.bat|*Projname*|源文件|系统使用它来编译项目时生成的帮助项目。|  
|Print.rtf|*Projname*\hlp|帮助文件|如果你的项目包括打印支持 （默认值），创建。 介绍打印命令和对话框。|  
|*.bmp|*Projname*\hlp|资源文件|包含有关不同的生成的帮助文件的主题的图像。|  
  
 可以通过选择向 MFC ActiveX 控件项目添加 WinHelp 支持**生成帮助文件**中[应用程序设置](../mfc/reference/application-settings-mfc-activex-control-wizard.md)MFC ActiveX 控件向导的选项卡。 将以下文件添加到你的项目时将帮助支持添加到 MFC ActiveX 控件：  
  
|文件名|目录位置|解决方案资源管理器位置|描述|  
|---------------|------------------------|--------------------------------|-----------------|  
|*Projname*.hpj|*Projname*\hlp|源文件|帮助编译器用于创建你的程序或控件的帮助文件的项目文件。|  
|*Projname*.rtf|*Projname*\hlp|项目|包含模板主题，你可以编辑和自定义.hpj 文件信息。|  
|Makehelp.bat|*Projname*|源文件|系统使用它来编译项目时生成的帮助项目。|  
|Bullet.bmp|*Projname*|资源文件|使用标准的帮助文件主题来表示项目符号列表。|  
  
## <a name="see-also"></a>请参阅  
 [为 Visual C++ 项目创建的文件类型](../ide/file-types-created-for-visual-cpp-projects.md)