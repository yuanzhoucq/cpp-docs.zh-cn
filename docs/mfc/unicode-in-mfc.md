---
title: "MFC 中的 Unicode | Microsoft Docs"
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
  - "字符串 [C++], Unicode"
  - "Unicode [C++], 启用"
  - "Unicode [C++], MFC"
  - "宽字符, 编码"
  - "宽字符, Unicode"
ms.assetid: 1002004b-4113-4380-bf63-e1570934b793
caps.latest.revision: 13
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC 中的 Unicode
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述 MFC 对在 Windows NT、Windows 2000 和 Windows XP 平台上编码宽字符的 Unicode 标准的支持。  Unicode 应用程序在 Windows 98 平台不能运行。  
  
 MFC 库的 Unicode 版本介绍：  
  
### 静态连接库。  
  
|Release|调试|说明|  
|-------------|--------|--------|  
|UAFXCW.lib，.pdb|UAFXCWD.lib，.pdb|Unicode MFC 静态链接库|  
  
### 动态链接库  
  
|Release|调试|说明|  
|-------------|--------|--------|  
|MFC100U.lib, .dbg, def, .dll, .map, .pdb, .prf|MFC100UD.lib, .def, .dll, .map, .pdb|Unicode MFC 导入库 \(文件扩展的说明。请参见下面的说明\)|  
|MFCS100U.lib, .pdb|MFCS100UD.lib, .pdb|Unicode MFC导入库包含应用程序或 DLL 必须静态链接的代码|  
  
 **文件类型**  
  
-   导入扩展库文件 \(.lib\)。  
  
-   动态链接库文件扩展 \(.dll\)。  
  
-   模块定义 \(.def\) 文件是包含定义的 .exe 或 .dll 语句的文本文件。  
  
-   映射 \(.map\) 文件是包含有关当链接程序时链接器使用信息的文本文件。  
  
-   库 \(.LIB\) 文件与 MFC DLL 版本一起使用。  这些文件包含应用程序或 DLL 静态链接必须的代码。  
  
-   程序数据库 \(.pdb\) 文件中包含调试和项目状态信息。  
  
-   调试 \(.dbg\) 文件包含 Visual C\+\+ 调试器使用的信息 \(FPO 和 COFF CodeView\)。  
  
 关于命名约定的详细信息，请参见 [库命名约定](../mfc/library-naming-conventions.md)。  
  
 有关使用的 MFC Unicode 的信息，请参见 [字符串：Unicode 和多字节字符集 \(MBCS\) 支持](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)。  
  
## 请参阅  
 [概念](../mfc/mfc-concepts.md)   
 [常规 MFC 主题](../mfc/general-mfc-topics.md)