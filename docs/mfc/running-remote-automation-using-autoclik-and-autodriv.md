---
title: "使用 AUTOCLIK 和 AUTODRIV 运行远程自动化 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- AUTOCLIK sample [MFC]
ms.assetid: 8900c0de-8dba-4f0a-8d9e-7db77a1f4f46
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 791655047eaf07732e1e006e8cc3ea8e7dec4727
ms.sourcegitcommit: fa7a6dccddce3747389c91277a53e296f905305c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="running-remote-automation-using-autoclik-and-autodriv"></a>使用 AUTOCLIK 和 AUTODRIV 运行远程自动化
AUTOCLIK 是简单的自动化服务器示例应用程序，您可将其用作通过其了解更多有关远程自动化的信息的基础。 AUTODRIV 是驱动 AUTOCLIK 的简单自动化客户端应用程序。 您可以使用它们演示远程自动化。  
  
#### <a name="to-install-autoclikexe-on-two-machines-and-drive-it-using-remote-automation"></a>在两台计算机上安装 AUTOCLIK.EXE 并使用远程自动化来驱动它  
  
1.  安装[AUTOCLIK](../visual-cpp-samples.md)示例应用程序部署到你的开发计算机。  
  
2.  生成 AUTOCLIK.EXE。  
  
3.  独立运行 AUTOCLIK.EXE，然后将其关闭。 这会将其注册为自动化服务器。  
  
4.  将 AUTOCLIK.EXE 复制到远程计算机，在此运行它，然后将其关闭。  
  
5.  在本地计算机上运行 AUTODRIV.EXE 并验证运行它是否会启动 AUTOCLIK.EXE。 若要了解有关 AUTODRIV 的详细信息。EXE，请参阅[AUTOCLIK](../visual-cpp-samples.md)。  
  
6.  在远程计算机上，启动 AUTMGR32.EXE（自动化管理器）。  
  
7.  在远程计算机上，启动 RACMGR32.EXE（远程自动化连接管理器）。  
  
8.  在远程自动化连接管理器中，选择从 AutoClik.Document **OLE 类**列表。  
  
9. 选择从系统安全策略**客户端访问**选项卡以授予对 AutoClik.Document 客户端访问权限。  
  
10. 在本地计算机上，启动 RACMGR32。EXE，然后从选择 AutoClik.Document **OLE 类**列表。  
  
11. 从**服务器连接**选项卡上，选择远程计算机和适当的网络协议的网络地址。  
  
12. 与在中选择 AutoClik.Document 仍然**OLE 类**列表框中，选择**远程**命令`Register`菜单。  
  
13. 在本地计算机上，如果您需要具有 Visual Basic 而不是 MFC 客户端，请运行 AUTODRIV.EXE 或等效的 AUTOCLIK.MAK Visual Basic 项目。  
  
 在远程计算机上，您现在应能够查看从本地客户端启动的 AUTOCLIK 执行命令。  
  
## <a name="see-also"></a>请参阅  
 [远程自动化](../mfc/remote-automation.md)

