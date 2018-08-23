---
title: 重写提供程序服务默认值 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- service providers [OLE DB]
- OLE DB services [OLE DB], overriding defaults
ms.assetid: 08e366c0-74d8-463b-93a6-d58a8dc195f8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5e54a44be0ad5b7b07311d102871e584770fc441
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2018
ms.locfileid: "42571753"
---
# <a name="overriding-provider-service-defaults"></a>重写提供程序服务默认值
OLEDB_SERVICES 的提供程序的注册表值返回的默认值为[DBPROP_INIT_OLEDBSERVICES](/previous-versions/windows/desktop/ms716898\(v=vs.85\))的数据源对象的初始化属性。  
  
 只要存在注册表项，提供程序的对象聚合的用户可以重写提供程序的默认设置已启用的服务通过设置`DBPROP_INIT_OLEDBSERVICES`之前初始化属性。 若要启用或禁用特定服务，用户通常获取的当前值`DBPROP_INIT_OLEDBSERVICES`属性，设置或清除要启用或禁用的特定属性的位并重置该属性。 `DBPROP_INIT_OLEDBSERVICES` 可以直接在 OLE DB 或 ADO 到传递的连接字符串中设置或`IDataInitialize::GetDatasource`。 下表中列出的相应值以启用/禁用各项服务。  
  
|启用的默认服务|DBPROP_INIT_OLEDBSERVICES 属性值|连接字符串中的值|  
|------------------------------|------------------------------------------------|--------------------------------|  
|所有服务 （默认值）|`DBPROPVAL_OS_ENABLEALL`|"OLE DB 服务 =-1;"|  
|除池和登记|`DBPROPVAL_OS_ENABLEALL &`<br /><br /> `~DBPROPVAL_OS_RESOURCEPOOLING &`<br /><br /> `~DBPROPVAL_OS_TXNENLISTMENT`|"OLE DB 服务 =-4;"|  
|除客户端游标|`DBPROPVAL_OS_ENABLEALL &`<br /><br /> `~DBPROPVAL_OS_CLIENTCURSOR`|"OLE DB 服务 =-5;"|  
|除池，登记和客户端游标|`DBPROPVAL_OS_ENABLEALL &`<br /><br /> `~DBPROPVAL_OS_TXNENLISTMENT &`<br /><br /> `~DBPROPVAL_OS_CLIENTCURSOR`|"OLE DB 服务 =-7;"|  
|没有服务|`~DBPROPVAL_OS_ENABLEALL`|"OLE DB 服务 = 0;"|  
  
 如果注册表项不存在提供程序中，组件管理器也不会对提供程序的对象，并将调用任何服务，即使用户显式请求。  
  
## <a name="see-also"></a>请参阅  
 [资源池](/previous-versions/windows/desktop/ms713655\(v=vs.85\))   
 [使用者如何使用资源池](/previous-versions/windows/desktop/ms715907\(v=vs.85\))   
 [提供程序如何有效地使用资源池](/previous-versions/windows/desktop/ms714906\(v=vs.85\))   
 [启用和禁用 OLE DB 服务](../../data/oledb/enabling-and-disabling-ole-db-services.md)