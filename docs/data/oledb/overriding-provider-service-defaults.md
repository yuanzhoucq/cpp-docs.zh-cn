---
title: 重写提供程序服务默认值
ms.date: 10/29/2018
helpviewer_keywords:
- service providers [OLE DB]
- OLE DB services [OLE DB], overriding defaults
ms.assetid: 08e366c0-74d8-463b-93a6-d58a8dc195f8
ms.openlocfilehash: 4cf3ad1064627f64315822a5045642aa50330d10
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209781"
---
# <a name="overriding-provider-service-defaults"></a>重写提供程序服务默认值

OLEDB_SERVICES 的提供程序的注册表值作为数据源对象上[DBPROP_INIT_OLEDBSERVICES](/previous-versions/windows/desktop/ms716898(v=vs.85))初始化属性的默认值返回。

只要存在注册表项，就会聚合提供程序的对象。 用户可以通过在初始化之前设置 DBPROP_INIT_OLEDBSERVICES 属性来覆盖已启用服务的提供程序的默认设置。 若要启用或禁用某个特定的服务，用户可以获取 DBPROP_INIT_OLEDBSERVICES 属性的当前值，设置或清除要启用或禁用的特定属性的位，并重置该属性。 可以直接在 OLE DB 或传递到 ADO 或 `IDataInitialize::GetDatasource`的连接字符串中设置 DBPROP_INIT_OLEDBSERVICES。 下表列出了用于启用/禁用单个服务的相应值。

|已启用默认服务|DBPROP_INIT_OLEDBSERVICES 属性值|连接字符串中的值|
|------------------------------|------------------------------------------------|--------------------------------|
|所有服务（默认值）|DBPROPVAL_OS_ENABLEALL|"OLE DB Services =-1;"|
|除 Pooling 和 AutoEnlistment 之外的所有|`DBPROPVAL_OS_ENABLEALL &`<br /><br /> `~DBPROPVAL_OS_RESOURCEPOOLING &`<br /><br /> `~DBPROPVAL_OS_TXNENLISTMENT`|"OLE DB Services =-4;"|
|除客户端游标外的所有|`DBPROPVAL_OS_ENABLEALL &`<br /><br /> `~DBPROPVAL_OS_CLIENTCURSOR`|"OLE DB Services =-5;"|
|除池、AutoEnlistment 和客户端游标外的所有|`DBPROPVAL_OS_ENABLEALL &`<br /><br /> `~DBPROPVAL_OS_TXNENLISTMENT &`<br /><br /> `~DBPROPVAL_OS_CLIENTCURSOR`|"OLE DB Services =-7;"|
|无服务|`~DBPROPVAL_OS_ENABLEALL`|"OLE DB Services = 0;"|

如果提供程序的注册表项不存在，则组件管理器不会收集提供程序的对象。 即使用户显式请求，也不会打开任何服务。

## <a name="see-also"></a>另请参阅

[资源池](/previous-versions/windows/desktop/ms713655(v=vs.85))<br/>
[使用者如何使用资源池](/previous-versions/windows/desktop/ms715907(v=vs.85))<br/>
[提供程序如何与资源池有效地协作](/previous-versions/windows/desktop/ms714906(v=vs.85))<br/>
[启用和禁用 OLE DB 服务](../../data/oledb/enabling-and-disabling-ole-db-services.md)<br/>
