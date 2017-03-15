---
title: "使用合并模块重新发布组件 | Microsoft Docs"
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
  - "合并模块, using"
  - "重新分发应用程序, 使用合并模块"
ms.assetid: 93b84211-bf9b-4a78-9f22-474ac2ef7840
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# 使用合并模块重新发布组件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 包括获得许可要与应用程序一起重新发布的每个 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 组件的[合并模块](http://msdn.microsoft.com/library/aa367434)。  合并模块在 Windows Installer 安装文件中编译后，便可以将特定的 DLL 部署到具有特定平台的计算机。  在你的安装文件中，请指定合并模块是应用程序的先决条件。  [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 安装后，合并模块将安装在 \\Program Files\\Common Files\\Merge Modules\\ 中。（只能重新发布 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] DLL 的非调试版本。）有关更多信息以及许可重新发布的合并模块列表的链接，请参阅[重新分发 Visual C\+\+ 文件](../ide/redistributing-visual-cpp-files.md)。  
  
 你可以使用合并模块将可再发行的 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] DLL 安装到 %SYSTEMROOT%\\system32\\ 文件夹。（[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 本身使用此技术。）但是，安装的用户必须具有管理员权限才能成功安装到该文件夹。  
  
 除非你不必为应用程序提供服务并且不依赖于一个以上的 DLL 版本，否则我们建议你不要使用合并模块。  同一 DLL 的不同版本的合并模块不能包含在一个安装程序中，而且合并模块使你难以独立于应用程序为 DLL 服务。  因而我们建议你安装 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] Redistributable Package。  
  
## 请参阅  
 [重新分发 Visual C\+\+ 文件](../ide/redistributing-visual-cpp-files.md)