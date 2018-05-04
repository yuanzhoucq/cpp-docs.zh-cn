---
title: 可以承载单个窗口中的多个控件？ | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [ATL], hosting multiple
- windows [C++], hosting multiple controls
ms.assetid: 3a967a1a-7e7e-42e3-8eed-f7bde912363f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ceb9444b6371e261115bbf52ef5a249100772d1f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="can-i-host-more-than-one-control-in-a-single-window"></a>可以承载单个窗口中的多个控件？
不可以承载多个控件中单个 ATL 主机窗口。 每个主机窗口旨在 （它支持简单的机制，用于处理消息反射和每个控件环境属性） 一次存放一个控件。 但是，如果你需要用户查看单个窗口中的多个控件，它是一个简单来创建作为该窗口的子级的多个主机窗口。  
  
## <a name="see-also"></a>请参阅  
 [控件包含常见问题](../atl/atl-control-containment-faq.md)

