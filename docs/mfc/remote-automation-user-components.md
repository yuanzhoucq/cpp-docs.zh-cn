---
title: "远程自动化用户组件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- DLLs [MFC], Automation
- Remote Automation [MFC], user components
ms.assetid: 601591cc-a442-440a-988e-baf3284b0d46
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2f82fe529586579109434da447e26b15dcb9503a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="remote-automation-user-components"></a>远程自动化用户组件
您需要确保每台客户端计算机包含客户端程序及其所需的任何支持 DLL。 您还需要确保服务器应用程序及其所需的任何支持 DLL 存在于服务器计算机上。 最后，您需要确保服务器程序已在每台客户端计算机上注册，然后才能运行 RAC 管理器以配置连接。 如果该程序是自注册的（因为大多数此类程序都是这样），则只需对客户端计算机执行服务器程序即可注册它。 如果注册失败，您可能必须执行您提供的注册文件，或者手动编辑注册表。  
  
## <a name="see-also"></a>请参阅  
 [自动化管理器 (MFC)](../mfc/automation-manager-mfc.md)   
 [远程自动化连接管理器](../mfc/remote-automation-connection-manager.md)   
 [远程自动化安装](../mfc/remote-automation-installation.md)

