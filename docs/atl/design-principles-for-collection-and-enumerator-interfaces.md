---
title: "设计集合和枚举器接口 (ATL) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- enumerator interfaces
- collection interfaces
ms.assetid: ea19a39e-6333-41a1-be62-5435c236640e
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 40aa94226b93a42b14dfd23a64e12fff00e22729
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="design-principles-for-collection-and-enumerator-interfaces"></a>集合和枚举器接口的设计原则
有不同的设计依据每种类型的接口的原理：  
  
-   一个集合接口提供了*随机*访问*单个*通过集合中的项**项**方法，它允许发现多少项在集合中的客户端通过**计数**属性，并通常允许客户端添加和移除项。  
  
-   枚举器接口提供*串行*访问*多个*集合中的项，它不允许客户端发现多少项在集合中 （直到枚举器停止返回项），并且它不提供任何方式来添加或删除项目。  
  
 每种类型的接口扮演不同的角色提供对集合中元素的访问。  
  
## <a name="see-also"></a>另请参阅  
 [集合和枚举数](../atl/atl-collections-and-enumerators.md)

