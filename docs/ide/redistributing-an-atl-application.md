---
title: "重新分发 ATL 应用程序 | Microsoft Docs"
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
  - "ATL, 重新分发"
  - "OLE DB 模板, 重新分发"
  - "重新分发 ATL"
  - "重新分发 OLE DB 模板"
ms.assetid: 9a696b22-2345-43ec-826b-be7cb8cfd676
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 重新分发 ATL 应用程序
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

从 Visual Studio 2012 开始，活动模板库 \(ATL\) 是仅包含标头的库。  ATL 项目没有指向 ATL 选项的动态链接。  不需要任何可再发行 ATL 库。  
  
 如果再次发行 ATL 可执行应用程序，必须通过发出以下命令来注册 .exe 文件（以及它所包含的任何控件）：  
  
```  
filename /regserver  
  
```  
  
 其中，`filename` 是可执行文件的名称。  
  
 在 Visual Studio 2010 中，可以为 MinDependency 或 MinSize 配置生成 ATL 项目。  若将**“常规”**属性页上的**“ATL 的使用”**属性设置为**“静态链接到 ATL”**，并将**“代码生成”**属性页上的**“运行时库”**属性设置为**“多线程 \(\/MT\)”**（C\/C\+\+ 文件夹），则将获得 MinDependency 配置。  
  
 若将**“常规”**属性页上的**“ATL 的使用”**属性设置为**“动态链接到 ATL”**，或将**“代码生成”**属性页上的**“运行时库”**属性设置为**“多线程 DLL \(\/MD\)”**（C\/C\+\+ 文件夹），则将获得 MinSize 配置。  
  
 MinSize 使输出文件尽可能小，但要求在目标计算机上安装 ATL100.dll 和 msvcr100.dll（如果选择了**“多线程 DLL \(\/MD\)”**选项）。  应在目标计算机上注册 ATL100.dll，以确保具有所有 ATL 功能。  ATL100.dll 包含 ANSI 和 Unicode 导出。  
  
 针对 MinDependency 目标生成 ATL 或 OLE DB 模板项目时，不需要在目标计算机上安装和注册 ATL100.dll，尽管可能获得更大的程序映像。  
  
 对于 OLE DB 模板应用程序，确保目标计算机具有最新版本的 Microsoft 数据访问组件 \(MDAC\) 文件。  有关详细信息，请参阅[重新分发数据库支持文件](../ide/redistributing-database-support-files.md)。  
  
## 请参阅  
 [重新分发 Visual C\+\+ 文件](../ide/redistributing-visual-cpp-files.md)