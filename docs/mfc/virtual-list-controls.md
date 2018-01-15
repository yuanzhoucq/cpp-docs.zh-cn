---
title: "虚拟列表控件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- cache, virtual list control item data
- list controls [MFC], virtual
- list controls [MFC], List view
- virtual list controls
ms.assetid: 319f841f-e426-423a-8276-d93f965b0b45
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0223d9733f9290d989183a34b91779ee1f4d5e28
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="virtual-list-controls"></a>虚拟列表控件
虚拟列表控件是一个列表视图控件，具有**LVS_OWNERDATA**样式。 此样式使控件能够最多支持项计数`DWORD`(默认项计数仅扩展到`int`)。 但是，此样式所提供的最大优点是能够在任何时候在内存中仅有部分数据项目。 这将允许虚拟列表视图控件，若要将自身添加为大型数据库的信息，用于访问数据的特定方法已到位。  
  
> [!NOTE]
>  除了提供中的虚拟列表功能`CListCtrl`，MFC 还提供了中的相同功能[CListView](../mfc/reference/clistview-class.md)类。  
  
 有一些你应注意开发虚拟列表控件时的兼容性问题。 有关详细信息，请参阅 Windows SDK 中的列表视图控件主题的兼容性问题部分。  
  
## <a name="handling-the-lvngetdispinfo-notification"></a>处理 LVN_GETDISPINFO 通知  
 虚拟列表控件维护很少项信息。 项选择和焦点信息中，除外由控件的所有者管理项的所有信息。 由框架通过请求信息**LVN_GETDISPINFO**通知消息。 若要提供所请求的信息，虚拟列表控件 （或该控件本身） 的所有者必须处理此通知。 这可以轻松地进行使用属性窗口 (请参阅[消息映射到函数](../mfc/reference/mapping-messages-to-functions.md))。 得到的代码应类似下面的示例 (其中`CMyDialog`拥有虚拟列表控件对象和对话框正在处理通知):  
  
 [!code-cpp[NVC_MFCControlLadenDialog#23](../mfc/codesnippet/cpp/virtual-list-controls_1.cpp)]  
  
 中的处理程序**LVN_GETDISPINFO**通知消息，必须检查以查看正在请求的信息的类型。 可能的值为：  
  
-   `LVIF_TEXT``pszText`成员必须填写。  
  
-   `LVIF_IMAGE``iImage`成员必须填写。  
  
-   **LVIF_INDENT** *iIndent*成员必须填写。  
  
-   `LVIF_PARAM`*LParam*成员必须填写。 （不存在子项目）  
  
-   `LVIF_STATE`*状态*成员必须填写。  
  
 然后应提供给框架请求任何信息。  
  
 下面的示例 （摘自列表控件对象通知处理程序的主体） 通过提供的文本缓冲区和项的图像的信息说明一个可能的方法：  
  
 [!code-cpp[NVC_MFCControlLadenDialog#24](../mfc/codesnippet/cpp/virtual-list-controls_2.cpp)]  
  
## <a name="caching-and-virtual-list-controls"></a>缓存和虚拟列表控件  
 由于此类型的列表控件适用于大型数据集，建议你缓存请求的项数据以改进检索性能。 该框架提供缓存提示的机制，以帮助优化缓存通过发送**LVN_ODCACHEHINT**通知消息。  
  
 下面的示例使用传递给处理程序函数的范围更新缓存。  
  
 [!code-cpp[NVC_MFCControlLadenDialog#25](../mfc/codesnippet/cpp/virtual-list-controls_3.cpp)]  
  
 有关准备和维护缓存的详细信息，请参阅 Windows SDK 中的列表视图控件主题的缓存管理部分。  
  
## <a name="finding-specific-items"></a>查找特定项  
 **LVN_ODFINDITEM**需要找到的特定列表控件项时，由虚拟列表控件发送的通知消息。 在列表视图控件接收快速密钥访问权限，或在接收时发送通知消息**LVM_FINDITEM**消息。 搜索信息发送的窗体中**LVFINDINFO**结构，这是成员的**NMLVFINDITEM**结构。 通过重写处理此消息`OnChildNotify`函数的列表控件对象并在处理程序的主体，检查**LVN_ODFINDITEM**消息。 如果找到，执行相应的操作。  
  
 你应该准备好搜索项给定的列表视图控件的信息相匹配。 如果不找到任何匹配项，则应返回的项，如果成功，则为-1 的索引。  
  
## <a name="see-also"></a>请参阅  
 [使用 CListCtrl](../mfc/using-clistctrl.md)   
 [控件](../mfc/controls-mfc.md)

