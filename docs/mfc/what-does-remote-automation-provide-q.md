---
title: "远程自动化提供什么？ | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: Remote Automation, DCOM
ms.assetid: 269ad218-e164-40ef-9b87-25fcc8ba21de
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a4a82b26a1e6c208a584dfd19ebfd4530b4bdf76
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="what-does-remote-automation-provide"></a>远程自动化提供什么？
远程自动化允许程序从一台计算机到另一台计算机上调用 `IDispatch` 实现。 它还支持自动化需要的具体而言其他接口**IEnumVARIANT**用于集合支持。 它不提供分发任何其他 COM 接口的功能 (除**IUnknown**，这是当然的) 而且像常规自动化一样，它包含仅对自动化支持的那些数据类型的封送支持。  
  
 这组功能允许程序访问方法和属性，包括返回在可访问网络节点上运行的对象的集合或更多自动化对象的方法和属性。 如果客户端计算机也运行相应的软件，则服务器可能会回调客户端，并再次使用自动化功能（这仅适用于 32 位和 64 位客户端，并且在概念上与事件类似，但它不使用相同的机制）。  
  
 对于可作为远程自动化服务器操作的应用程序，它必须作为可执行程序实现（也就是说，作为“本地服务器”而不是“进程内服务器”）。  
  
## <a name="see-also"></a>请参阅  
 [远程自动化放置何处](where-does-remote-automation-fit-in-q.md)   
 [DCOM 历史记录](../mfc/history-of-dcom.md)
