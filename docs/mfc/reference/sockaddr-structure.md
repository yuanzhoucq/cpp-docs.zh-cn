---
title: "SOCKADDR 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SOCKADDR
dev_langs:
- C++
helpviewer_keywords:
- SOCKADDR structure
ms.assetid: df1ed66a-f4b8-43f8-8db8-8c2533d25f68
caps.latest.revision: 12
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
ms.openlocfilehash: 28984fcc5614a5f901a01ffdeff4ea5f360f63fc
ms.lasthandoff: 02/24/2017

---
# <a name="sockaddr-structure"></a>SOCKADDR 结构
`SOCKADDR` 结构用于为参与 Windows 套接字通信的计算机存储 Internet 协议 (IP) 地址。  
  
## <a name="syntax"></a>语法  
  
```  
struct sockaddr {  
    unsigned short sa_family;  
    char sa_data[14];  
};  
```  
  
#### <a name="parameters"></a>参数  
 *sa_family*  
 套接字地址族。  
  
 *sa_data*  
 所有不同的套接字地址结构的最大大小。  
  
## <a name="remarks"></a>备注  
 Microsoft TCP/IP 套接字开发人员工具包仅支持 Internet 地址域。 若要实际上填写地址的每个部分的值，请使用专用于此地址格式的 `SOCKADDR_IN` 数据结构。 `SOCKADDR` 和 `SOCKADDR_IN` 数据结构具有相同的大小。 您只需进行强制转换即可在两种结构类型之间切换。  
  
## <a name="requirements"></a>要求  
 **标头︰** winsock2.h  
  
## <a name="see-also"></a>另请参阅  
 [结构、 样式、 回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [SOCKADDR_IN 结构](../../mfc/reference/sockaddr-in-structure.md)   
 [CAsyncSocket::Create](../../mfc/reference/casyncsocket-class.md#create)   
 [CSocket::Create](../../mfc/reference/csocket-class.md#create)


