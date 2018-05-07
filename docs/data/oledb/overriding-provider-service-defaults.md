---
title: 重写提供程序服务默认值 |Microsoft 文档
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
ms.openlocfilehash: be802c1c3c6ba4b77d1418c9c620840e9ab10170
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="overriding-provider-service-defaults"></a>重写提供程序服务默认值
提供程序的注册表值以查找**OLEDB_SERVICES**返回的默认值为[DBPROP_INIT_OLEDBSERVICES](https://msdn.microsoft.com/en-us/library/ms716898.aspx)数据源对象上的初始化属性。  
  
 只要存在注册表项，则提供程序的对象聚合的用户可以重写提供程序的默认设置为启用的服务通过设置**DBPROP_INIT_OLEDBSERVICES**在初始化之前的属性。 若要启用或禁用特定服务，用户通常获取的当前值**DBPROP_INIT_OLEDBSERVICES**属性，设置或清除要启用或禁用，所有的特定属性的位，并重置属性。 **DBPROP_INIT_OLEDBSERVICES**可以直接在 OLE DB 或传递给 ADO 连接字符串中设置或**IDataInitialize::GetDatasource**。 下表列出了相应的值以启用/禁用个别服务。  
  
|启用默认服务|DBPROP_INIT_OLEDBSERVICES 属性值|连接字符串中的值|  
|------------------------------|------------------------------------------------|--------------------------------|  
|所有服务 （默认值）|**DBPROPVAL_OS_ENABLEALL**|"OLE DB 服务 =-1;"|  
|除池和登记|**DBPROPVAL_OS_ENABLEALL （&AMP; A)**<br /><br /> **~ DBPROPVAL_OS_RESOURCEPOOLING （&AMP; A)**<br /><br /> **~DBPROPVAL_OS_TXNENLISTMENT**|"OLE DB 服务 =-4;"|  
|除客户端游标|**DBPROPVAL_OS_ENABLEALL** &<br /><br /> ~**DBPROPVAL_OS_CLIENTCURSOR**|"OLE DB 服务 =-5;"|  
|除池，自动登记和客户端游标|**DBPROPVAL_OS_ENABLEALL （&AMP; A)**<br /><br /> **~ DBPROPVAL_OS_TXNENLISTMENT （&AMP; A)**<br /><br /> **~DBPROPVAL_OS_CLIENTCURSOR**|"OLE DB 服务 =-7;"|  
|没有任何服务|~**DBPROPVAL_OS_ENABLEALL**|"OLE DB 服务 = 0;"|  
  
 如果注册表项不存在的提供程序，组件管理器将不会聚合该提供程序的对象，并将调用任何服务，即使用户显式请求。  
  
## <a name="see-also"></a>请参阅  
 [资源池](https://msdn.microsoft.com/en-us/library/ms713655.aspx)   
 [使用者如何使用资源池](https://msdn.microsoft.com/en-us/library/ms715907.aspx)   
 [提供程序如何有效地使用资源池](https://msdn.microsoft.com/en-us/library/ms714906.aspx)   
 [启用和禁用 OLE DB 服务](../../data/oledb/enabling-and-disabling-ole-db-services.md)