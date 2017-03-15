---
title: "自动链接 MFC 库版本 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "defaultlib"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "自动链接 [C++]"
  - "MFC 中的 defaultlib"
  - "链接 [C++]"
  - "链接 [C++], MFC 库版本的自动化"
  - "链接 [C++], MFC"
  - "MFC 库, 链接到"
  - "MFC 库, 版本"
ms.assetid: 02af4a20-2034-4fce-b200-c2202c3c8311
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 自动链接 MFC 库版本
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在 MFC 版本在 3.0 版之前 \(在 Visual C\+\+ 2.0 版之前，在库输入列表必须手动指定的 MFC 库的正确版本。链接器。  MFC 3.0 版及之后，手动指定的 MFC 库版本不再是必需的。  而是由 MFC 头文件基于预处理器定义为`#define`（如 **\_DEBUG** 或 **\_UNICODE**）自动确定要链接到的 MFC 库的正确版本。  MFC 头文件添加 **\/defaultlib**指令来指示链接器链接到特定的 MFC 库版本中。  
  
 例如，下面的代码片段 AFX.H 从 MFC 头文件中 NAFXCW.LIB NAFXCWD.LIB 或版本指示链接器链接，具体取决于是使用 MFC 调试版本：  
  
 `#ifndef _UNICODE`  
  
 `#ifdef _DEBUG`  
  
 `#pragma comment(lib, "nafxcwd.lib")`  
  
 `#else`  
  
 `#pragma comment(lib, "nafxcw.lib")`  
  
 `#endif`  
  
 `#else`  
  
 `#ifdef _DEBUG`  
  
 `#pragma comment(lib, "uafxcwd.lib")`  
  
 `#else`  
  
 `#pragma comment(lib, "uafxcw.lib")`  
  
 `#endif`  
  
 `#endif`  
  
 MFC 头文件中所需的任何库的链接，包括 MFC 库，Win32 库，OLE 库，请从示例生成的 OLE 库，ODBC 库，依此类推。  包含 Win32 Kernel32.Lib 库、User32.Lib 和 GDI32.Lib。  
  
## 请参阅  
 [MFC 库版本](../mfc/mfc-library-versions.md)