---
title: "Windows 消息宏 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
ms.assetid: 63abd22c-372d-4148-bb04-c605950ae64f
caps.latest.revision: 16
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
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: be814c0a2ade7df8f7a4d6863627e79efe0a48bc
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="windows-messages-macros"></a>Windows 消息宏
该宏将窗口消息转发。  
  
|||  
|-|-|  
|[WM_FORWARDMSG](#wm_forwardmsg)|使用转发到另一个用于处理窗口的窗口收到的消息。|  

## <a name="requirements"></a>要求  
 **标头︰** atlbase.h 
   
##  <a name="wm_forwardmsg"></a>WM_FORWARDMSG  
 此宏会将转发到另一个用于处理窗口的窗口收到的消息。  
  
```
WM_FORWARDMSG
```  
  
### <a name="return-value"></a>返回值  
 非零如果没有，如果消息已处理，将为零。  
  
### <a name="remarks"></a>备注  
 使用`WM_FORWARDMSG`转发到另一个用于处理窗口的窗口收到的消息。 LPARAM 和 WPARAM 参数的用法如下︰  
  
|参数|用法|  
|---------------|-----------|  
|WPARAM|由用户定义的数据|  
|LPARAM|一个指向`MSG`结构，其中包含有关消息的信息|  
  
### <a name="example"></a>示例  
 在下面的示例中，`m_hWndOther`表示收到此消息的其他窗口。  
  
 [!code-cpp[NVC_ATL_Windowing #&137;](../../atl/codesnippet/cpp/windows-messages-macros_1.cpp)]  
  
## <a name="see-also"></a>另请参阅  
 [宏](../../atl/reference/atl-macros.md)

