---
title: SOCKADDR_IN 结构
ms.date: 11/04/2016
f1_keywords:
- SOCKADDR_IN
helpviewer_keywords:
- SOCKADDR_IN structure [MFC]
ms.assetid: e8cd7c34-78bd-4e28-a990-eb3ca070b7a6
ms.openlocfilehash: 22d02b2e3c6fd7151e59cad0f3233539c04a16e0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50431221"
---
# <a name="sockaddrin-structure"></a>SOCKADDR_IN 结构

在 Internet 地址族， `SOCKADDR_IN` Windows 套接字使用结构来指定要连接套接字的本地或远程终结点地址。

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

*sin_family*<br/>
地址的系列 （必须是 AF_INET）。

*sin_port*<br/>
IP 端口。

*sin_addr*<br/>
IP 地址。

*sin_zero*<br/>
填充结构使大小相同`SOCKADDR`。

## <a name="remarks"></a>备注

此窗体中的`SOCKADDR`结构特定于 Internet 地址族并可转换为`SOCKADDR`。

此结构的 IP 地址组件是类型的`IN_ADDR`。 `IN_ADDR` Windows 套接字标头文件 WINSOCK 中定义结构。H，如下所示：

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

## <a name="requirements"></a>要求

**标头：** winsock2.h

## <a name="see-also"></a>请参阅

[结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[SOCKADDR 结构](../../mfc/reference/sockaddr-structure.md)
