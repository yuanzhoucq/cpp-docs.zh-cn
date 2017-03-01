---
title: "SYSTEMTIME 结构&1; |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SYSTEMTIME
dev_langs:
- C++
helpviewer_keywords:
- SYSTEMTIME structure
ms.assetid: 9aaef4d6-de79-4fa1-8158-86b245ef5bff
caps.latest.revision: 15
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
ms.openlocfilehash: 298b2673a3eb05525683f8269fcd415d5be1c80a
ms.lasthandoff: 02/24/2017

---
# <a name="systemtime-structure1"></a>SYSTEMTIME 结构&1;
`SYSTEMTIME`结构表示的日期和时间用于月、 日、 年、 工作日、 小时、 分钟、 秒和毫秒为单位的各个成员。  
  
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
 当前所处月份;一月表示为 1。  
  
 *wDayOfWeek*  
 当前日期是星期几;星期日为 0，星期一是 1，依此类推。  
  
 *wDay*  
 当前日期的月份。  
  
 *wHour*  
 当前的小时数。  
  
 *wMinute*  
 当前的一分钟。  
  
 *wSecond*  
 当前第二个。  
  
 *wMilliseconds*  
 当前的毫秒。  
  
## <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_Utilities #&39;](../../mfc/codesnippet/cpp/systemtime-structure1_1.cpp)]  
  
## <a name="requirements"></a>要求  
 **标头︰** winbase.h  
  
## <a name="see-also"></a>另请参阅  
 [结构、 样式、 回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CTime::CTime](../../atl-mfc-shared/reference/ctime-class.md#ctime)


