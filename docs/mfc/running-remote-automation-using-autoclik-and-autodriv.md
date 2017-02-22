---
title: "使用 AUTOCLIK 和 AUTODRIV 运行远程自动化 | Microsoft Docs"
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
  - "AUTOCLIK 示例 [MFC]"
ms.assetid: 8900c0de-8dba-4f0a-8d9e-7db77a1f4f46
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 使用 AUTOCLIK 和 AUTODRIV 运行远程自动化
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

AUTOCLIK 可以用作基更多有关远程的自动化的简单自动化服务器示例应用程序。  AUTODRIV 示例是用来驱动 AUTOCLIK 示例的简单自动化客户端应用程序。  可以使用它们演示如何远程的自动化。  
  
#### 使用远程的自动化，安装在两台计算机的 AUTOCLIK.EXE 和驱动它  
  
1.  安装到开发计算机上的 [AUTOCLIK](../top/visual-cpp-samples.md) 示例应用程序。  
  
2.  生成 AUTOCLIK.EXE。  
  
3.  运行 AUTOCLIK.EXE 以独立方法然后关闭它。  这将注册该文件用作自动化服务器。  
  
4.  复制 AUTOCLIK.EXE 到远程计算机，因此运行它，然后将其关闭。  
  
5.  本地计算机上运行的 AUTODRIV.EXE 并验证运行它的一 AUTOCLIK.EXE 启动。  若要找出需要哪 AUTODRIV.EXE 更多信息，请参见 [AUTOCLIK](../top/visual-cpp-samples.md)。  
  
6.  在远程计算机上，启动 AUTMGR32.EXE \(自动化管理器\)。  
  
7.  在远程计算机上，启动镭 CMGR32 \(.EXE 远程的自动化管理器连接\)。  
  
8.  在远程连接自动化管理器中，从 **OLE Classes** 列表中选择 AutoClik.Document。  
  
9. 从 **Client Access** 选项卡选择系统安全策略授予对 AutoClik.Document 的客户端访问。  
  
10. 在本地计算机上，启动镭 CMGR32 .EXE 和选择的 AutoClik.Document 从 **OLE Classes** 列表中。  
  
11. 在 **服务器连接** 选项卡，选择远程计算机的网络地址并适当的网络协议。  
  
12. 在 **OLE Classes** 列表框仍选择的 AutoClik.Document，从 `Register` 菜单中选择 **远程** 命令。  
  
13. 在本地计算机、运行的 AUTODRIV.EXE 或等效的 AUTOCLIK.MAK Visual Basic 项目是否要让 Visual Basic，而不是 MFC，客户端。  
  
 在远程计算机，现在应查看 AUTOCLIK 执行命令所启动本地从的客户。  
  
## 请参阅  
 [远程自动化](../mfc/remote-automation.md)