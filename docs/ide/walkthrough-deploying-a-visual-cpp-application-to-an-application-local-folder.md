---
title: "演练：将 Visual C++ 应用程序部署到应用程序本地文件夹 | Microsoft Docs"
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
  - "部署 Visual C++ 应用程序"
ms.assetid: 47a81c47-9dbe-47c6-96cc-fbb2fda5e6ad
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 演练：将 Visual C++ 应用程序部署到应用程序本地文件夹
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述如何通过复制文件部署 Visual C\+\+ 应用程序中的文件夹。  
  
## 系统必备  
  
-   安装 Visual Studio 的计算机。  
  
-   没有 Visual C\+\+ 库的另一台计算机。  
  
### 将应用程序部署到应用程序本地文件夹  
  
1.  按照中的步骤创建并生成 MFC 应用程序在 [演练：使用安装项目部署 Visual C\+\+ 应用程序](../ide/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project.md)。  
  
2.  复制相应的 MFC 和 C 运行时 \(CRT\) 库文件 \(例如，对于 x86 平台和 Unicode 在 \\MFC 项目的 release\\ 文件夹支持，复制 mfc100u.dll 和 msvcr100.dll 从 \\program files\\Microsoft Visual Studio 10.0\\VC\\redist\\x86\\—然后将它们粘贴。  有关其他文件的更多信息可能必须复制，请参见 [确定要重新分发的 DLL](../ide/determining-which-dlls-to-redistribute.md)。  
  
3.  运行在没有 Visual C\+\+ 库的另一台计算机上的 MFC 应用程序。  
  
    1.  将 \\release\\ 文件夹的内容并将其粘贴在第二台计算机上的应用程序文件夹。  
  
    2.  运行在第二台计算机上运行应用程序。  
  
     此应用程序运行成功，因为可以在应用程序本地文件夹中使用 Visual C\+\+ 库。  
  
## 请参阅  
 [部署示例](../ide/deployment-examples.md)