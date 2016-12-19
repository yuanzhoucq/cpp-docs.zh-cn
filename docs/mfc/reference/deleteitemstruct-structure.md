---
title: "DELETEITEMSTRUCT 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DELETEITEMSTRUCT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DELETEITEMSTRUCT 结构"
ms.assetid: 48d3998c-f4a8-402a-bf90-df3770a78685
caps.latest.revision: 13
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# DELETEITEMSTRUCT 结构
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`DELETEITEMSTRUCT` 结构来描述已删除的所有者绘制的列表框或组合框项。  
  
## 语法  
  
```  
  
      typedef struct tagDELETEITEMSTRUCT { /* ditms */  
    UINT CtlType;  
    UINT CtlID;  
    UINT itemID;  
    HWND hwndItem;  
    UINT itemData;  
} DELETEITEMSTRUCT;  
```  
  
#### 参数  
 `CtlType`  
 指定 **ODT\_LISTBOX** \(一个所有者绘制的列表框\) 或 **ODT\_COMBOBOX** \(所有者绘制的一组合框\)。  
  
 `CtlID`  
 指定列表框或组合框中的标识符。  
  
 `itemID`  
 移除列表框或组合框中指定项的索引。  
  
 `hwndItem`  
 标识控件。  
  
 `itemData`  
 为该项指定应用程序定义的数据。  此值在用加到列表框或组合框的消息的 **lParam** 参数中传递给控件。  
  
## 备注  
 当项从列表框或组合框中移除，或者当销毁列表框或组合框时，窗口发送 `WM_DELETEITEM` 消息给每个删除项的所有者。  消息的 **lParam** 参数包含指到此结构的指针。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnDeleteItem](../Topic/CWnd::OnDeleteItem.md)