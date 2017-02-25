---
title: "MFC DLL 向导生成的类和函数 | Microsoft Docs"
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
  - "类 [C++], 由 MFC DLL 向导生成"
  - "代码 [C++], 由 MFC DLL 向导生成"
  - "DLL [C++], 向导类和函数"
  - "函数 [MFC]"
  - "函数 [MFC], DLL"
  - "MFC DLL 向导"
ms.assetid: e69e62fe-4953-42bf-a2fc-50bbf9bdaeaf
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# MFC DLL 向导生成的类和函数
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

MFC DLL 向导生成的代码取决于正在创建的 DLL 类型和选择的选项。  MFC DLL 向导为两种形式的规则 DLL 生成相同的代码。  
  
|DLL 类型|选项|类|函数|  
|------------|--------|-------|--------|  
|[扩展名](../../build/extension-dlls-overview.md)|无|无|`DllMain`|  
|[规则](../../build/regular-dlls-dynamically-linked-to-mfc.md)|无|从 `CWinApp` 派生的应用程序类|无|  
|[规则](../../build/regular-dlls-dynamically-linked-to-mfc.md)|自动化|从 `CWinApp` 派生的应用程序类|**DllGetClassObjectDllCanUnloadNowDllRegisterServer**|  
|[扩展名](../../build/extension-dlls-overview.md)|Windows 套接字|无|`DllMain`|  
|[规则](../../build/regular-dlls-dynamically-linked-to-mfc.md)|Windows 套接字|从 `CWinApp` 派生的应用程序类|`InitInstance` 包含对 `AfxSocketInit` 的调用。|  
  
## 请参阅  
 [MFC DLL 向导](../../mfc/reference/mfc-dll-wizard.md)