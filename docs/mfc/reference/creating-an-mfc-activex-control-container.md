---
title: "创建 MFC ActiveX 控件容器 | Microsoft Docs"
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
  - "vc.appwiz.activex.container"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActiveX 控件容器 [C++], 创建"
  - "容器 [C++], 创建"
  - "MFC ActiveX 控件 [C++], 容器"
  - "OLE 控件 [C++], 容器"
ms.assetid: ec70e137-7c14-4940-bd0e-fd4edcc63ea5
caps.latest.revision: 8
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 创建 MFC ActiveX 控件容器
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

ActiveX 控件容器是为 ActiveX（原来为 OLE）控件提供运行环境的父程序。  可以使用或者不使用 MFC 来创建能够包含 ActiveX 控件的应用程序，但如果使用 MFC 来创建会容易得多。  
  
 使用 [MFC 应用程序向导](../../mfc/reference/mfc-application-wizard.md)创建 MFC 容器程序时，可以访问 MFC 和 ActiveX 类实现的 ActiveX 控件和自动化的许多功能。  这些功能包括可视化编辑、自动化、创建复合文件和对控件的支持。  父程序支持的 MFC 应用程序向导可视化编辑选项包括：创建容器，创建袖珍服务器，创建完全服务器，以及创建既是容器又是服务器的程序。  
  
-   “新的 MFC 应用程序”。  若要创建包括自动化、可视化编辑、复合文件或控件支持的新 MFC 程序，请使用 MFC 应用程序向导并选择适当的自动化选项。  
  
-   “现有的 MFC 应用程序”。  如果将控件包容添加到现有的 MFC 应用程序，请参见 [OLE 控件容器：手动启用 OLE 控件包容](../../mfc/activex-control-containers-manually-enabling-activex-control-containment.md)。  
  
### 为下列任何类型的应用程序创建 ActiveX 容器  
  
1.  [容器](../../mfc/containers.md)  
  
2.  [可视化编辑](../../mfc/ole-mfc.md)  
  
3.  [MFC ActiveX 控件](../../mfc/mfc-activex-controls.md)  
  
## 请参阅  
 [Visual C\+\+ 项目类型](../../ide/visual-cpp-project-types.md)