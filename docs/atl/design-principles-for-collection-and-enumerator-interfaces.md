---
title: 设计集合和枚举器接口 (ATL) |Microsoft Docs
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
ms.openlocfilehash: ab8b42804ca892c80971928b869e09ccdf479d68
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/05/2018
ms.locfileid: "37851322"
---
# <a name="design-principles-for-collection-and-enumerator-interfaces"></a>集合和枚举器接口的设计原则
有每种类型的接口不同的设计原则：  
  
-   集合接口提供了*随机*访问权限*单个*通过集合中的项`Item`方法，它可让客户端发现通过集合中有多少项`Count`属性，并通常允许客户端添加和删除项。  
  
-   枚举器接口提供了*串行*访问权限*多个*集合中的项，它不允许客户端能够发现 （直到枚举器停止返回集合中有多少项项），并且它不提供任何办法来添加或删除项。  
  
 每种类型的接口扮演不同的角色提供对集合中元素的访问。  
  
## <a name="see-also"></a>请参阅  
 [集合和枚举数](../atl/atl-collections-and-enumerators.md)

