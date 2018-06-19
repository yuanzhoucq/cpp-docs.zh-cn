---
title: LINGER 结构 |Microsoft 文档
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
ms.openlocfilehash: f19ab7e05b4e27a3b00576339d0b60b37bdba4a7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33374339"
---
# <a name="linger-structure"></a>LINGER 结构
`LINGER`结构用于操作**SO_LINGER**和**SO_DONTLINGER**选项`CAsyncSocket::GetSockOpt`。  
  
## <a name="syntax"></a>语法  
  
```  
struct linger {  
    u_short l_onoff;            // option on/off  
    u_short l_linger;           // linger time  
};  
```  
  
## <a name="remarks"></a>备注  
 设置**SO_DONTLINGER**选项将防止锁定成员函数上**关闭**等待发送的未发送数据时。 设置此选项等效于设置**SO_LINGER**与**l_onoff**设置为 0。  
  
## <a name="requirements"></a>要求  
 **标头：** winsock2.h  
  
## <a name="see-also"></a>请参阅  
 [结构、 样式、 回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CAsyncSocket::GetSockOpt](../../mfc/reference/casyncsocket-class.md#getsockopt)   
 [CAsyncSocket::SetSockOpt](../../mfc/reference/casyncsocket-class.md#setsockopt)

