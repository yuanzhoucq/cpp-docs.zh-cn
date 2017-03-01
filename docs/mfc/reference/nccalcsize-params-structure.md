---
title: "NCCALCSIZE_PARAMS 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- NCCALCSIZE_PARAMS
dev_langs:
- C++
helpviewer_keywords:
- NCCALCSIZE_PARAMS structure
ms.assetid: 3424cd9f-806a-4089-82fb-414187589edf
caps.latest.revision: 13
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
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 88c25fd5e5862d5f0954ae853442c66eaf7320c8
ms.lasthandoff: 02/24/2017

---
# <a name="nccalcsizeparams-structure"></a>NCCALCSIZE_PARAMS 结构
`NCCALCSIZE_PARAMS`结构包含应用程序可以处理时使用的信息`WM_NCCALCSIZE`消息来计算大小、 位置和一个窗口的工作区中的有效内容。  
  
## <a name="syntax"></a>语法  
  
```  
typedef struct tagNCCALCSIZE_PARAMS {  
    RECT rgrc[3];  
    PWINDOWPOS lppos;  
} NCCALCSIZE_PARAMS;  
```  
  
#### <a name="parameters"></a>参数  
 *rgrc*  
 指定的矩形的数组。 第一个包含新的坐标，已被移动或调整大小的窗口。 它已移动或调整大小之前，第二个包含窗口中的坐标。 它已移动或调整大小之前，第三个包含小化窗口的客户端区域的坐标。 如果窗口中，子窗口的坐标为相对于父窗口工作区。 如果窗口为顶级窗口，坐标是相对于屏幕。  
  
 *lppos*  
 指向[WINDOWPOS](../../mfc/reference/windowpos-structure1.md)结构，其中包含导致移动或调整大小的窗口的操作中指定的大小和位置值。  
  
## <a name="requirements"></a>要求  
 **标头：** winuser.h  
  
## <a name="see-also"></a>另请参阅  
 [结构、 样式、 回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize)


