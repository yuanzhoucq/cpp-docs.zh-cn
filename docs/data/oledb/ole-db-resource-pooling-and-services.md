---
title: OLE DB 资源池和服务
ms.date: 10/29/2018
helpviewer_keywords:
- resource pooling [OLE DB], provider requirements
- OLE DB, resource pooling
- service providers [OLE DB]
- OLE DB services [OLE DB], provider requirements
- OLE DB services [OLE DB]
- OLE DB providers, resource pooling
ms.assetid: 360c36e2-25ae-4caf-8ee7-d4a6b6898f68
ms.openlocfilehash: 1fb5164b9e744175f60c920a1d92278e9d5213f2
ms.sourcegitcommit: 943c792fdabf01c98c31465f23949a829eab9aad
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2018
ms.locfileid: "51264653"
---
# <a name="ole-db-resource-pooling-and-services"></a>OLE DB 资源池和服务

若要运行于 OLE DB 池，或使用任何 OLE DB 服务，您的提供程序必须支持的所有对象的聚合。 这是任何 OLE DB 1.5 或更高版本的提供程序的要求。 它对于利用服务至关重要。 不能共用提供程序不支持聚合并不提供任何其他服务。

若要建立池连接，提供程序必须支持自由线程模型。 资源池确定根据 DBPROP_THREADMODEL 属性的提供程序的线程模型。

如果该提供程序可能会更改数据源处于初始化状态时的全局连接状态，它应支持新的 DBPROP_RESETDATASOURCE 属性。 此属性称为之前的连接重复使用和使提供程序有机会清理其下一步使用之前的状态。 如果提供程序不能清除与连接关联的某些状态，它可以将返回的属性并不会重复使用连接。

提供程序连接到远程数据库，可以检测到该连接是否可能会丢失应支持 DBPROP_CONNECTIONSTATUS 属性。 此属性使 OLE DB 服务能够检测到死信连接，并确保它们不返回到池中。

最后，自动事务登记通常不起作用除非池发生级别实现。 支持自动事务登记的提供程序应支持通过公开 DBPROP_INIT_OLEDBSERVICES 属性和禁用登记，如果 DBPROPVAL_OS_TXNENLISTMENT 取消选择禁用此登记。

## <a name="see-also"></a>请参阅

[高级提供程序技术](../../data/oledb/advanced-provider-techniques.md)