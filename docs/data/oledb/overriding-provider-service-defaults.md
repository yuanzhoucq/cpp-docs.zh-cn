---
title: 重写提供程序服务默认值
ms.date: 10/29/2018
helpviewer_keywords:
- service providers [OLE DB]
- OLE DB services [OLE DB], overriding defaults
ms.assetid: 08e366c0-74d8-463b-93a6-d58a8dc195f8
ms.openlocfilehash: a9f8eb1c96c40336f39f14fe1a0ee29d60efd003
ms.sourcegitcommit: 943c792fdabf01c98c31465f23949a829eab9aad
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2018
ms.locfileid: "51265212"
---
# <a name="overriding-provider-service-defaults"></a>重写提供程序服务默认值

OLEDB_SERVICES 的提供程序的注册表值返回的默认值为[DBPROP_INIT_OLEDBSERVICES](/previous-versions/windows/desktop/ms716898)的数据源对象的初始化属性。

只要存在注册表项，聚合提供程序的对象。 用户可以重写提供程序的默认设置已启用的服务通过之前初始化 DBPROP_INIT_OLEDBSERVICES 属性设置。 若要启用或禁用特定服务，用户会获取 DBPROP_INIT_OLEDBSERVICES 属性的当前值、 设置或清除要启用或禁用、 特定属性的位和属性重置。 可以直接在 OLE DB 中或传递到 ADO 连接字符串中设置 DBPROP_INIT_OLEDBSERVICES 或`IDataInitialize::GetDatasource`。 下表中列出的相应值以启用/禁用各项服务。

|启用的默认服务|DBPROP_INIT_OLEDBSERVICES 属性值|连接字符串中的值|
|------------------------------|------------------------------------------------|--------------------------------|
|所有服务 （默认值）|DBPROPVAL_OS_ENABLEALL|"OLE DB 服务 =-1;"|
|除池和登记|`DBPROPVAL_OS_ENABLEALL &`<br /><br /> `~DBPROPVAL_OS_RESOURCEPOOLING &`<br /><br /> `~DBPROPVAL_OS_TXNENLISTMENT`|"OLE DB 服务 =-4;"|
|除客户端游标|`DBPROPVAL_OS_ENABLEALL &`<br /><br /> `~DBPROPVAL_OS_CLIENTCURSOR`|"OLE DB 服务 =-5;"|
|除池，登记和客户端游标|`DBPROPVAL_OS_ENABLEALL &`<br /><br /> `~DBPROPVAL_OS_TXNENLISTMENT &`<br /><br /> `~DBPROPVAL_OS_CLIENTCURSOR`|"OLE DB 服务 =-7;"|
|没有服务|`~DBPROPVAL_OS_ENABLEALL`|"OLE DB 服务 = 0;"|

如果提供程序不存在的注册表项，则组件管理器不会收集提供程序的对象。 任何服务将会不打开，即使用户显式请求。

## <a name="see-also"></a>请参阅

[资源池](/previous-versions/windows/desktop/ms713655)<br/>
[使用者如何使用资源池](/previous-versions/windows/desktop/ms715907)<br/>
[提供程序如何有效地使用资源池](/previous-versions/windows/desktop/ms714906)<br/>
[启用和禁用 OLE DB 服务](../../data/oledb/enabling-and-disabling-ole-db-services.md)<br/>