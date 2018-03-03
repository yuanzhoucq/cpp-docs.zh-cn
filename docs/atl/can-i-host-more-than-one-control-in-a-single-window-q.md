---
title: "可以承载单个窗口中的多个控件？ | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- controls [ATL], hosting multiple
- windows [C++], hosting multiple controls
ms.assetid: 3a967a1a-7e7e-42e3-8eed-f7bde912363f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: be87c0bad9ab250593847cc24d16158030040054
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="can-i-host-more-than-one-control-in-a-single-window"></a>可以承载单个窗口中的多个控件？
不可以承载多个控件中单个 ATL 主机窗口。 每个主机窗口旨在 （它支持简单的机制，用于处理消息反射和每个控件环境属性） 一次存放一个控件。 但是，如果你需要用户查看单个窗口中的多个控件，它是一个简单来创建作为该窗口的子级的多个主机窗口。  
  
## <a name="see-also"></a>请参阅  
 [控件包含常见问题](../atl/atl-control-containment-faq.md)

