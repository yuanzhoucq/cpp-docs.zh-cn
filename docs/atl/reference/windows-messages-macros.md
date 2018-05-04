---
title: Windows 消息宏 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlbase/ATL::WM_FORWARDMSG
dev_langs:
- C++
ms.assetid: 63abd22c-372d-4148-bb04-c605950ae64f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 21bb273b94f871e253ab927238c96256f46e2b3a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="windows-messages-macros"></a>Windows 消息宏
此宏将转发窗口消息。  
  
|||  
|-|-|  
|[WM_FORWARDMSG](#wm_forwardmsg)|使用将转发到另一个处理的窗口的窗口收到的消息。|  

## <a name="requirements"></a>要求  
 **标头：** atlbase.h 
   
##  <a name="wm_forwardmsg"></a>  WM_FORWARDMSG  
 此宏将转发到另一个处理的窗口的窗口收到的消息。  
  
```
WM_FORWARDMSG
```  
  
### <a name="return-value"></a>返回值  
 非零如果不，如果消息已处理，将为零。  
  
### <a name="remarks"></a>备注  
 使用`WM_FORWARDMSG`转发到另一个处理的窗口的窗口收到的消息。 则 LPARAM 和 WPARAM 使用参数，如下所示：  
  
|参数|用法|  
|---------------|-----------|  
|WPARAM|用户定义的数据|  
|LPARAM|指向的指针`MSG`结构，其中包含有关消息的信息|  
  
### <a name="example"></a>示例  
 在下面的示例中，`m_hWndOther`表示收到此消息的其他窗口。  
  
 [!code-cpp[NVC_ATL_Windowing#137](../../atl/codesnippet/cpp/windows-messages-macros_1.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [宏](../../atl/reference/atl-macros.md)
