---
title: "容器：实现容器 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "应用程序 [OLE], OLE 容器"
  - "OLE 容器, 实现"
ms.assetid: af1e2079-619a-4eac-9327-985ad875823a
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 容器：实现容器
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文概述实现容器的方法并将点提供有关实现容器的详细说明的其他文章。  它还列出可能需要实现并描述这些功能中的文章的一些选项 OLE 功能。  
  
#### 准备 CWinApp 派生的类  
  
1.  通过调用 `InitInstance` 的 **AfxOleInit** 成员函数初始化 OLE 库。  
  
2.  调用 `InitInstance` 的 `CDocTemplate::SetContainerInfo` 分配快捷菜单，然后在嵌入项激活时加速资源使用。  有关本主题的更多信息，请参见 [](../mfc/activation-cpp.md "Activation (C++)")。  
  
 在使用 MFC 应用程序向导创建的容器应用程序时，这些功能将为您自动提供。  参见 [创建 MFC ActiveX EXE 程序](../mfc/reference/mfc-application-wizard.md)。  
  
#### 准备视图类  
  
1.  keep 的 track 通过维护指针选择指针项或列表，如果支持多重选择，为选定项。  `OnDraw` 函数需要绘制任何 OLE 项。  
  
2.  `IsSelected` 重写检查项传递给它的是否当前选择。  
  
3.  实现 **OnInsertObject** 消息处理程序演示 **插入对象** 对话框。  
  
4.  实现 `OnSetFocus` 消息处理程序将从的视图焦点到就地活动 OLE 嵌入项。  
  
5.  实现 `OnSize` 消息处理程序通知 OLE 嵌入项在需要改变其矩形的尺寸上反映更改为其包含的意图。  
  
 由于这些功能实现从一个应用程序向下显著更改，应用程序向导仅提供的基本实现。  您可能需要自定义这些函数获取应用程序正常工作。  有关此情况的示例，请参见[CONTAINER](../top/visual-cpp-samples.md)代码示例。  
  
#### 若要处理嵌入的资源和链接的项  
  
1.  从[COleClientItem](../mfc/reference/coleclientitem-class.md)类派生一个类  此类对象表示嵌入指向 OLE 文档的项。  
  
2.  重写 **OnChange**、`OnChangeItemPosition`和 `OnGetItemPosition`。  这些函数处理大小，位置和修改嵌入的资源和链接的项。  
  
 应用程序向导将派生您的类，但是，可能需要重写 **OnChange** 和其他一些函数列出时带有在前面过程中的步骤 2。  因为这些功能实现应用程序与一个不同。下，主干实现适用于大多数应用程序需要自定义。  有关本的示例，请参见 MFC 示例 [DRAWCLI](../top/visual-cpp-samples.md) 和 [容器 \(O\)](../top/visual-cpp-samples.md)。  
  
 必须将大量项到容器应用程序菜单结构。支持 OLE。  有关这些内容的更多信息，请参见 [菜单和资源：容器添加](../mfc/menus-and-resources-container-additions.md)。  
  
 您可能还想要支持某些在容器应用程序启用下列功能：  
  
-   就地激活，则编辑嵌入式项。  
  
     有关激活的更多信息，请参见[Activation](../mfc/activation-cpp.md)。  
  
-   OLE 项的创建通过拖放从服务器应用程序的选择。  
  
     有关拖放的更多信息，请参见[Drag and Drop \(OLE\)](../mfc/drag-and-drop-ole.md)。  
  
-   到嵌入对象或组合容器\/服务器应用的链接。  
  
     有关更多信息，请参见[Containers: Advanced Features](../mfc/containers-advanced-features.md) 。  
  
## 请参阅  
 [容器](../mfc/containers.md)   
 [容器：客户端项](../mfc/containers-client-items.md)