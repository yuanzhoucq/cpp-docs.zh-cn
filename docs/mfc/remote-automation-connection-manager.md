---
title: "远程自动化连接管理器 |Microsoft 文档"
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
- Automation clients [MFC], configuring for Remote Automation
- registry [MFC], remote Automation
- Automation servers [MFC], configuring for Remote Automation
- Remote Automation Connection Manager [MFC]
- Remote Automation [MFC], configuring client and server machines
- RAC Manager tool [MFC]
ms.assetid: 562eb7bc-f95c-46ad-ac97-f0dfa98362af
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ee78c1fb5c66974c946d0571db981d899f405fe3
ms.sourcegitcommit: a5916b48541f804a79891ff04e246628b5f9a24a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/09/2018
---
# <a name="remote-automation-connection-manager"></a>远程自动化连接管理器
若要配置客户端计算机和服务器计算机，则需要进行注册表更改。 与其手动执行此操作，不如使用远程自动化连接 (RAC) 管理器工具，因为后者方便得多。 需要将工具 RACMGR32.EXE 以及 RACREG32.DLL 复制到您选择的所有目录。 将此工具放入 PATH 后，可以使用 Run 从任务栏执行它。 或者，也可以在“开始”菜单中创建此工具的快捷方式或放置对它的引用。  
  
 RACMGR32 是采用 Visual Basic 编写的，因此需要一些 Visual Basic 支持 DLL。 这些文件与 RACMGR32 放置在 CD-ROM 上的同一目录中。 由 Visual C++ Enterprise Edition 的安装程序置安装的这些文件的版本与 Visual Basic Enterprise Edition 5.0 附带这些文件的版本相同或比它更新。 Visual c + + 安装程序将新版本的 Visual Basic 文件复制到你的系统目录中，这通常是 C:\Windows\System32。 安装程序还会将这些文件注册到操作系统。 您可以从 Visual Basic 安装中移除它们。  
  
## <a name="see-also"></a>请参阅  
 [自动化管理器 (MFC)](../mfc/automation-manager-mfc.md)   
 [远程自动化用户组件](../mfc/remote-automation-user-components.md)   
 [远程自动化安装](../mfc/remote-automation-installation.md)

