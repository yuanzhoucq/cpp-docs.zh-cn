---
title: "Windows 套接字类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.classes.net
dev_langs:
- C++
helpviewer_keywords:
- sockets classes [MFC]
- Windows Sockets [MFC], classes
ms.assetid: 58b9ab8d-9e44-4db3-8265-e04e713d2e9a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cea7690c9d1f754006a38c793fcd9608747c13b7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="windows-sockets-classes"></a>Windows 套接字类
Windows 套接字提供了一个在两台计算机之间进行通信的与网络协议无关的方法。 这些套接字可以是同步（你的程序等到通信完成才运行），也可以是异步的（你的程序在通信进行时继续运行）。  
  
 [CAsyncSocket](../mfc/reference/casyncsocket-class.md)  
 将 Windows 套接字封装在细包装器中。  
  
 [CSocket](../mfc/reference/csocket-class.md)  
 派生自 `CAsyncSocket` 的更高程度的抽象。 它同步运行。  
  
 [CSocketFile](../mfc/reference/csocketfile-class.md)  
 为 Windows 套接字提供 `CFile` 接口。  
  
## <a name="see-also"></a>请参阅  
 [类概述](../mfc/class-library-overview.md)

