---
title: "动态链接库支持 | Microsoft Docs"
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
  - "DLL [C++], MFC"
  - "MFC DLL [C++], 规则 DLL"
  - "NAFXDW.LIB"
  - "NAFXDWD.LIB"
  - "规则 DLL [C++], 作为 DLL 的项目目标"
  - "USRDLL, DLL 支持"
ms.assetid: cc31c69f-3c78-4db1-9ecd-0fd8dc3217e3
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 动态链接库支持
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

NAFXCW.lib 和 NAFXCWD.lib 库 \(列出在静态链接库命名约定中 [库命名约定](../mfc/library-naming-conventions.md)的表\) 创建为动态链接库 \(DLL\)，调用可用于应用程序不使用生成类库的常规 DLL“”\(之前“USRDLL”\)。  此 DLL 支持与 MFCx0.dll 和 AFXDLL MFCx0D.DLL \(称为\)，该 DLL 包含整个类库。  有关详细信息，请参阅 [DLLs](../build/dlls-in-visual-cpp.md)。  有关 DLL 名称表，请参见 [MFC 的 DLL 命名约定](../build/naming-conventions-for-mfc-dlls.md)。  
  
## 请参阅  
 [MFC 库版本](../mfc/mfc-library-versions.md)