---
title: Windows 套接字： 数据报套接字 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- sockets [MFC], datagram
- Windows Sockets [MFC], bi-directional data flow
- datagram sockets [MFC]
- Windows Sockets [MFC], datagram
- sockets [MFC], bi-directional data flow
ms.assetid: bec16a1c-74c0-4ff9-8c18-c2d87897d264
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 30ad7cab43301ae2cb7ebcb1fb4dfa850090955d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33383937"
---
# <a name="windows-sockets-datagram-sockets"></a>Windows 套接字：数据报套接字
本指南介绍了数据报套接字，两个可用的 Windows 套接字类型之一。 (另一种类型是[流套接字](../mfc/windows-sockets-stream-sockets.md)。)  
  
 数据报套接字支持双向数据流不保证排序或不重复。 数据报也不保证是不可靠;它们可能无法到达。 数据报数据可能到达无序并且可能会重复，但将保留在数据中的记录边界，只要记录小于接收方的内部大小限制。 你负责管理序列化和可靠性。 （可靠性往往是良好的局域网网络 [LAN] 上但小于等广域网络 [WAN]，如 Internet）  
  
 数据报是"无连接"，即建立没有显式的连接;将数据报消息发送到指定的套接字，你可以从指定的套接字接收消息。  
  
 数据报套接字的示例是保留系统时钟同步在网络的应用。 这表明数据报套接字中至少一些设置的一个附加功能： 将消息广播到大量的网络地址。  
  
 数据报套接字要优于面向记录的数据的流套接字。 有关数据报套接字的详细信息，请参阅 Windows SDK 中提供的 Windows 套接字规范。  
  
## <a name="see-also"></a>请参阅  
 [MFC 中的 Windows 套接字](../mfc/windows-sockets-in-mfc.md)   
 [Windows 套接字：背景](../mfc/windows-sockets-background.md)

