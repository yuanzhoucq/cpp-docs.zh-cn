---
title: "Cdc:: setabortproc 的回调函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Callback Function for CDC::SetAbortProc
dev_langs:
- C++
helpviewer_keywords:
- callback functions, for CDC::SetAbortProc
ms.assetid: daa36d5d-15de-40fc-8d37-a865d06c4710
caps.latest.revision: 11
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
ms.openlocfilehash: 1ba16ea60d8b18abd1962ded2da7e11ff2ef09a1
ms.lasthandoff: 02/24/2017

---
# <a name="callback-function-for-cdcsetabortproc"></a>Callback Function for CDC::SetAbortProc
名称*AbortFunc*是应用程序提供的函数名称的占位符。  
  
## <a name="syntax"></a>语法  
  
```  
BOOL CALLBACK EXPORT AbortFunc(
    HDC hPr,  
    int code);
```  
  
#### <a name="parameters"></a>参数  
 *hPr*  
 标识设备上下文。  
  
 `code`  
 指定是否已发生了错误。 如果未发生错误，则为 0。 它是**SP_OUTOFDISK**如果打印管理器当前磁盘空间不足，更多磁盘空间将变为可用，如果应用程序等待。 如果`code`是**SP_OUTOFDISK**，应用程序没有中止打印作业。 如果不存在，它必须通过调用产生到打印管理器**PeekMessage**或**GetMessage** Windows 函数。  
  
## <a name="return-value"></a>返回值  
 终止处理程序函数的返回值，并且如果打印作业若要继续，则为非 0 如果就被取消。  
  
## <a name="remarks"></a>备注  
 中的备注部分所述，必须导出实际名称[cdc:: setabortproc](../../mfc/reference/cdc-class.md#setabortproc)。  
  
## <a name="requirements"></a>要求  
 **标头:** afxwin.h  
  
## <a name="see-also"></a>另请参阅  
 [结构、 样式、 回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [Cdc:: setabortproc](../../mfc/reference/cdc-class.md#setabortproc)


