---
title: "何时需要调用 AtlAxWinTerm？ | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AtlAxWinTerm
dev_langs:
- C++
helpviewer_keywords:
- AtlAxWinTerm method
ms.assetid: 0088d494-2d8d-45b4-b582-2af726bd6cbd
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c52c5295108ef01dc23ea9f945850e91a9806d6f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="when-do-i-need-to-call-atlaxwinterm"></a>何时需要调用 AtlAxWinTerm？
[AtlAxWinTerm](reference/composite-control-global-functions.md#atlaxwinterm)注销**"AtlAxWin80"**窗口类。 所有现有主机窗口已销毁之后，都应 （如果不再需要创建宿主窗口） 调用此函数。 如果你不调用此函数，窗口类将自动取消注册在进程终止时。  
  
## <a name="see-also"></a>请参阅  
 何时需要调用 AtlAxWinInit  
[控件包含常见问题](../atl/atl-control-containment-faq.md)

