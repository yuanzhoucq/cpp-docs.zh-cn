---
title: "消息映射 (MFC) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.messages
dev_langs:
- C++
helpviewer_keywords:
- message maps [C++], MFC
- Windows messages [C++], message maps
- messages [C++], Windows
- MFC [C++], messages
ms.assetid: 3f9855e4-9d7d-4b64-8f3f-a19ea3cf79ba
caps.latest.revision: 10
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5187996fc377bca8633360082d07f7ec8a68ee57
ms.openlocfilehash: bb31d35e221c9f5d06dc34408bed500b4a18b077
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="message-maps-mfc"></a>消息映射 (MFC)
该引用本部分列出了所有[消息映射宏](../../mfc/reference/message-map-macros-mfc.md)和全部[CWnd](../../mfc/reference/cwnd-class.md)消息映射条目以及相应的成员函数原型︰  
  
|类别|说明|  
|--------------|-----------------|  
|[WM_COMMAND 消息处理程序](../../mfc/reference/wm-command-message-handler.md)|处理**WM_COMMAND**在用户菜单选项或菜单访问键产生的消息。|  
|[子窗口通知消息处理程序](../../mfc/reference/child-window-notification-message-handlers.md)|处理从子窗口通知消息。|  
|[WM_ 消息处理程序](../../mfc/reference/handlers-for-wm-messages.md)|处理**WM_**消息，如`WM_PAINT`。|  
|[用户定义消息处理程序](../../mfc/reference/user-defined-handlers.md)|处理用户定义的消息。|  
  
 (有关术语和本参考中使用的约定的说明，请参阅[如何使用消息映射交叉引用](../../mfc/reference/how-to-use-the-message-map-cross-reference.md)。)  
  
 由于 Windows 是面向消息的系统的操作系统，对 Windows 环境进行编程的大部分内容涉及消息处理。 每次事件如击键或鼠标单击时，一条消息发送到应用程序，然后，必须处理该事件。  
  
 Microsoft 基础类库提供了针对基于消息的编程优化的编程模型。 在此模型中，"消息映射"用于指定哪些函数将处理特定的事件类的各种消息。 消息映射包含一个或多个指定的消息将由哪些函数处理的宏。 例如，一个消息映射包含`ON_COMMAND`宏可能如下所示︰  
  
 [!code-cpp[NVC_MFCMessageMaps #&16;](../../mfc/reference/codesnippet/cpp/message-maps-mfc_1.cpp)]  
  
 `ON_COMMAND`宏用于处理生成的菜单、 按钮和快捷键的命令消息。 [宏](../../mfc/reference/message-map-macros-mfc.md)包含可映射以下︰  
  
## <a name="windows-messages"></a>Windows 消息  
  
-   控件通知  
  
-   用户定义的消息  
  
## <a name="command-messages"></a>命令消息  
  
-   已注册的用户定义的消息  
  
-   用户界面更新消息  
  
## <a name="ranges-of-messages"></a>范围的消息  
  
-   命令  
  
-   更新处理程序的消息  
  
-   控件通知  
  
 尽管消息映射宏很重要，但您通常不必直接使用它们。 这是因为属性窗口，自动创建消息映射条目在源文件中时用于将消息处理函数与消息相关联。 无论的何时想要编辑或添加消息映射条目时，您可以使用属性窗口。  
  
> [!NOTE]
>  属性窗口不支持消息映射范围。 您必须自己编写这些消息映射条目。  
  
 但是，消息映射是 Microsoft 基础类库的一个重要部分。 您应该了解它们的功能，并为它们提供文档。  
  
## <a name="see-also"></a>另请参阅  
 [结构、 样式、 回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)


