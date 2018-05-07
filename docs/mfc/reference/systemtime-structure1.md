---
title: SYSTEMTIME 结构 1 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- SYSTEMTIME
dev_langs:
- C++
helpviewer_keywords:
- SYSTEMTIME structure [MFC]
ms.assetid: 9aaef4d6-de79-4fa1-8158-86b245ef5bff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 97a0042adaa223fc5898c057f191f7b750fa230f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="systemtime-structure1"></a>SYSTEMTIME 结构 1
`SYSTEMTIME`结构表示的日期和时间用于月份、 天、 年、 工作日、 小时、 分钟、 秒和毫秒的各个成员。  
  
## <a name="syntax"></a>语法  
  
```  
typedef struct _SYSTEMTIME {  
    WORD wYear;  
    WORD wMonth;  
    WORD wDayOfWeek;  
    WORD wDay;  
    WORD wHour;  
    WORD wMinute;  
    WORD wSecond;  
    WORD wMilliseconds;  
} SYSTEMTIME;  
```  
  
#### <a name="parameters"></a>参数  
 *wYear*  
 当前年份。  
  
 *wMonth*  
 当前月;年 1 月为 1。  
  
 *wDayOfWeek*  
 当前日期是星期几;星期日为 0，星期一是 1，依此类推。  
  
 *wDay*  
 月的当前日期。  
  
 *wHour*  
 当前的小时。  
  
 *wMinute*  
 当前分钟数。  
  
 *wSecond*  
 当前第二个。  
  
 *wMilliseconds*  
 当前的毫秒数。  
  
## <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_Utilities#39](../../mfc/codesnippet/cpp/systemtime-structure1_1.cpp)]  
  
## <a name="requirements"></a>要求  
 **标头：** winbase.h  
  
## <a name="see-also"></a>请参阅  
 [结构、 样式、 回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CTime::CTime](../../atl-mfc-shared/reference/ctime-class.md#ctime)

