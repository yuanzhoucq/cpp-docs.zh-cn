---
title: 设计集合和枚举器接口 (ATL) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- enumerator interfaces
- collection interfaces
ms.assetid: ea19a39e-6333-41a1-be62-5435c236640e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 05649cce0e80af6f54327545cef7b663d69babf9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="design-principles-for-collection-and-enumerator-interfaces"></a>集合和枚举器接口的设计原则
有不同的设计依据每种类型的接口的原理：  
  
-   一个集合接口提供了*随机*访问*单个*通过集合中的项**项**方法，它允许发现多少项在集合中的客户端通过**计数**属性，并通常允许客户端添加和移除项。  
  
-   枚举器接口提供*串行*访问*多个*集合中的项，它不允许客户端发现多少项在集合中 （直到枚举器停止返回项），并且它不提供任何方式来添加或删除项目。  
  
 每种类型的接口扮演不同的角色提供对集合中元素的访问。  
  
## <a name="see-also"></a>请参阅  
 [集合和枚举数](../atl/atl-collections-and-enumerators.md)

