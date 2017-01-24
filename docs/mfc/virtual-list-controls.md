---
title: "虚拟列表控件 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "缓存, 虚拟列表控件项数据"
  - "列表控件, 列表视图"
  - "列表控件, virtual"
  - "虚拟列表控件"
ms.assetid: 319f841f-e426-423a-8276-d93f965b0b45
caps.latest.revision: 13
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 虚拟列表控件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

虚列表控件是有 **LVS\_OWNERDATA** 样式的列表视图控件。  此样式允许控件支持项计数到`DWORD` \(默认项计数只扩展到 `int`。\)  但是，这一样式所提供的最大的优点是在任何时候都只有一部分数据项在内存中。  这允许虚拟列表视图控件将自己用于大型信息数据库中，这其中访问数据的方法已经准备就绪。  
  
> [!NOTE]
>  除了在`CListCtrl`中提供虚拟列表功能外，MFC 还在 [CListView](../mfc/reference/clistview-class.md) 类中提供了相同的功能。  
  
 在开发虚拟列表控件时，还应意识到这里会有一些兼容性问题。  有关详细信息，请参见[!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]中的主题列表视图控件的兼容性问题部分 。  
  
## 处理 LVN\_GETDISPINFO 通知  
 虚拟列表控件很少维护项信息。  除选择项和专注信息，所有项信息都有控件所有者管理。  信息由框架通过 **LVN\_GETDISPINFO** 请求通知消息。  若要提供请求信息，虚拟列表控件的所有者 \(或控件本身\) 必须处理此通知。  使用属性窗口这能轻松地完成 \(请参见[指向函数的信息映射](../mfc/reference/mapping-messages-to-functions.md)\)  提供的代码应类似于下面的示例 \(其中 `CMyDialog` 拥有虚拟列表控件对象，且该对话框通知处理\):  
  
 [!code-cpp[NVC_MFCControlLadenDialog#23](../mfc/codesnippet/CPP/virtual-list-controls_1.cpp)]  
  
 在通知消息处理程序**LVN\_GETDISPINFO** 中，必须检查所请求的消息的类型。  可能的值包括：  
  
-   `LVIF_TEXT` `pszText`是必须填写的成员。  
  
-   `LVIF_IMAGE` `iImage`是必须填写的成员。  
  
-   **LVIF\_INDENT** *iIndent* 是必须填写的成员 。  
  
-   `LVIF_PARAM` *lParam* 是必须填写的成员。\(对于子项不存在。\)  
  
-   `LVIF_STATE` *state*是必须填充的成员。  
  
 您随后应提供任何回到框架的请求信息。  
  
 以下示例 \(对列表控件对象，从通知处理程序主体中提取出的\) 展示了一种通过为文本缓冲区和图像项提供信息的方法。  
  
 [!code-cpp[NVC_MFCControlLadenDialog#24](../mfc/codesnippet/CPP/virtual-list-controls_2.cpp)]  
  
## 缓存和虚拟列表控件  
 由于这种列表控件用于大型数据集，建议要缓存请求项检索数据来提高性能。  框架提供一个机制的缓存提示机制，通过发送 **LVN\_ODCACHEHINT** 通知消息来帮助优化缓存。  
  
 下面的示例通过范围传递给处理程序函数来更新缓存。  
  
 [!code-cpp[NVC_MFCControlLadenDialog#25](../mfc/codesnippet/CPP/virtual-list-controls_3.cpp)]  
  
 有关准备和维护缓存的详细信息，请参见在 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]中的 主题列表视图控件的缓存管理部门。  
  
## 查找特定项  
 当需要寻找特定列表项控件时，**LVN\_ODFINDITEM** 通知消息由虚拟列表控件发送。  通知消息会发送，当列表视图控件接收键快速访问时，或者接收到 **LVM\_FINDITEM** 消息时。  搜索信息以 **LVFINDINFO** 结构的形式发送，其是 **NMLVFINDITEM** 结构的成员。  通过重写列表控件对象的`OnChildNotify` 函数和此消息处理程序的主体，检查**LVN\_ODFINDITEM** 消息。  如果找到，请执行适当的操作。  
  
 您需要准备寻找与给定的列表视图控件相匹配的项。  如果找到，则返回索引值，如果没有找到匹配项则返回\-1。  
  
## 请参阅  
 [使用 CListCtrl](../mfc/using-clistctrl.md)   
 [控件](../mfc/controls-mfc.md)