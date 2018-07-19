---
title: LINGER 结构 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- LINGER
dev_langs:
- C++
helpviewer_keywords:
- LINGER structure [MFC]
ms.assetid: 1fb1c5bf-a64e-4a6c-89d6-1734e4fdbb1b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 53601afdd562f29ccd4bce9db76811e610940b7a
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37339366"
---
# <a name="linger-structure"></a>LINGER 结构
`LINGER`结构用于操作的 {3&gt;so_linger&lt;3 和 4&gt;so_dontlinger&lt;4} 选项`CAsyncSocket::GetSockOpt`。  
  
## <a name="syntax"></a>语法  
  
```  
struct linger {  
    u_short l_onoff;            // option on/off  
    u_short l_linger;           // linger time  
};  
```  
  
## <a name="remarks"></a>备注  
 锁定成员函数将设置 4&gt;so_dontlinger&lt;4} 选项可阻止`Close`等待发送的未发送数据时。 设置此选项等同于将设置与 SO_LINGER`l_onoff`设置为 0。  
  
## <a name="requirements"></a>要求  
 **标头：** winsock2.h  
  
## <a name="see-also"></a>请参阅  
 [结构、 样式、 回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CAsyncSocket::GetSockOpt](../../mfc/reference/casyncsocket-class.md#getsockopt)   
 [CAsyncSocket::SetSockOpt](../../mfc/reference/casyncsocket-class.md#setsockopt)

