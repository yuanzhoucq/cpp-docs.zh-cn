---
title: "激活 （c + +） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OLE server applications [MFC], activation
- OLE items [MFC], visual editing
- activation [MFC]
- OLE [MFC], in-place activation
- OLE [MFC], activation
- in-place activation, embedded and linked items
- activating objects
- visual editing, activation
- visual editing
- documents [MFC], OLE
- embedded objects [MFC]
- OLE [MFC], editing
- in-place activation
- activation [MFC], embedded OLE items
- OLE activation [MFC]
ms.assetid: ed8357d9-e487-4aaa-aa6b-2edc4de25dfa
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 70017721fb59fa0c6d18d568546d9618257328b5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="activation-c"></a>Activation (C++)
此文章介绍了在可视编辑 OLE 项中激活的角色。 用户具有在容器文档中嵌入 OLE 项后，它可能需要使用。 若要执行此操作，用户，请双击项，其激活。 激活的最常见活动正在编辑。 多个当前 OLE 项，以进行编辑，激活时导致在当前的框架窗口，若要更改以反映属于服务器应用程序创建项的菜单和工具栏。 此行为，已知为就地激活，允许用户无需离开容器文档窗口中编辑复合文档中的任何嵌入的项。  
  
 还有可能要编辑一个单独的窗口中的嵌入的 OLE 项。 如果在容器或服务器应用程序不支持就地激活，则将发生这种情况。 在这种情况下，当用户双击嵌入的项时，服务器应用程序将在单独的窗口中启动和嵌入的项将显示为其自己的文档。 用户编辑此窗口中的项。 编辑完成后，用户关闭服务器应用程序，并返回到容器应用程序。  
  
 作为替代方法，用户可以选择"打开编辑" **\<对象 > 打开**命令**编辑**菜单。 这将在单独的窗口中打开对象。  
  
> [!NOTE]
>  编辑嵌入的项在单独的窗口是 OLE，版本 1 中的标准行为，而且某些 OLE 应用程序可能支持仅编辑此样式。  
  
 就地激活提升为文档创建的以文档为中心的方法。 用户可以将复合文档作为单个实体，而无需应用程序之间切换在其上运行。 但是，在就地激活仅用于嵌入项，不适用于链接的项： 必须在单独的窗口中编辑这些。 这是因为链接的项实际存储在其他位置。 链接的项的编辑发生实际的数据，即，上下文中存储数据。 编辑链接的项在单独的窗口提醒其数据属于另一个文档的用户。  
  
 MFC 不支持嵌套的就地激活。 如果你生成容器/服务器应用程序，并且容器/服务器嵌入在另一个容器和就地激活，它不能就地激活嵌入在它里面的对象。  
  
 当用户双击它，嵌入项会发生什么情况取决于为项定义的谓词。 有关信息，请参阅[激活： 谓词](../mfc/activation-verbs.md)。  
  
## <a name="see-also"></a>请参阅  
 [OLE](../mfc/ole-in-mfc.md)   
 [容器](../mfc/containers.md)   
 [服务器](../mfc/servers.md)

