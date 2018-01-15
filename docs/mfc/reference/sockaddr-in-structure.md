---
title: "SOCKADDR_IN 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SOCKADDR_IN
dev_langs: C++
helpviewer_keywords: SOCKADDR_IN structure [MFC]
ms.assetid: e8cd7c34-78bd-4e28-a990-eb3ca070b7a6
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9e5350e48570a564361328e7b666a1cbb976221a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="sockaddrin-structure"></a>SOCKADDR_IN 结构
在 Internet 地址系列中， `SOCKADDR_IN` Windows 套接字使用结构来指定要连接套接字的本地或远程终结点地址。  
  
## <a name="syntax"></a>语法  
  
```  
struct sockaddr_in{  
    short sin_family;  
    unsigned short sin_port;  
struct in_addr sin_addr;  
    char sin_zero[8];  
};  
```  
  
#### <a name="parameters"></a>参数  
 *sin_family*  
 地址系列 (必须是**AF_INET**)。  
  
 *sin_port*  
 IP 端口。  
  
 *sin_addr*  
 IP 地址。  
  
 *sin_zero*  
 填充以使大小相同的结构`SOCKADDR`。  
  
## <a name="remarks"></a>备注  
 此窗体中的`SOCKADDR`结构特定于 Internet 地址族，和可以强制转换为`SOCKADDR`。  
  
 组件的此结构的 IP 地址属于类型**IN_ADDR**。 **IN_ADDR** Windows 套接字头文件 WINSOCK 中定义结构。H，如下所示：  
  
```  
struct in_addr {
    union {
        struct {  
            unsigned char s_b1, s_b2, s_b3, s_b4;  
        } S_un_b;  
        struct {  
            unsigned short s_w1, s_w2;
        } S_un_w;
        unsigned long S_addr;
    } S_un;  
};  
```  
  
## <a name="requirements"></a>惠?  
 **标头：** winsock2.h  
  
## <a name="see-also"></a>请参阅  
 [结构、 样式、 回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [SOCKADDR 结构](../../mfc/reference/sockaddr-structure.md)
