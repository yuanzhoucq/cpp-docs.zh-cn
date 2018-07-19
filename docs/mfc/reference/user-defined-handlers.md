---
title: 用户定义的处理程序 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.handlers
dev_langs:
- C++
helpviewer_keywords:
- ON_REGISTERED_MESSAGE macro [MFC]
- ON_MESSAGE macro [MFC]
- user-defined handlers [MFC]
ms.assetid: 99478294-bef0-4ba7-a369-25a6abdcdb62
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8fdc8c70f7ef9bdd04bf40f408c4e014b3e3faa3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33373241"
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

