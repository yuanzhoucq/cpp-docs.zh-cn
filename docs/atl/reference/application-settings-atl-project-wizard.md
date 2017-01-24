---
title: "应用程序设置，ATL 项目向导 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "vc.appwiz.atl.com.appset"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL 项目向导，应用程序设置"
ms.assetid: d48c9fc5-f439-49fd-884c-8bcfa7d52991
caps.latest.revision: 17
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 应用程序设置，ATL 项目向导
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用 ATL 项目向导的**“应用程序设置”**页为新的 ATL 项目设计和添加基本功能。  
  
## 服务器类型  
 从三种服务器类型中选择一种：  
  
 **动态链接库 \(DLL\)**  
 选择以创建进程内服务器。  
  
 **可执行文件 \(EXE\)**  
 选择以创建本地进程外服务器。  此选项不允许 MFC 或 COM\+ 1.0 支持。  它不允许合并代理\/存根 \(stub\) 代码。  
  
 **服务 \(EXE\)**  
 选择以创建当 Windows 启动时在后台运行的 Windows 应用程序。  此选项不允许 MFC 或 COM\+ 1.0 支持，也不允许合并代理\/存根 \(stub\) 代码。  
  
## 附加选项  
  
> [!NOTE]
>  所有的附加选项仅适用于 DLL 项目。  
  
 **允许合并代理\/存根\(stub\)代码**  
 选中**“允许合并代理\/存根\(stub\)代码”**复选框可在需要封送处理接口时提供方便。  此选项在与服务器相同的可执行文件中放置 MIDL 生成的代理和存根 \(stub\) 代码。  
  
 **支持 MFC**  
 选择以指定对象包含 MFC 支持。  此选项将项目链接到 MFC 库，以便可以访问它们包含的任何类和函数。  
  
 **支持 COM\+ 1.0**  
 选择修改项目生成设置以支持 COM\+ 1.0 组件。  除标准库列表以外，向导还添加了 COM\+ 1.0 组件特定库 comsvcs.lib  
  
 另外，当启动应用程序时 mtxex.dll 在主系统上延迟加载。  
  
-   **支持部件注册器**，如果您的 ATL 项目包含用于支持 COM\+ 1.0 组件，可以设置此选项。  组件注册器使 COM\+ 1.0 对象得以获取组件列表、注册组件或注销组件（个别或同时）。  
  
## 请参阅  
 [ATL 项目向导](../../atl/reference/atl-project-wizard.md)   
 [创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)   
 [默认 ATL 项目配置](../../atl/reference/default-atl-project-configurations.md)