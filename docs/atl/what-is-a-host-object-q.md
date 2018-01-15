---
title: "主机对象是什么？ (ATL) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: host objects
ms.assetid: 4f8da992-b27e-45e8-b5e0-c8b1dcae4fac
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: da735caa84c133b9cdf63fae5df8bdd3d5f774b5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="what-is-a-host-object"></a>主机对象是什么？
主机对象是一个表示由 ATL 提供特定窗口的 ActiveX 控件容器的 COM 对象。 该主机对象子类容器窗口，以便它可以反映到控件的消息，它提供了必要的容器接口用于控件，并且它公开[IAxWinHostWindow](../atl/reference/iaxwinhostwindow-interface.md)和[IAxWinAmbientDispatch](../atl/reference/iaxwinambientdispatch-interface.md)接口，以便允许你配置的环境的控件。  
  
 该主机对象可用于设置容器的环境属性。  
  
## <a name="see-also"></a>请参阅  
 [控件包含常见问题](../atl/atl-control-containment-faq.md)

