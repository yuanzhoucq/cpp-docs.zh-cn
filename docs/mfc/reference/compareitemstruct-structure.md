---
title: "COMPAREITEMSTRUCT 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "COMPAREITEMSTRUCT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COMPAREITEMSTRUCT 结构"
ms.assetid: 4b7131a5-5c7d-4e98-aac7-e85650262b52
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# COMPAREITEMSTRUCT 结构
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`COMPAREITEMSTRUCT` 结构提供标识符和为已排序的，所有者绘制的列表框或组合框两项应用程序所提供的数据。  
  
## 语法  
  
```  
  
      typedef struct tagCOMPAREITEMSTRUCT {  
    UINT   CtlType;  
    UINT   CtlID;  
    HWND   hwndItem;  
    UINT   itemID1;  
    DWORD  itemData1;  
    UINT   itemID2;  
    DWORD  itemData2;  
} COMPAREITEMSTRUCT;  
```  
  
#### 参数  
 `CtlType`  
 **ODT\_LISTBOX** \(指定所有者描述列表框\) 或 **ODT\_COMBOBOX** \(指定所有者描述组合框\) 。  
  
 `CtlID`  
 列表框或组合框的控件 ID。  
  
 `hwndItem`  
 控件的窗口句柄。  
  
 *itemID1*  
 相比较的列表框或组合框的第一项索引。  
  
 *itemData1*  
 为进行比较的第一项的应用程序所提供的数据。  此值在添加到组合框或列表框的项的调用中传递。  
  
 *itemID2*  
 被比较的列表框或组合框中第二项的索引。  
  
 *itemData2*  
 为进行比较的第二项的应用程序所提供的数据。  此值在添加到组合框或列表框的项的调用中传递。  
  
## 备注  
 无论什么时候一个应用程序在使用 **CBS\_SORT** 或 **LBS\_SORT** 样式创建的所有者描绘的列表框或组合框上添加一个新项时，Windows 发送所有者一个 `WM_COMPAREITEM` 消息。  消息的 `lParam` 参数包含指向 `COMPAREITEMSTRUCT` 结构长整型的指针。  依据收到的消息，所有者比较两个项并返回值指示前面的一项。  
  
## 要求  
 **头文件：** 指令  
  
## 请参阅  
 [结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnCompareItem](../Topic/CWnd::OnCompareItem.md)