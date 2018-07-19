---
title: COMPAREITEMSTRUCT 结构 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COMPAREITEMSTRUCT
dev_langs:
- C++
helpviewer_keywords:
- COMPAREITEMSTRUCT structure [MFC]
ms.assetid: 4b7131a5-5c7d-4e98-aac7-e85650262b52
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6c42f356cb323bb7690b6c39b1fc7bd9ce0485f3
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/05/2018
ms.locfileid: "37850584"
---
# <a name="compareitemstruct-structure"></a>COMPAREITEMSTRUCT 结构
`COMPAREITEMSTRUCT`结构提供的标识符和排序，所有者描述列表框或组合框中的两个项的应用程序提供数据。  
  
## <a name="syntax"></a>语法  
  
```  
typedef struct tagCOMPAREITEMSTRUCT {  
    UINT CtlType;  
    UINT CtlID;  
    HWND hwndItem;  
    UINT itemID1;  
    DWORD itemData1;  
    UINT itemID2;  
    DWORD itemData2;  
} COMPAREITEMSTRUCT;  
```  
  
#### <a name="parameters"></a>参数  
 *CtlType*  
 ODT_LISTBOX （它指定一个所有者描述列表框） 或 ODT_COMBOBOX （它指定一个所有者描述组合框）。  
  
 *CtlID*  
 列表框或组合框控件 ID。  
  
 *hwndItem*  
 控件的窗口句柄。  
  
 *itemID1*  
 在列表框或组合框中要比较的第一项的索引。  
  
 *itemData1*  
 要比较的第一项应用程序提供的数据。 将项添加到组合框或列表框调用中传递此值。  
  
 *itemID2*  
 在列表框或组合框中要比较的第二个项的索引。  
  
 *itemData2*  
 要比较的第二个项的应用程序提供数据。 将项添加到组合框或列表框调用中传递此值。  
  
## <a name="remarks"></a>备注  
 每当应用程序添加到所有者描述的列表框或组合框使用 CBS_SORT 或 LBS_SORT 样式创建一个新项，Windows 将向所有者发送 WM_COMPAREITEM 消息。 *LParam*消息参数包含的长指针`COMPAREITEMSTRUCT`结构。 收到消息时，所有者比较两个项并返回一个值，该值的项进行排序之前的其他。  
  
## <a name="requirements"></a>要求  
 **标头：** winuser.h  
  
## <a name="see-also"></a>请参阅  
 [结构、 样式、 回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnCompareItem](../../mfc/reference/cwnd-class.md#oncompareitem)

