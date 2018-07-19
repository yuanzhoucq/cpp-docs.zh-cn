---
title: ATL 连接点 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- connections, connection points
- ATL, connection points
- connection points [C++], about connection points
ms.assetid: 17d76165-5f83-4f95-b36d-483821c247a1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 179f4329d55261d71d3d122e6a2601ce7e805c0f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32354663"
---
# <a name="atl-connection-points"></a>ATL 连接点
可连接对象是支持输出接口的对象。 输出接口允许对象与客户端进行通信。 对于每个输出接口，可连接对象都释放一个连接点。 每个输出接口是由调用接收器的对象上的客户端实现的。  
  
 ![连接点](../atl/media/vc2zw31.gif "vc2zw31")  
  
 每个连接点支持[IConnectionPoint](http://msdn.microsoft.com/library/windows/desktop/ms694318)接口。 可连接对象公开其通过客户端的连接点[IConnectionPointContainer](http://msdn.microsoft.com/library/windows/desktop/ms683857)接口。  
  
## <a name="in-this-section"></a>本节内容  
 [ATL 连接点类](../atl/atl-connection-point-classes.md)  
 简要介绍支持连接点的 ATL 类。  
  
 [将连接点添加到对象](../atl/adding-connection-points-to-an-object.md)  
 概述了用于将连接点添加到对象的步骤。  
  
 [ATL 连接点示例](../atl/atl-connection-point-example.md)  
 提供了声明连接点的一个示例。  
  
## <a name="related-sections"></a>相关章节  
 [ATL](../atl/active-template-library-atl-concepts.md)  
 提供了关于如何使用 Active Template Library 进行编程的概念性主题的链接。  
  
## <a name="see-also"></a>请参阅  
 [概念](../atl/active-template-library-atl-concepts.md)

