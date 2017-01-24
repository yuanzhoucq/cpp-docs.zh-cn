---
title: "常规类设计理念 | Microsoft Docs"
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
  - "vc.classes.mfc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "类 [C++], MFC 类设计"
  - "设计类"
  - "MFC [C++], Windows API"
  - "Visual C, Windows API 调用"
  - "Windows API [C++], 和 MFC"
ms.assetid: e6861ae0-1581-4d9c-9ddf-63f9afcdb913
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 常规类设计理念
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

C\+\+ 语言，然后变为常见之前，Microsoft Windows 中设计。  由于、千位应用程序使用 C 语言 Windows 应用程序编程接口 \(API\) \(API\)，该接口会维护的可预见到的将来：for}}。  生成必须因此所有 C\+\+ Windows 接口位于程序 C 语言 API 的顶部。  这保证 C\+\+ 应用程序可以同时包含 C\# 应用程序。  
  
 Microsoft 基础类库是实现以下设计目标的一种面向对象的接口向窗口：  
  
-   对工作的显著降低编写对于 Windows 的应用程序。  
  
-   执行速度比与 C 语言 API。  
  
-   最少的编码规范开销。  
  
-   可以直接调用任何 Windows C 函数。  
  
-   现有的 C\# 应用程序更易于进行转换为 C\+\+。  
  
-   能否从 C 语言现有窗口的基本编程体验的使用。  
  
-   使用用 C\+\+ 的 Windows API 的更简单的使用相对于使用 C\#。  
  
-   更易于使用，复杂的强大功能的抽象 \(如 ActiveX 控件、数据库支持、打印、工具栏和状态栏。  
  
-   为有效使用 C\+\+ 语言功能的 C\+\+ Windows API。  
  
 有关更多在 MFC 库的设计，请参见：  
  
-   [应用程序框架](../mfc/application-framework.md)  
  
-   [对 C 语言 API 的关系](../mfc/relationship-to-the-c-language-api.md)  
  
## 请参阅  
 [类概述](../mfc/class-library-overview.md)