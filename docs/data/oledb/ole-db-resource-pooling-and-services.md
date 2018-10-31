---
title: OLE DB 资源池和服务 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- resource pooling [OLE DB], provider requirements
- OLE DB, resource pooling
- service providers [OLE DB]
- OLE DB services [OLE DB], provider requirements
- OLE DB services [OLE DB]
- OLE DB providers, resource pooling
ms.assetid: 360c36e2-25ae-4caf-8ee7-d4a6b6898f68
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a90f60f830b4d5ec98685dbd8cd1c573d0fbcb4e
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50070291"
---
# <a name="ole-db-resource-pooling-and-services"></a>OLE DB 资源池和服务

若要运行于 OLE DB 池，或使用任何 OLE DB 服务，您的提供程序必须支持的所有对象的聚合。 这是任何 OLE DB 1.5 或更高版本的提供程序的要求。 它对于利用服务至关重要。 不支持聚合的提供程序不能共用并不提供任何其他服务。

若要建立池连接，提供程序必须支持自由线程模型。 资源池决定根据提供程序的线程模型`DBPROP_THREADMODEL`属性。

如果该提供程序可能会更改数据源处于初始化状态时的全局连接状态，则它应支持新`DBPROP_RESETDATASOURCE`属性。 此属性称为之前的连接重复使用和使提供程序有机会清理其下一步使用之前的状态。 如果提供程序不能清除与连接关联的某些状态，它可以返回`DBPROPSTATUS_NOTSETTABLE`的属性和连接将不能重复使用。

提供程序连接到远程数据库，可以检测是否应支持连接可能会丢失`DBPROP_CONNECTIONSTATUS`属性。 此属性使 OLE DB 服务能够检测到死信连接，并确保它们不会返回到池。

最后，除非它池发生级别实现自动事务登记通常无法运行。 本身支持自动事务登记的提供程序应支持通过公开禁用此登记`DBPROP_INIT_OLEDBSERVICES`属性，如果禁用登记`DBPROPVAL_OS_TXNENLISTMENT`已取消选择。

## <a name="see-also"></a>请参阅

[高级提供程序技术](../../data/oledb/advanced-provider-techniques.md)