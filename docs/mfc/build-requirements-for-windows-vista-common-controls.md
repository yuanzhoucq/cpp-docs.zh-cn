---
title: "Windows Vista 公共控件的生成要求 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- common controls (MFC), build requirements
- common controls (MFC)
ms.assetid: 025f7d55-55a2-4dcd-8f62-02424e3dcc04
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 76919bcdd416ed7195e94ed1fa0b2e3f3a4d573d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="build-requirements-for-windows-vista-common-controls"></a>Windows Vista 公共控件的生成需求
Microsoft 基础类 (MFC) 库支持 Windows 公共控件版本 6.1。 公共控件包含在 [!INCLUDE[windowsver](../build/reference/includes/windowsver_md.md)] 中，该库包含在 [!INCLUDE[vsipsdk](../mfc/includes/vsipsdk_md.md)]中。 库提供了增强现有类和新类的新方法和支持的方法[!INCLUDE[windowsver](../build/reference/includes/windowsver_md.md)]公共控件。 在生成应用程序时，应该遵循后续章节中所述的编译和迁移需求。  
  
## <a name="compilation-requirements"></a>编译要求  
  
### <a name="supported-versions"></a>支持的版本  
 某些新的类和方法仅支持 [!INCLUDE[windowsver](../build/reference/includes/windowsver_md.md)] 和更高版本，但其他方法还支持早期版本的操作系统。 每个方法主题的 `Requirements` 节中的注释指明了在哪些情况下所需的最低操作系统版本是 [!INCLUDE[windowsver](../build/reference/includes/windowsver_md.md)]。  
  
 即使你的计算机不会运行[!INCLUDE[windowsver](../build/reference/includes/windowsver_md.md)]，你可以生成 MFC 应用程序将在上运行[!INCLUDE[windowsver](../build/reference/includes/windowsver_md.md)]如果你有您的计算机上的 6.1 版 MFC 标头文件。 但是，公共控件，专为[!INCLUDE[windowsver](../build/reference/includes/windowsver_md.md)]操作仅在该系统上，并忽略较早的操作系统。  
  
### <a name="supported-character-sets"></a>支持的字符集  
 新 Windows 公共控件仅支持 Unicode 字符集，不支持 ANSI 字符集。 如果您在命令行中生成应用程序，请使用以下两个 define (/D) 编译器选项指定 Unicode 字符集作为基础字符集：  
  
```  
/D_UNICODE /DUNICODE  
```  
  
 如果你生成应用程序在 Visual Studio 集成的开发环境 (IDE) 中，指定**Unicode 字符集**选项**字符集**中的属性**常规**项目属性的节点。  
  
 从 Windows 公共控件 6.1 版开始，某些 MFC 方法的 ANSI 版本已被弃用。 有关详细信息，请参阅[弃用的 ANSI Api](../mfc/deprecated-ansi-apis.md)。  
  
## <a name="migration-requirements"></a>迁移需求  
 如果您使用 Visual Studio IDE 生成使用 Windows 公共控件 6.1 版的新 MFC 应用程序，IDE 将自动声明适当的清单。 但是，如果您从早期版本的 Visual Studio 迁移到现有 MFC 应用程序，并且您要使用新的公共控件，IDE 不会自动提供用来升级应用程序清单信息。 相反，你必须在 stdafx.h 文件中手动插入以下源代码：  
  
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
  
## <a name="see-also"></a>请参阅  
 [常规 MFC 主题](../mfc/general-mfc-topics.md)   
 [层次结构图](../mfc/hierarchy-chart.md)   
 [弃用的 ANSI API](../mfc/deprecated-ansi-apis.md)

