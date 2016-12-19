---
title: "ATL 向导添加的 ATL 支持的详细信息 | Microsoft Docs"
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
  - "vc.codewiz.atl.support"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL, MFC 项目"
  - "MFC, ATL 支持"
ms.assetid: aa66bad0-008f-4886-94c1-2a0a0d04bce4
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ATL 向导添加的 ATL 支持的详细信息
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

当[向已有 MFC 可执行文件或 DLL 添加 ATL 支持](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)时，Visual C\+\+ 对现有 MFC 项目做如下修改（此例中，项目称为 `MFCEXE`）：  
  
-   添加两个新文件（.idl 文件和 .rgs 文件，用于注册服务器）。  
  
-   在主应用程序头文件和实现文件（Mfcexe.h 和 Mfcexe.cpp）中添加一个新类（从 **CAtlMFCModule** 导出）。  除了此新类外，还向 `InitInstance` 中添加注册用的代码。  还向 `ExitInstance` 函数中添加用于撤消类对象的代码。  最后，在实现文件中包括头文件中的两个新头文件（Initguid.h 和 Mfcexe\_i.c），声明并初始化 **CAtlMFCModule** 导出类的新 GUID。  
  
-   为正确注册服务器，向项目的资源文件中添加新 .rgs 文件的项。  
  
## DLL 项目注意事项  
 向 MFC DLL 项目添加 ATL 支持时，将会发现有些差异。  向 **DLLRegisterServer** 和 **DLLUnregisterServer** 函数中添加用于注册和注销 DLL 的代码。  还向 [DllCanUnloadNow](../Topic/CAtlDllModuleT::DllCanUnloadNow.md) 和 [DllGetClassObject](../Topic/CAtlDllModuleT::DllGetClassObject.md) 中添加代码。  
  
## 请参阅  
 [MFC 项目中的 ATL 支持](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)   
 [用代码向导添加功能](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [添加类](../../ide/adding-a-class-visual-cpp.md)   
 [添加成员函数](../../ide/adding-a-member-function-visual-cpp.md)   
 [添加成员变量](../../ide/adding-a-member-variable-visual-cpp.md)   
 [重写虚函数](../../ide/overriding-a-virtual-function-visual-cpp.md)   
 [MFC 消息处理程序](../../mfc/reference/adding-an-mfc-message-handler.md)   
 [导航类结构](../../ide/navigating-the-class-structure-visual-cpp.md)