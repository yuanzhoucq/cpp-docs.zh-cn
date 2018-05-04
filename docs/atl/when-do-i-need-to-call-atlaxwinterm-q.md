---
title: 何时需要调用 AtlAxWinTerm？ | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- AtlAxWinTerm
dev_langs:
- C++
helpviewer_keywords:
- AtlAxWinTerm method
ms.assetid: 0088d494-2d8d-45b4-b582-2af726bd6cbd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 61830023d3fb67d331784769f32cda4eee8355b5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="when-do-i-need-to-call-atlaxwinterm"></a>何时需要调用 AtlAxWinTerm？
[AtlAxWinTerm](reference/composite-control-global-functions.md#atlaxwinterm)注销 **"AtlAxWin80"** 窗口类。 所有现有主机窗口已销毁之后，都应 （如果不再需要创建宿主窗口） 调用此函数。 如果你不调用此函数，窗口类将自动取消注册在进程终止时。  
  
## <a name="see-also"></a>请参阅  
 何时需要调用 AtlAxWinInit  
[控件包含常见问题](../atl/atl-control-containment-faq.md)

