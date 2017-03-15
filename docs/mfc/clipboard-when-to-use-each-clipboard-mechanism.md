---
title: "剪贴板：何时使用每一剪贴板机制 | Microsoft Docs"
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
  - "应用程序 [OLE], 剪贴板"
  - "剪贴板 [C++], 格式"
  - "剪贴板 [C++], 机制"
  - "格式 [C++], OLE 剪贴板"
  - "OLE 剪贴板, 格式"
  - "OLE 剪贴板, 指南"
ms.assetid: fd071996-ef8c-488b-81bd-89057095a201
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 剪贴板：何时使用每一剪贴板机制
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

遵循使用了剪贴板的准则：  
  
-   现在使用 OLE 剪贴板机制在以后启用新功能。  当标准剪贴板 API 将维护时，OLE 机制是将来数据传输。  
  
-   使用 OLE 剪贴板机制，则编写 OLE 应用程序或需要任何 OLE 拖放功能，如。  
  
-   如果提供 OLE 格式，请使用 OLE 剪贴板机制。  
  
## 你希望做什么？  
  
-   [使用 OLE 剪贴板机制](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)  
  
-   [使用 Windows 剪贴板机制](../mfc/clipboard-using-the-windows-clipboard.md)  
  
## 请参阅  
 [剪贴板](../mfc/clipboard.md)