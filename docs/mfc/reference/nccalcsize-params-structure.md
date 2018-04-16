---
title: "NCCALCSIZE_PARAMS 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- NCCALCSIZE_PARAMS
dev_langs:
- C++
helpviewer_keywords:
- NCCALCSIZE_PARAMS structure [MFC]
ms.assetid: 3424cd9f-806a-4089-82fb-414187589edf
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 76a0a16ff0a2c90c6dd6060badc2c79dde1af231
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="nccalcsizeparams-structure"></a>NCCALCSIZE_PARAMS 结构
`NCCALCSIZE_PARAMS`结构包含应用程序可以在处理时使用的信息`WM_NCCALCSIZE`消息来计算大小、 位置和一个窗口的客户端区域的有效内容。  
  
## <a name="syntax"></a>语法  
  
```  
typedef struct tagNCCALCSIZE_PARAMS {  
    RECT rgrc[3];  
    PWINDOWPOS lppos;  
} NCCALCSIZE_PARAMS;  
```  
  
#### <a name="parameters"></a>参数  
 *rgrc*  
 指定矩形的数组。 第一个包含已被移动或调整大小的窗口的新坐标。 它已移动或调整大小之前，第二个包含窗口的坐标。 第三个包含之前它已移动或调整大小的窗口的工作区的坐标。 如果窗口，子窗口的坐标为父窗口的工作区相对。 如果窗口为顶级窗口的坐标为相对于屏幕。  
  
 *lppos*  
 指向[WINDOWPOS](../../mfc/reference/windowpos-structure1.md)包含引起只能移动或调整窗口的操作中指定的大小和位置值的结构。  
  
## <a name="requirements"></a>惠?  
 **标头：** winuser.h  
  
## <a name="see-also"></a>请参阅  
 [结构、 样式、 回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize)

