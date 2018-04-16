---
title: "用户定义的处理程序 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.handlers
dev_langs:
- C++
helpviewer_keywords:
- ON_REGISTERED_MESSAGE macro [MFC]
- ON_MESSAGE macro [MFC]
- user-defined handlers [MFC]
ms.assetid: 99478294-bef0-4ba7-a369-25a6abdcdb62
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b276ea546d5940b78090a99f36c953afe62a67fb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="user-defined-handlers"></a>用户定义的处理程序
下面的映射条目对应的函数原型。  
  
|映射条目|函数原型|  
|---------------|------------------------|  
|ON_MESSAGE (\<消息 >， \<f x n >)|afx_msg LRESULT f x n （WPARAM，LPARAM）;|  
|ON_REGISTERED_MESSAGE ( \<nMessageVariable >， \<f x n >)|afx_msg LRESULT f x n （WPARAM，LPARAM）;|  
|ON_THREAD_MESSAGE (\<消息 >， \<f x n >)|afx_msg void f x n （WPARAM，LPARAM）;|  
|ON_REGISTERED_THREAD_MESSAGE ( \<nMessageVariable >， \<f x n >)|afx_msg void f x n （WPARAM，LPARAM）;|  
  
## <a name="see-also"></a>请参阅  
 [消息映射](../../mfc/reference/message-maps-mfc.md)   
 [WM_ 消息的处理程序](../../mfc/reference/handlers-for-wm-messages.md)

