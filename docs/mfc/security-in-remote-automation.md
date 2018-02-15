---
title: "远程自动化中的安全性 |Microsoft 文档"
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
- AllowRemoteActivation [MFC]
- Remote Automation [MFC], security
- activating objects [MFC]
- security [MFC]
- Automation objects [MFC], security options
- object activation [MFC]
- security [MFC], Remote Automation
ms.assetid: 276b300d-c0b5-4bd8-8bf5-0270994b9cfa
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e535fac6330d6268629e8e3681fec47c7b0d65d3
ms.sourcegitcommit: fa7a6dccddce3747389c91277a53e296f905305c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="security-in-remote-automation"></a>远程自动化中的安全性
远程自动化支持基本级别的安全性，以允许服务器应用程序编写者（或应用程序管理员）指定如何能够远程激活特定对象。 可以将给定系统上的所有自动化对象全局设置为“禁止远程激活”或“允许远程激活”。 此外，更多时候，可能会为单个对象提供此类功能。 远程自动化在每个对象的注册表设置中，使用密钥**AllowRemoteActivation**，以确定是否可能远程激活给定的服务器。 如果系统级设置使用此模式，则可以为注册表中的每个对象分配此键，而且每个键的单个状态可以相应设置成“yes”或“no”。  
  
 如果服务器系统正在运行 Windows NT 或 Windows 2000，则允许使用安全性的一种替代形式。 在这种情况下，远程自动化使用 NT 访问控制列表 (ACL) 来指定哪些用户或组或用户组可以远程激活给定的服务器。  
  
 请注意，安全选项应用于整个对象；无法设置某个特定接口的特性或者设置该对象的单个属性或方法的特性。  
  
 可通过远程自动化连接 (RAC) 管理器设置所有安全选项。  
  
## <a name="see-also"></a>请参阅  
 [远程自动化](../mfc/remote-automation.md)

