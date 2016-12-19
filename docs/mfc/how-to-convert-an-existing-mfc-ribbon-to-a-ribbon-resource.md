---
title: "如何：将现有 MFC 功能区转换为功能区资源 | Microsoft Docs"
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
  - "MFC 功能区, 转换为功能区资源"
  - "功能区资源, 从 MFC 功能区转换"
ms.assetid: 324b7ff6-58f9-4691-96a9-9836a79d0fb6
caps.latest.revision: 8
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：将现有 MFC 功能区转换为功能区资源
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

功能区资源比手动代码的功能区是简单直观，修改和维护。  本主题描述如何将一个 MFC 项目中的手动代码的功能区转换到功能区资源。  
  
 必须有使用 MFC 功能区类的现有 MFC 项目代码，例如，[CMFCRibbonBar 类](../mfc/reference/cmfcribbonbar-class.md)。  
  
### 将MFC 功能区转换为一个功能区资源  
  
1.  在 Visual Studio 中，在现有的 MFC 项目，打开 CMFCRibbonBar 对象初始化的源文件。  通常，文件是 mainfrm.cpp。  在功能区的初始化代码之后添加以下代码。  
  
    ```  
    m_wndRibbonBar.SaveToXMLFile("RibbonOutput.xml");  
    ```  
  
     保存并关闭文件。  
  
2.  生成并运行应用 MFC 程序，然后在记事本打开 RibbonOutput.txt，并复制其内容。  
  
3.  在 Visual Studio 中，在 项目 菜单上，单击 添加资源。  在“添加资源”对话框中，选择功能区，再单击新建。  
  
     Visual Studio 会创建一个功能资源并在设计试图中打开此文件。  功能资源ID是IDR\_RIBBON1，这是显示在资源视图。  功能区在ribbon1.mfcribbon MS XML 文件中定义。  
  
4.  在 Visual Studio 中，打开 ribbon1.mfcribbon MS，删除其内容，然后粘贴先前复制的 RibbonOutput.txt 的内容。  保存并关闭 ribbon1.mfcribbon MS。  
  
5.  再次打开 CMFCRibbonBar 对象初始化的源文件 \(通常，mainfrm.cpp\) 和注释掉现有的功能区代码。  在注释掉的代码之后添加以下代码。  
  
    ```  
    m_wndRibbonBar.LoadFromResource(IDR_RIBBON1);  
    ```  
  
6.  生成项目并运行应用程序。  
  
## 请参阅  
 [功能区设计器 \(MFC\)](../mfc/ribbon-designer-mfc.md)