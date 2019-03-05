---
title: Windows 套接字：数据报套接字
ms.date: 11/04/2016
helpviewer_keywords:
- sockets [MFC], datagram
- Windows Sockets [MFC], bi-directional data flow
- datagram sockets [MFC]
- Windows Sockets [MFC], datagram
- sockets [MFC], bi-directional data flow
ms.assetid: bec16a1c-74c0-4ff9-8c18-c2d87897d264
ms.openlocfilehash: 14d33ece66d902b5705e573e9863ea78fff9737f
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57266786"
---
# <a name="windows-sockets-datagram-sockets"></a>Windows 套接字：数据报套接字

本文介绍数据报套接字，可用的两个 Windows 套接字类型之一。 (另一种类型是[流套接字](../mfc/windows-sockets-stream-sockets.md)。)

数据报套接字支持双向数据流不保证按顺序和不重复。 数据报也不保证能够可靠;它们可能无法到达。 数据报数据可能会到达顺序并且可能会重复，但前提是接收方的内部大小限制比小的记录将会保留记录边界的数据中。 你负责管理序列化和可靠性。 （可靠性往往是本地区域网络 [LAN] 上很好但更少，在广域网络 [WAN]，如 Internet）

数据报"无连接"，即建立显式连接;将数据报消息发送到指定套接字和可以从指定套接字接收消息。

数据报套接字的示例是保持系统时钟同步在网络的应用程序。 这说明了一项额外功能的一些设置中的数据报套接字： 将消息广播到大量的网络地址。

数据报套接字要优于面向记录的数据的流套接字。 有关数据报套接字的详细信息，请参阅 Windows SDK 中提供的 Windows 套接字规范。

## <a name="see-also"></a>请参阅

[MFC 中的 Windows 套接字](../mfc/windows-sockets-in-mfc.md)<br/>
[Windows 套接字：背景](../mfc/windows-sockets-background.md)
