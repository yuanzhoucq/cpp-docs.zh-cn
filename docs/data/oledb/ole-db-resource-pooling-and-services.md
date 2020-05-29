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
ms.openlocfilehash: 67eeffff2bf165a5ccbdbaa546ad5b9ca9a57914
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210023"
---
# <a name="ole-db-resource-pooling-and-services"></a>OLE DB 资源池和服务

若要很好地处理 OLE DB 池或使用任何 OLE DB 服务，提供程序必须支持所有对象的聚合。 这是任何 OLE DB 1.5 或更高版本的提供程序所必需的。 这对于利用服务至关重要。 不支持聚合的提供程序不能被共用，也不提供其他服务。

若要进行汇集，提供程序必须支持自由线程模型。 资源池根据 DBPROP_THREADMODEL 属性确定提供程序的线程模型。

如果提供程序的全局连接状态可能在数据源处于已初始化状态时更改，则它应支持新的 DBPROP_RESETDATASOURCE 属性。 此属性在重新使用连接之前调用，并向提供程序提供在其下一次使用之前清理状态的机会。 如果提供程序无法清除与连接相关联的某些状态，它可能会返回属性 DBPROPSTATUS_NOTSETTABLE，且不会重复使用连接。

连接到远程数据库并可以检测该连接是否可能丢失的访问接口应支持 DBPROP_CONNECTIONSTATUS 属性。 此属性为 OLE DB 服务提供检测停滞连接的功能，并确保它们不会返回到池中。

最后，除非在池发生的相同级别实现，否则自动事务登记通常不起作用。 支持自动事务登记的提供程序应支持通过公开 DBPROP_INIT_OLEDBSERVICES 属性并在取消选择 DBPROPVAL_OS_TXNENLISTMENT 的情况下禁用登记来禁用此登记。

## <a name="see-also"></a>另请参阅

[高级提供程序技术](../../data/oledb/advanced-provider-techniques.md)
