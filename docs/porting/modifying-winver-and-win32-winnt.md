---
title: "修改 WINVER 和 _WIN32_WINNT | Microsoft Docs"
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
  - "_WIN32_WINNT in an upgraded Visual C++ project"
  - "WINVER in an upgraded Visual C++ project"
ms.assetid: 6a1f1d66-ae0e-48a7-81c3-524d8e8f3447
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 17
---
# 修改 WINVER 和 _WIN32_WINNT
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Visual C\+\+ 不再支持面向 Windows 95、Windows 98、Windows ME、Windows NT 或 Windows 2000。 如果你的 **WINVER** 或 **\_WIN32\_WINNT** 宏分配给了这些 Windows 版本中的一个，则必须修改宏。 升级使用早期版本的 Visual C\+\+ 创建的项目时，你可能会看到与 **WINVER** 或 **\_WIN32\_WINNT** 宏相关的编译错误（如果这些宏分配给了不再受支持的 Windows 版本）。  
  
## 备注  
 若要修改这些宏，请在头文件（例如在创建面向 Windows 的项目时包含的 targetver.h）中添加以下行。  
  
```  
#define WINVER 0x0A00 #define _WIN32_WINNT 0x0A00  
```  
  
 这面向 Windows 10 操作系统。 在 Windows 头文件 SDKDDKVer.h（它还定义每个 Windows 版本的宏）中列出了这些值。 应添加 \#define 语句，然后才能包括 SDKDDKVer.h。 下面是 Windows 10 版 SDKDDKVer.h（它对每个版本的 Windows 的值进行编码）中的行：  
  
```  
// // _WIN32_WINNT version constants // #define _WIN32_WINNT_NT4                    0x0400 // Windows NT 4.0 #define _WIN32_WINNT_WIN2K                  0x0500 // Windows 2000 #define _WIN32_WINNT_WINXP                  0x0501 // Windows XP #define _WIN32_WINNT_WS03                   0x0502 // Windows Server 2003 #define _WIN32_WINNT_WIN6                   0x0600 // Windows Vista #define _WIN32_WINNT_VISTA                  0x0600 // Windows Vista #define _WIN32_WINNT_WS08                   0x0600 // Windows Server 2008 #define _WIN32_WINNT_LONGHORN               0x0600 // Windows Vista #define _WIN32_WINNT_WIN7                   0x0601 // Windows 7 #define _WIN32_WINNT_WIN8                   0x0602 // Windows 8 #define _WIN32_WINNT_WINBLUE                0x0603 // Windows 8.1 #define _WIN32_WINNT_WINTHRESHOLD           0x0A00 // Windows 10 #define _WIN32_WINNT_WIN10                  0x0A00 // Windows 10  
```  
  
 如果你查看的 SDKDDKVer.h 的一个副本中没有列出以上所有 Windows 版本，则很可能是由于你正在使用 Windows SDK 的较旧版本。 默认情况下，[!INCLUDE[vs_dev14](../ide/includes/vs_dev14_md.md)] 中的 Win32 项目使用 Windows 8.1 SDK。 若要使用 Windows 10 SDK，请参阅[如何：在 Windows 桌面应用程序中使用 Windows 10 SDK](../windows/how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)。  
  
> [!NOTE]
>  如果将内部 MFC 头文件包含到应用程序中，则无法保证这些值有效。  
  
 你还可以使用 **\/D** 编译器选项定义此宏。 有关详细信息，请参阅 [\/D（预处理器定义）](../build/reference/d-preprocessor-definitions.md)。  
  
 若要深入了解这些宏的含义，请参阅[使用 Windows 头文件](http://msdn.microsoft.com/library/windows/desktop/aa383745)。  
  
## 请参阅  
 [先前产品更改](http://msdn.microsoft.com/zh-cn/91fa1713-0778-4b6b-82f7-0fe0a23ab1db)