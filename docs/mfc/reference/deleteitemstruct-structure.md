---
title: DELETEITEMSTRUCT 结构 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- DELETEITEMSTRUCT
dev_langs:
- C++
helpviewer_keywords:
- DELETEITEMSTRUCT structure [MFC]
ms.assetid: 48d3998c-f4a8-402a-bf90-df3770a78685
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2f56a09742276c7fcb1bd66ff1a36b1d17cdf882
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33370941"
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
  
## <a name="requirements"></a>要求  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [结构、 样式、 回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnDeleteItem](../../mfc/reference/cwnd-class.md#ondeleteitem)


