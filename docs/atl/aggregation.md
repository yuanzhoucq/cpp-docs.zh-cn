---
title: 聚合 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- aggregation [C++]
- aggregate objects [C++]
ms.assetid: 7125bb8e-b269-4b50-9bba-295b467a54cc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 760a595274ba7a1901138cc0cceceddf97122725
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="aggregation"></a>聚合
有对象的实现者希望充分利用预构建的另一个对象提供的服务的时间。 此外，它想要此第二个对象，以显示为第一个自然一部分。 COM 达到这两个目标通过包容和聚合。  
  
 聚合意味着在包含的 （外部） 对象作为其创建过程的一部分创建包含 （内部） 对象的接口的内部对象公开的外部。 对象允许对自身或不是可聚合。 如果是，它必须遵循特定的规则的聚合来正常工作。  
  
 主要原因是，所有**IUnknown**上包含的对象的方法调用必须委托到包含的对象。  
  
## <a name="see-also"></a>请参阅  
 [COM 简介](../atl/introduction-to-com.md)   
 [重复使用对象](http://msdn.microsoft.com/library/windows/desktop/ms678443)

