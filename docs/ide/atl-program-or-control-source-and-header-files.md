---
title: "ATL 程序或控件的源文件和头文件 | Microsoft Docs"
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
  - "文件类型 [C++], ATL 源和头"
ms.assetid: cb65372f-4880-4007-b582-a52eaa568fd1
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# ATL 程序或控件的源文件和头文件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

根据为创建的项目选择的选项，在 Visual Studio 中创建 ATL 项目时将创建下列文件。  
  
 所有这些文件都位于 *Projname* 目录中，而且位于解决方案资源管理器中的头文件（.h 文件）文件夹中或源文件（.cpp 文件）文件夹中。  
  
|文件名|说明|  
|---------|--------|  
|*Projname*.h|主包含文件，包含 ATLSample.idl 中定义的项的 C\+\+ 接口定义和 GUID 声明。  编译期间由 MIDL 重新生成。|  
|*Projname*.cpp|主程序源文件。  它包含进程内服务器的 DLL 导出实现和本地服务器的 `WinMain` 实现。  对于服务，它还实现所有服务管理函数。|  
|Resource.h|资源文件的头文件。|  
|StdAfx.cpp|包含 StdAfx.h 和 Atlimpl.cpp 文件|  
|StdAfx.h|包含 ATL 头文件。|  
  
## 请参阅  
 [为 Visual C\+\+ 项目创建的文件类型](../ide/file-types-created-for-visual-cpp-projects.md)   
 [MFC 程序或控件的源文件和头文件](../ide/mfc-program-or-control-source-and-header-files.md)   
 [CLR 项目](../ide/files-created-for-clr-projects.md)