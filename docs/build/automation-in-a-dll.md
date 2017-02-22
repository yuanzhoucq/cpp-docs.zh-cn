---
title: "DLL 中的自动化 | Microsoft Docs"
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
  - "本机 [C++], DLL"
  - "DLL [C++], 自动化"
ms.assetid: 2728ecd1-14e2-4ae0-a946-e749e11dbb74
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# DLL 中的自动化
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

当在“MFC DLL 向导”中选择“自动化”选项时，向导为您提供下列内容：  
  
-   起始对象描述语言 \(.ODL\) 文件  
  
-   STDAFX.h 文件中面向 Afxole.h 的 include 指令  
  
-   `DllGetClassObject` 函数的实现，此函数调用 **AfxDllGetClassObject** 函数  
  
-   `DllCanUnloadNow` 函数的实现，此函数调用 **AfxDllCanUnloadNow** 函数  
  
-   `DllRegisterServer` 函数的实现，此函数调用 [COleObjectFactory::UpdateRegistryAll](../Topic/COleObjectFactory::UpdateRegistryAll.md) 函数  
  
## 您想进一步了解什么？  
  
-   [自动化服务器](../mfc/automation-servers.md)  
  
## 请参阅  
 [Visual C\+\+ 中的 DLL](../build/dlls-in-visual-cpp.md)