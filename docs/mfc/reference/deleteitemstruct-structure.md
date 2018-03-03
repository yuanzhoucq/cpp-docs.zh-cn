---
title: "DELETEITEMSTRUCT 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DELETEITEMSTRUCT
dev_langs:
- C++
helpviewer_keywords:
- DELETEITEMSTRUCT structure [MFC]
ms.assetid: 48d3998c-f4a8-402a-bf90-df3770a78685
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 93be7b23ae713caea5fa64e437fe792c550589f1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="deleteitemstruct-structure"></a>DELETEITEMSTRUCT 结构
`DELETEITEMSTRUCT` 结构介绍了一个已删除的所有者描述的列表框或组合框项。  
  
## <a name="syntax"></a>语法  
  
```  
typedef struct tagDELETEITEMSTRUCT { /* ditms */  
    UINT CtlType;  
    UINT CtlID;  
    UINT itemID;  
    HWND hwndItem;  
    UINT itemData;  
} DELETEITEMSTRUCT;  
```  
  
#### <a name="parameters"></a>参数  
 `CtlType`  
 指定**ODT_LISTBOX** （一个所有者描述的列表框） 或**ODT_COMBOBOX** （一个所有者描述的组合框）。  
  
 `CtlID`  
 指定列表框或组合框的标识符。  
  
 `itemID`  
 指定要移除的列表框或组合框中的项的索引。  
  
 `hwndItem`  
 标识控件。  
  
 `itemData`  
 为该项指定应用程序定义的数据。 此值传递到中的控件**lParam**将项添加到列表框或组合框的消息的参数。  
  
## <a name="remarks"></a>备注  
 在从列表框或组合框中移除某个项或销毁列表框或组合框时，Windows 会将 `WM_DELETEITEM` 消息发送给每个被删除项的所有者。 **LParam**消息参数包含指向此结构的指针。  
  
## <a name="requirements"></a>惠?  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [结构、 样式、 回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnDeleteItem](../../mfc/reference/cwnd-class.md#ondeleteitem)


