---
title: SOCKADDR 结构
ms.date: 11/04/2016
f1_keywords:
- SOCKADDR
helpviewer_keywords:
- SOCKADDR structure [MFC]
ms.assetid: df1ed66a-f4b8-43f8-8db8-8c2533d25f68
ms.openlocfilehash: 68d5261c6520b5baee8495b72a0b9d234a35a185
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50543840"
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

*sa_family*<br/>
套接字地址族。

*sa_data*<br/>
所有不同的套接字地址结构的最大大小。

## <a name="remarks"></a>备注

Microsoft TCP/IP 套接字开发人员工具包仅支持 Internet 地址域。 若要实际上填写地址的每个部分的值，请使用专用于此地址格式的 `SOCKADDR_IN` 数据结构。 `SOCKADDR` 和 `SOCKADDR_IN` 数据结构具有相同的大小。 您只需进行强制转换即可在两种结构类型之间切换。

## <a name="requirements"></a>要求

**标头：** winsock2.h

## <a name="see-also"></a>请参阅

[结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[SOCKADDR_IN 结构](../../mfc/reference/sockaddr-in-structure.md)<br/>
[CAsyncSocket::Create](../../mfc/reference/casyncsocket-class.md#create)<br/>
[CSocket::Create](../../mfc/reference/csocket-class.md#create)

