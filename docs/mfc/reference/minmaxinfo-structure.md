---
title: "MINMAXINFO 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MINMAXINFO
dev_langs:
- C++
helpviewer_keywords:
- MINMAXINFO structure
ms.assetid: be6fb578-f98a-4581-9ada-be9df308ed2f
caps.latest.revision: 10
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 772416bdac3c72f55644fa31aef23ba76a14e606
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="minmaxinfo-structure"></a>MINMAXINFO 结构
`MINMAXINFO`结构包含一个窗口最大化的大小、 位置和其最小值和最大跟踪大小有关的信息。  
  
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
 指定最大化的宽度 (point.x) 和最大化 (point.y) 窗口的高度。  
  
 `ptMaxPosition`  
 指定的最大化窗口 (point.x) 的左侧位置和最大化窗口 (point.y) 的顶部的位置。  
  
 *ptMinTrackSize*  
 指定的最小跟踪宽度 (point.x) 和的最小跟踪窗口的高度 (point.y)。  
  
 *ptMaxTrackSize*  
 指定跟踪宽度 (point.x) 的最大值和跟踪窗口的高度 (point.y) 的最大值。  
  
## <a name="requirements"></a>要求  
 **标头：** winuser.h  
  
## <a name="see-also"></a>另请参阅  
 [结构、 样式、 回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)


