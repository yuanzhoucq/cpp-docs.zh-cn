---
title: MINMAXINFO 结构 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- MINMAXINFO
dev_langs:
- C++
helpviewer_keywords:
- MINMAXINFO structure [MFC]
ms.assetid: be6fb578-f98a-4581-9ada-be9df308ed2f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 12161938f96e5044ae48f9eb5cf380fbc3840d3f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33369513"
---
# <a name="minmaxinfo-structure"></a>MINMAXINFO 结构
`MINMAXINFO`结构包含一个窗口最大化的大小、 位置和其最小和最大跟踪大小有关的信息。  
  
## <a name="syntax"></a>语法  
  
```  
typedef struct tagMINMAXINFO {  
    POINT ptReserved;  
    POINT ptMaxSize;  
    POINT ptMaxPosition;  
    POINT ptMinTrackSize;  
    POINT ptMaxTrackSize;  
} MINMAXINFO;  
```  
  
#### <a name="parameters"></a>参数  
 *ptReserved*  
 保留以供内部使用。  
  
 *ptMaxSize*  
 指定的最大化的宽度 (point.x) 和窗口的最大化的高度 (point.y)。  
  
 `ptMaxPosition`  
 指定的最大化窗口 (point.x) 左侧的位置和最大化窗口 (point.y) 的顶部的位置。  
  
 *ptMinTrackSize*  
 指定的最小跟踪宽度 (point.x) 和的最小跟踪窗口的高度 (point.y)。  
  
 *ptMaxTrackSize*  
 指定跟踪宽度 (point.x) 的最大和最大值，跟踪窗口的高度 (point.y)。  
  
## <a name="requirements"></a>要求  
 **标头：** winuser.h  
  
## <a name="see-also"></a>请参阅  
 [结构、 样式、 回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)

