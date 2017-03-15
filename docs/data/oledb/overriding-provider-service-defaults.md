---
title: "重写提供程序服务默认值 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OLE DB 服务 [OLE DB], 重写默认值"
  - "服务提供程序 [OLE DB]"
ms.assetid: 08e366c0-74d8-463b-93a6-d58a8dc195f8
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 重写提供程序服务默认值
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供程序的 **OLEDB\_SERVICES** 注册表值作为数据源对象上的 [DBPROP\_INIT\_OLEDBSERVICES](https://msdn.microsoft.com/en-us/library/ms716898.aspx) 初始化属性的默认值返回。  
  
 只要注册表项存在，提供程序的对象就将聚合，并且用户可以通过在初始化前设置 **DBPROP\_INIT\_OLEDBSERVICES** 属性，为启用的服务重写提供程序的默认设置。  为了启用或禁用特定的服务，用户通常需要获取 **DBPROP\_INIT\_OLEDBSERVICES** 属性的当前值，设置或清除要启用或禁用的特定属性的位并重置属性。  可以直接在 OLE DB 中或在传递到 ADO 或 **IDataInitialize::GetDatasource** 的连接字符串中设置 **DBPROP\_INIT\_OLEDBSERVICES**。  下表列出了启用\/禁用各服务的对应值。  
  
|启用的默认服务|DBPROP\_INIT\_OLEDBSERVICES 属性值|连接字符串中的值|  
|-------------|-------------------------------------|--------------|  
|所有服务（默认）|**DBPROPVAL\_OS\_ENABLEALL**|"OLE DB Services \= \-1;"|  
|除“池”和“自动登记”外的所有服务|**DBPROPVAL\_OS\_ENABLEALL &**<br /><br /> **~DBPROPVAL\_OS\_RESOURCEPOOLING &**<br /><br /> **~DBPROPVAL\_OS\_TXNENLISTMENT**|"OLE DB Services \= \-4;"|  
|除“客户端光标”外的所有服务|**DBPROPVAL\_OS\_ENABLEALL** &<br /><br /> ~**DBPROPVAL\_OS\_CLIENTCURSOR**|"OLE DB Services \= \-5;"|  
|除“池”、“自动登记”和“客户端光标”外的所有服务|**DBPROPVAL\_OS\_ENABLEALL &**<br /><br /> **~DBPROPVAL\_OS\_TXNENLISTMENT &**<br /><br /> **~DBPROPVAL\_OS\_CLIENTCURSOR**|"OLE DB Services \= \-7;"|  
|没有服务|~**DBPROPVAL\_OS\_ENABLEALL**|"OLE DB Services \= 0;"|  
  
 如果提供程序的注册表项不存在，组件管理器将不聚合提供程序的对象，并且将没有服务被调用，即使用户显式请求。  
  
## 请参阅  
 [Resource Pooling](https://msdn.microsoft.com/en-us/library/ms713655.aspx)   
 [How Consumers Use Resource Pooling](https://msdn.microsoft.com/en-us/library/ms715907.aspx)   
 [How Providers Work Effectively with Resource Pooling](https://msdn.microsoft.com/en-us/library/ms714906.aspx)   
 [启用和禁用 OLE DB 服务](../../data/oledb/enabling-and-disabling-ole-db-services.md)