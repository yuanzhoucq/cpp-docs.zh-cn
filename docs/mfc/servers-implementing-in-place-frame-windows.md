---
title: 服务器： 实现就地框架窗口 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- frame windows [MFC], implementing
- OLE server applications [MFC], frame windows
- servers, in-place frame windows
- frame windows [MFC], in-place
- in-place frame windows
ms.assetid: 09bde4d8-15e2-4fba-8d14-9b954d926b92
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1cc26e2874921d30ef233509ee46b776ec8e3e9b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="servers-implementing-in-place-frame-windows"></a>服务器：实现就地框架窗口
本文介绍如果您不使用应用程序向导创建服务器应用程序，则在可视编辑服务器应用程序中实现就地框架窗口时必须执行的操作。 代替遵循本文中概述的过程，你可以使用应用程序向导生成的应用程序或 Visual c + + 提供的示例从现有的就地框架窗口类。  
  
#### <a name="to-declare-an-in-place-frame-window-class"></a>声明就地框架窗口类  
  
1.  从 `COleIPFrameWnd` 派生就地框架窗口类。  
  
    -   在类的标头文件中使用 `DECLARE_DYNCREATE` 宏。  
  
    -   在类的实现 (.cpp) 文件中使用 `IMPLEMENT_DYNCREATE` 宏。 这使得此类的对象由框架创建。  
  
2.  在框架窗口类中声明 `COleResizeBar` 成员。 这在您需要在服务器应用程序中支持就地重设大小时是必需的。  
  
     声明`OnCreate`消息处理程序 (使用**属性**窗口)，并调用**创建**为你`COleResizeBar`成员，当你已定义。  
  
3.  如果您有一个工具栏，请在框架窗口类中声明 `CToolBar` 成员。  
  
     当服务器处于就地活动状态时，请重写 `OnCreateControlBars` 成员函数以创建工具栏。 例如：  
  
     [!code-cpp[NVC_MFCOleServer#1](../mfc/codesnippet/cpp/servers-implementing-in-place-frame-windows_1.cpp)]  
  
     请参阅下面步骤 5 中对此代码的讨论。  
  
4.  在主 .cpp 文件中包含此就地框架窗口类的标头文件。  
  
5.  在应用程序类的 `InitInstance` 中，调用文档模板对象的 `SetServerInfo` 函数以指定要在打开和就地编辑中使用的资源和就地框架窗口。  
  
 一系列函数调用**如果**语句创建工具栏资源中提供的 server。 此时，工具栏是容器的窗口层次结构的一部分。 由于此工具栏派生自 `CToolBar`，因此它会将其消息传递给其所有者 - 容器应用程序的框架窗口，除非您更改所有者。 这是必需调用 `SetOwner` 的原因。 此调用会将命令将发送到的窗口更改为服务器的就地框架窗口，从而使消息传递到服务器。 这使服务器响应其提供的工具栏上的操作。  
  
 工具栏位图的 ID 应与服务器应用程序中定义的其他就地资源相同。 请参阅[菜单和资源： 服务器添加](../mfc/menus-and-resources-server-additions.md)有关详细信息。  
  
 有关详细信息，请参阅[COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md)， [COleResizeBar](../mfc/reference/coleresizebar-class.md)，和[CDocTemplate::SetServerInfo](../mfc/reference/cdoctemplate-class.md#setserverinfo)中*类库参考*.  
  
## <a name="see-also"></a>请参阅  
 [服务器](../mfc/servers.md)   
 [服务器： 实现服务器](../mfc/servers-implementing-a-server.md)   
 [服务器： 实现服务器文档](../mfc/servers-implementing-server-documents.md)   
 [服务器：服务器项](../mfc/servers-server-items.md)

