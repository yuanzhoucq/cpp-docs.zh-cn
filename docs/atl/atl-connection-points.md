---
title: ATL 连接点 |Microsoft Docs
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
ms.openlocfilehash: fe2cf03debbfd88f19ccc77d3922a9a5c50a50d2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46091265"
---
# <a name="atl-connection-points"></a>ATL 连接点

可连接对象是支持输出接口的对象。 输出接口允许对象与客户端进行通信。 对于每个输出接口，可连接对象都释放一个连接点。 每个输出接口是由调用接收器的对象上的客户端实现的。

![连接点](../atl/media/vc2zw31.gif "vc2zw31")

每个连接点支持[IConnectionPoint](/windows/desktop/api/ocidl/nn-ocidl-iconnectionpoint)接口。 可连接对象会公开到客户端通过其连接点[IConnectionPointContainer](/windows/desktop/api/ocidl/nn-ocidl-iconnectionpointcontainer)接口。

## <a name="in-this-section"></a>本节内容

[ATL 连接点类](../atl/atl-connection-point-classes.md)<br/>
简要介绍支持连接点的 ATL 类。

[将连接点添加到对象](../atl/adding-connection-points-to-an-object.md)<br/>
概述了用于将连接点添加到对象的步骤。

[ATL 连接点示例](../atl/atl-connection-point-example.md)<br/>
提供了声明连接点的一个示例。

## <a name="related-sections"></a>相关章节

[ATL](../atl/active-template-library-atl-concepts.md)<br/>
提供了关于如何使用 Active Template Library 进行编程的概念性主题的链接。

## <a name="see-also"></a>请参阅

[概念](../atl/active-template-library-atl-concepts.md)

