---
title: "Windows Vista 公共控件的生成要求 | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
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
  - "公共控件 (MFC)"
  - "公共控件 (MFC), 生成要求"
ms.assetid: 025f7d55-55a2-4dcd-8f62-02424e3dcc04
caps.latest.revision: 18
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Windows Vista 公共控件的生成要求
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Microsoft 基础类 \(MFC\) \(MFC\) 库支持 Windows 公共控件版本 6.1。  公共控件在 [!INCLUDE[windowsver](../build/reference/includes/windowsver_md.md)] 中，该库包括在 [!INCLUDE[vsipsdk](../mfc/includes/vsipsdk_md.md)]中。  库提供引发现有类中的新方法并支持 [!INCLUDE[windowsver](../build/reference/includes/windowsver_md.md)] 公共控件的新的类和方法。  在生成应用程序时，应该按照下一节中介绍的编译和迁移要求。  
  
## 汇编要求  
  
### 支持的版本  
 尽管其他方法支持以前的操作系统，有些新的类和方法仅支持 [!INCLUDE[windowsver](../build/reference/includes/windowsver_md.md)] 和更高版本。  在每个方法主题中的 `Requirements` 一节的说明指定最低要求时的操作系统是 [!INCLUDE[windowsver](../build/reference/includes/windowsver_md.md)]。  
  
 即使计算机不在运行 [!INCLUDE[windowsver](../build/reference/includes/windowsver_md.md)]，则可在 [!INCLUDE[windowsver](../build/reference/includes/windowsver_md.md)] 中运行的应用 MFC 程序，如果您具有的计算机上版本 6.1 MFC 头文件。  但是，用于 [!INCLUDE[windowsver](../build/reference/includes/windowsver_md.md)] 而专门设计了常用控件在该系统仅运行和由以前的操作系统上忽略。  
  
### 支持的字符集  
 新 Windows 公共控件仅支持 Unicode 字符集而不是 ANSI 字符集。  如果在命令行中生成应用程序，请使用以下两个定义 \(\/D\) 编译器选项指定 Unicode 字符集为基础：  
  
```  
/D_UNICODE /DUNICODE  
```  
  
 如果您在 Visual Studio 集成开发环境 \(IDE\) \(IDE\) 的应用程序，指定 **Unicode 字符集** 选项 **字符集** 属性。**常规** 节点项目属性。  
  
 几个 MFC 方法 ANSI 版本为否决的开始使用 Windows 公共控件版本 6.1。  有关详细信息，请参阅[弃用的 ANSI API](../mfc/deprecated-ansi-apis.md)。  
  
## 迁移要求  
 如果您使用 Visual Studio IDE 生成使用 Windows 公共控件版本 6.1 的新 MFC 应用程序上时，IDE 将自动声明适当的清单。  但是，迁移，如果您从早期版本的 Visual Studio 的一个现有 MFC 应用程序，而且您要使用新的公共控件，IDE 不会自动提供截然不同信息升级应用程序。  相反，必须手动插入在 stdafx.h 文件的以下源代码：  
  
```  
#ifdef UNICODE  
#if defined _M_IX86  
#pragma comment(linker,"/manifestdependency:\"type='win32' name='Microsoft.Windows.Common-Controls' version='6.0.0.0' processorArchitecture='x86' publicKeyToken='6595b64144ccf1df' language='*'\"")  
#elif defined _M_IA64  
#pragma comment(linker,"/manifestdependency:\"type='win32' name='Microsoft.Windows.Common-Controls' version='6.0.0.0' processorArchitecture='ia64' publicKeyToken='6595b64144ccf1df' language='*'\"")  
#elif defined _M_X64  
#pragma comment(linker,"/manifestdependency:\"type='win32' name='Microsoft.Windows.Common-Controls' version='6.0.0.0' processorArchitecture='amd64' publicKeyToken='6595b64144ccf1df' language='*'\"")  
#else  
#pragma comment(linker,"/manifestdependency:\"type='win32' name='Microsoft.Windows.Common-Controls' version='6.0.0.0' processorArchitecture='*' publicKeyToken='6595b64144ccf1df' language='*'\"")  
#endif  
#endif  
```  
  
## 请参阅  
 [常规 MFC 主题](../mfc/general-mfc-topics.md)   
 [层次结构图](../mfc/hierarchy-chart.md)   
 [弃用的 ANSI API](../mfc/deprecated-ansi-apis.md)