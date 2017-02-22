---
title: "ActiveX 控件容器：手动启用 ActiveX 控件包含 | Microsoft Docs"
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
  - "ActiveX 控件容器 [C++], 启用"
  - "ActiveX 控件 [C++], 启用容器"
  - "AfxEnableControlContainer 函数"
ms.assetid: 833bcde9-c9ad-4709-ad12-2fc2150fb6a5
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# ActiveX 控件容器：手动启用 ActiveX 控件包含
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果未启用 ActiveX 控件支持，在使用 MFC 应用程序向导生成应用程序，您必须将手动添加此支持。  本文介绍手动添加的 ActiveX 控件包容过程到现有的 OLE 容器应用程序。  如果您事先知道希望在的容器 ActiveX 控件，请参见 OLE 支持文章 [创建 MFC ActiveX 控件容器](../mfc/reference/creating-an-mfc-activex-control-container.md)。  
  
> [!NOTE]
>  本文中的过程和代码使用一个基于对话框的 ActiveX 控件容器项目命名的容器和作为示例中名为的 Circ 嵌入的控件。  
  
 若要支持 ActiveX 控件，则必须将一行代码添加两个项目文件。  
  
-   通过调用的 MFC 应用程序向导修改主对话框的 `InitInstance` 函数 \(位于 CONTAINER.CPP 到 [AfxEnableControlContainer](../Topic/AfxEnableControlContainer.md)\)，如下面的示例所示：  
  
     [!code-cpp[NVC_MFCOleContainer#34](../mfc/codesnippet/CPP/activex-control-containers-manually-enabling-activex-control-containment_1.cpp)]  
    [!code-cpp[NVC_MFCOleContainer#35](../mfc/codesnippet/CPP/activex-control-containers-manually-enabling-activex-control-containment_2.cpp)]  
  
-   将以下代码添加到项目的 STDAFX.H 头文件：  
  
     [!code-cpp[NVC_MFCOleContainer#36](../mfc/codesnippet/CPP/activex-control-containers-manually-enabling-activex-control-containment_3.h)]  
  
 在完成这些步骤后，通过单击 **生成** 重新生成项目。**生成** 菜单。  
  
## 请参阅  
 [ActiveX 控件容器](../mfc/activex-control-containers.md)