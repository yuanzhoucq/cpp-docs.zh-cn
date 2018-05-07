---
title: 服务器 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- OLE server applications [MFC]
- OLE server applications [MFC], activation
- full-server
- servers
- mini-server
- OLE server applications [MFC], server types
- server applications [MFC]
ms.assetid: e45172e8-eae3-400a-8139-0fa009a42fdc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7d153d73889520deaff12b64da36567a8b9a4087
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="servers"></a>服务器
服务器应用程序 （或组件应用程序） 创建供容器应用程序使用的 OLE 项 （或组件）。 可视化编辑服务器应用程序还支持可视编辑或就地激活。 OLE 服务器的另一种形式是[自动化服务器](../mfc/automation-servers.md)。 某些服务器应用程序支持仅创建嵌入项;其他支持嵌入的和链接的项目的创建。 一些只支持链接，但很少见。 所有服务器应用程序必须都支持由容器应用程序激活，当用户想要编辑的项。 应用程序可以是一个容器和服务器。 换而言之，它可以同时将数据合并到其文档，并创建可以作为项合并到其他应用程序的文档的数据。  
  
 袖珍服务器是一种特殊类型的仅可以由容器启动的服务器应用程序。 Microsoft 绘图和 Microsoft Graph 是袖珍的示例。 袖珍服务器不在磁盘上的文件作为存储文档。 相反，它读取它的文档，并将其写入到属于容器的文档中的项。 因此，miniserver 支持仅，嵌入不链接。  
  
 可将完整服务器运行作为一个独立应用程序或由容器应用程序启动。 完整的服务器可以将文档存储为磁盘上的文件。 它可以支持嵌入仅，这两个嵌入和链接，或通过仅链接。 容器应用程序的用户可以通过在服务器和容器中的粘贴命令选择剪切或复制命令创建嵌入的项。 通过选择在容器中的服务器中的复制命令和粘贴链接命令将创建一个链接的项。 或者，用户可以创建使用插入对象对话框中的嵌入或链接项。  
  
 下表总结了不同类型的服务器的特征：  
  
### <a name="server-characteristics"></a>服务器特征  
  
|类型的服务器|支持多个实例|每个文档的项|每个实例的文档|  
|--------------------|---------------------------------|------------------------|----------------------------|  
|袖珍服务器|是|1|1|  
|SDI 完全服务器|是|1 (如果支持链接，则一个或多个)|1|  
|MDI 完全服务器|否 （不是必需）|1 (如果支持链接，则一个或多个)|0 或更多|  
  
 服务器应用程序的事件中多个容器将用于编辑嵌入或链接的项应同时支持多个容器。 如果服务器是 SDI 应用程序 （或对话框界面与袖珍服务器），则服务器的多个实例必须能够同时运行。 这允许应用程序处理每个容器请求的单独实例。  
  
 如果服务器是 MDI 应用程序，它可以创建一个新的 MDI 子窗口容器需要编辑的项的每个时间。 这种方式，应用程序的单个实例可以支持多个容器。  
  
 服务器应用程序必须告知 OLE 系统 Dll 怎么办的服务器的一个实例已在运行时另一个容器请求其服务： 是否应启动新的 server 实例或所有容器将请求定向到的一个实例服务器。  
  
 在服务器上的更多详细信息，请参阅：  
  
-   [服务器：实现服务器](../mfc/servers-implementing-a-server.md)  
  
-   [服务器：实现服务器文档](../mfc/servers-implementing-server-documents.md)  
  
-   [服务器：实现就地框架窗口](../mfc/servers-implementing-in-place-frame-windows.md)  
  
-   [服务器：服务器项](../mfc/servers-server-items.md)  
  
-   [服务器：用户界面问题](../mfc/servers-user-interface-issues.md)  
  
## <a name="see-also"></a>请参阅  
 [OLE](../mfc/ole-in-mfc.md)   
 [容器](../mfc/containers.md)   
 [容器： 高级的功能](../mfc/containers-advanced-features.md)   
 [菜单和资源 (OLE)](../mfc/menus-and-resources-ole.md)   
 [注册](../mfc/registration.md)   
 [自动化服务器](../mfc/automation-servers.md)

