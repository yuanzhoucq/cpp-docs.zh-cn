---
title: "MFC 应用程序中的本地化资源：附属 DLL | Microsoft Docs"
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
  - "DLL [C++], 本地化 MFC"
  - "本地化 [C++], MFC 资源"
  - "本地化资源 [C++]"
  - "MFC DLL [C++], 本地化"
  - "多语言支持 [C++]"
  - "纯资源 DLL [C++]"
  - "纯资源 DLL [C++], MFC 应用程序"
  - "资源 [MFC], 本地化"
  - "附属 DLL [C++]"
ms.assetid: 3a1100ae-a9c8-47b5-adbd-cbedef5992ef
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# MFC 应用程序中的本地化资源：附属 DLL
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC 7.0 及更高版本提供对附属 DLL 的增强支持，该功能有助于创建针对多种语言进行本地化的应用程序。  附属 DLL 是一个[纯资源 DLL](../build/creating-a-resource-only-dll.md)，它包含应用程序的针对特定语言进行本地化的资源。  当应用程序开始执行时，MFC 自动加载最适合于环境的本地化资源。  例如，可能有一个具有英语语言资源的应用程序，该应用程序还有两个附属 DLL，其中一个包含资源的法语译本，另一个包含资源的德语译本。  当该应用程序在英语语言系统上运行时，它使用英语资源。  如果在法语系统上运行，则它使用法语资源；如果在德语系统上运行，则使用德语资源。  
  
 为了支持 MFC 应用程序中的本地化资源，MFC 尝试加载一个附属 DLL，它包含本地化为特定语言的资源。  附属 DLL 被命名为 *ApplicationNameXXX*.dll，其中 *ApplicationName* 是使用 MFC 的 .exe 或 .dll 的名称，而 *XXX* 是资源语言的由三个字母组成的代码（例如，“ENU”或“DEU”）。  
  
 MFC 尝试按顺序加载下列每种语言的资源 DLL，当找到一个时停止：  
  
1.  （仅适用于 Windows 2000 或更高版本）当前用户的默认用户界面语言，该语言从 GetUserDefaultUILanguage\(\) Win32 API 返回。  
  
2.  （仅适用于 Windows 2000 或更高版本）当前用户的默认用户界面语言，没有任何特定的次语言（也就是说，ENC \[加拿大英语\] 变为 ENU \[美国  英语\]）。  
  
3.  系统的默认用户界面语言。  在 Windows 2000 或更高版本上，这是从 GetSystemDefaultUILanguage\(\) API 返回的语言。  在其他平台上，这是操作系统本身的语言。  
  
4.  系统的默认用户界面语言，没有任何特定的次语言。  
  
5.  具有 3 字母代码 LOC 的“虚设”语言。  
  
 如果 MFC 未找到任何附属 DLL，则它使用包含在应用程序本身中的任何资源。  
  
 作为示例，假设应用程序 LangExample.exe 使用 MFC 并且正在 Windows 2000 多用户界面系统上运行；系统的用户界面语言是 ENU \[美国  英语\] 并且当前用户的用户界面语言设置为 FRC \[加拿大法语\]。  MFC 将按下面的顺序查找下面的 DLL：  
  
1.  LangExampleFRC.dll（用户的用户界面语言）。  
  
2.  LangExampleFRA.dll（用户的用户界面语言，不带次语言；在此示例中为法语（法国））。  
  
3.  LangExampleENU.dll（系统的用户界面语言）。  
  
4.  LangExampleLOC.dll。  
  
 如果没找到这些 DLL 中的任何一个，则 MFC 使用 LangExample.exe 中的资源。  
  
## 请参阅  
 [Visual C\+\+ 中的 DLL](../build/dlls-in-visual-cpp.md)   
 [TN057：MFC 组件的本地化](../mfc/tn057-localization-of-mfc-components.md)