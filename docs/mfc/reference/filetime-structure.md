---
title: "FILETIME 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: FILETIME
dev_langs: C++
helpviewer_keywords: FILETIME structure [MFC]
ms.assetid: e09557e2-b6d7-4dd5-a5b9-6328bca88595
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f23f9d4a508158b392de6eb5c872f0b5762e1ae3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="filetime-structure"></a>FILETIME 结构
`FILETIME`结构是 64 位值表示从 1601 年 1 月 1 日的 100 毫微秒隔数。  
  
## <a name="syntax"></a>语法  
  
```  
typedef struct _FILETIME {  
    DWORD dwLowDateTime;   /* low 32 bits */  
    DWORD dwHighDateTime;  /* high 32 bits */  
} FILETIME, *PFILETIME, *LPFILETIME;  
```  
  
#### <a name="parameters"></a>参数  
 *dwLowDateTime*  
 指定最小的文件时间的 32 位。  
  
 *dwHighDateTime*  
 指定的高 32 位文件时间。  
  
## <a name="requirements"></a>惠?  
 **标头：** windef.h  
  
## <a name="see-also"></a>请参阅  
 [结构、 样式、 回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CTime::CTime](../../atl-mfc-shared/reference/ctime-class.md#ctime)

