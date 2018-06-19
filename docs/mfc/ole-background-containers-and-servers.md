---
title: OLE 后台： 容器和服务器 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- OLE full-server applications [MFC]
- server applications [MFC], communication with containers
- full-server [MFC]
- server applications [MFC], requirements
- server applications [MFC], defined
- OLE server applications [MFC], about server applications
- server applications [MFC], full-server vs. mini-server
- OLE server applications [MFC], mini-server applications
- OLE containers [MFC], container applications
- containers [MFC], OLE container applications
- server applications [MFC]
ms.assetid: dafbb31d-096c-4654-b774-12900d832919
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f9f15ef532ba61a089f8adec9ed20f737c07eae2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33348542"
---
# <a name="ole-background-containers-and-servers"></a>OLE 后台：容器和服务器
容器应用程序是可将嵌入项或者链接项并入自己的文档中的应用程序。 管理容器应用程序的文档必须能够存储和显示 OLE 文档组件以及创建应用程序本身的数据。 容器应用程序还必须允许用户插入新项或通过激活服务器应用程序在必要时编辑现有项。 本文列出了的容器应用程序的用户界面要求[容器： 用户界面问题](../mfc/containers-user-interface-issues.md)。  
  
 服务器应用程序或组件应用程序的应用程序可以创建供容器应用程序使用的 OLE 文档组件。 服务器应用程序通常支持拖放或将其数据复制到剪贴板，以便容器应用程序可以插入数据作为嵌入或链接的项。 应用程序可以是一个容器和服务器。  
  
 大多数服务器都是独立的应用程序或完整服务器;它们也可以作为独立的应用程序运行或可由容器应用程序启动。 袖珍服务器是一种特殊类型的服务器应用程序可以仅由容器启动。 它不能作为独立的应用程序运行。 Microsoft 绘图和 Microsoft Graph 服务器是袖珍的示例。  
  
 容器和服务器不直接通信。 相反，它们与通信通过 OLE 系统动态链接库 (DLL)。 这些 Dll 提供函数的容器和服务器调用，并在容器和服务器提供 Dll 调用的回调函数。  
  
 使用这种通信，一个容器不必了解服务器应用程序的实现详细信息。 它允许一个容器来接受任何服务器而无需定义类型的服务器可以使用自己创建的项目。 因此，容器应用程序的用户可以利用的未来的应用程序和数据格式。 如果这些新的应用程序是 OLE 组件，复合文档将能够将合并由这些应用程序创建的项。  
  
## <a name="see-also"></a>请参阅  
 [OLE 后台](../mfc/ole-background.md)   
 [OLE 后台： MFC 实现](../mfc/ole-background-mfc-implementation.md)   
 [容器](../mfc/containers.md)   
 [服务器](../mfc/servers.md)   
 [容器： 客户端项](../mfc/containers-client-items.md)   
 [服务器：服务器项](../mfc/servers-server-items.md)

