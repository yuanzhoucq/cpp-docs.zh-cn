---
title: "AFXDLL 版本 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "afxdll"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AFXDLL 库"
  - "应用程序向导 [C++], 默认使用 AFXDLL"
  - "MFC 的 DLL 版本 [C++]"
  - "MFC [C++], AFXDLL 版本"
  - "MFC DLL [C++], 动态链接到库文件"
  - "MFC 库 [C++], 动态链接"
ms.assetid: c078ae8f-85a9-43cb-9ded-c09ca2c45723
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# AFXDLL 版本
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

除了生成应用程序通过静态链接到 MFC 对象代码库，您可以生成应用程序使用一 AFXDLL 库，在 MFC DLL 包含多个连续应用程序中共享。  AFXDLL 有关表名称，请参见 [DLL:命名约定](../build/naming-conventions-for-mfc-dlls.md)。  
  
> [!NOTE]
>  默认情况下，" MFC 应用程序向导"创建。AFXDLL 项目  若要将 MFC 代码的静态链接，请设置在 MFC 应用程序向导的 **在静态库中使用 MFC\(E\)** 选项。  静态链接不在 Visual C\+\+ 标准版。  
  
## 请参阅  
 [MFC 库版本](../mfc/mfc-library-versions.md)