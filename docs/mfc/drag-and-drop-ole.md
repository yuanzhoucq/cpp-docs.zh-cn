---
title: "拖放 (OLE) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OLE server applications [MFC], drag and drop
- drag and drop [MFC]
- OLE applications [MFC], drag and drop
- File Manager drag and drop support [MFC]
- drag and drop [MFC], about OLE drag and drop
- OLE drag and drop [MFC]
ms.assetid: a4595350-ca06-4400-88a1-f0175c76b77b
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2a852e597c06a08c3e9eb83731dc7da7df077435
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="drag-and-drop-ole"></a>拖放 (OLE)
OLE 的拖放功能主要是复制并粘贴数据的快捷方式。 当您使用剪贴板复制或粘贴数据时，需要执行一些步骤。 选择的数据，请单击**剪切**或**复制**从**编辑**菜单上，移动到目标文件、 窗口或应用程序，请将光标置于所需的位置，然后单击**粘贴**从**编辑**菜单。  
  
 OLE 拖放不同于文件管理器拖放机制，后者只能处理文件名，专用于将文件名传递到应用程序。 OLE 拖放更普遍。 利用此功能，您可拖放还可放置在剪贴板上的任何数据。  
  
 如果使用 OLE 拖放，则此过程可减少两个步骤。 从源窗口中选择数据（“放置源”），将其拖至所需目标（“放置目标”），然后释放鼠标按钮来放置数据。 此操作无需菜单，比复制/粘贴序列快。 唯一要求是放置源和放置目标必须打开，至少部分在屏幕上可见。  
  
 使用 OLE 拖放，数据可在文档内的各个位置之间、不同的文档之间或不同的应用程序之间传输。 这可在容器或服务器应用程序中实现，任何应用程序可以是放置源、放置目标或同时为二者。 如果应用程序实现了放置源和放置目标支持，则将在子窗口之间或一个窗口中实现拖放。 此功能可使您的应用程序更易于使用。  
  
 如果你只想要使用 OLE 的拖放功能，请参阅[拖放： 自定义](../mfc/drag-and-drop-customizing.md)。 您可使用文中介绍的方法生成非 OLE 应用程序放置源。 文章[拖放： 实现放置目标](../mfc/drag-and-drop-implementing-a-drop-target.md)描述如何实现对 OLE 和非 OLE 应用程序的放置目标支持。 它也将有助于查看 MFC OLE 示例[OCLIENT](../visual-cpp-samples.md)和[HIERSVR](../visual-cpp-samples.md)。  
  
 如果您不具有读取[数据对象和数据源 (OLE)](../mfc/data-objects-and-data-sources-ole.md)系列文章，你可能想要立即执行此操作。 这些文章介绍数据传输的基本知识，以及如何在应用程序中实现数据传输。  
  
 有关拖放的详细信息，请参阅：  
  
-   [拖放：实现放置源](../mfc/drag-and-drop-implementing-a-drop-source.md)  
  
-   [拖放：实现放置目标](../mfc/drag-and-drop-implementing-a-drop-target.md)  
  
-   [拖放：自定义](../mfc/drag-and-drop-customizing.md)  
  
## <a name="see-also"></a>请参阅  
 [OLE](../mfc/ole-in-mfc.md)   
 [数据对象和数据源 (OLE)](../mfc/data-objects-and-data-sources-ole.md)

