---
title: "帮助文件（HTML 帮助） | Microsoft Docs"
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
  - "文件类型 [C++], HTML 帮助文件"
ms.assetid: d30a1b1b-318f-4a78-8b60-93da53a224a8
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 帮助文件（HTML 帮助）
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

当通过选择“区分上下文的帮助”复选框，然后在 MFC 应用程序向导的[高级功能](../mfc/reference/advanced-features-mfc-application-wizard.md)页中选择“HTML 帮助格式”，为应用程序添加 HTML 帮助类型的帮助支持时创建下列文件。  
  
|文件名|目录位置|解决方案资源管理器位置|说明|  
|---------|----------|-----------------|--------|  
|*Projname*.hhp|*Projname*\\hlp|HTML 帮助文件|帮助项目文件。  它包含将帮助文件编辑成 .hxs 文件或 .chm 文件所需的数据。|  
|*Projname*.hhk|*Projname*\\hlp|HTML 帮助文件|包含帮助主题索引。|  
|*Projname*.hhc|*Projname*\\hlp|HTML 帮助文件|帮助项目的内容。|  
|Makehtmlhelp.bat|*Projname*|源文件|由系统用来在编译项目时生成帮助项目。|  
|Afxcore.htm|*Projname*\\hlp|HTML 帮助主题|包含标准 MFC 命令和屏幕对象的标准帮助主题。  在此文件中添加您自己的帮助主题。|  
|Afxprint.htm|*Projname*\\hlp|HTML 帮助主题|包含打印命令的帮助主题。|  
|\*.jpg; \*.gif|*Projname*\\hlp\\Images|资源文件|包含生成的不同帮助文件主题的图像。|  
  
## 请参阅  
 [为 Visual C\+\+ 项目创建的文件类型](../ide/file-types-created-for-visual-cpp-projects.md)