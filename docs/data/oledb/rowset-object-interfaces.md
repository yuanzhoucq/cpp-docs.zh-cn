---
title: "行集合对象接口 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- interfaces, OLE DB
- OLE DB, interfaces
- rowset objects [OLE DB]
- OLE DB provider templates, object interfaces
- interfaces, list of
ms.assetid: 0d7a5d48-2fe4-434f-a84b-157c1fdc3494
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ab4bfa2a39b89dbfaced859bc241e5c002c620bb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="rowset-object-interfaces"></a>行集合对象接口
下表显示由 OLE DB 行集对象定义的必需和可选接口。  
  
|接口|是否必需？|实现的 OLE DB 模板？|  
|---------------|---------------|--------------------------------------|  
|[IAccessor](https://msdn.microsoft.com/en-us/library/ms719672.aspx)|强制|是|  
|[IColumnsInfo](https://msdn.microsoft.com/en-us/library/ms724541.aspx)|强制|是|  
|[IConvertType](https://msdn.microsoft.com/en-us/library/ms715926.aspx)|强制|是|  
|[IRowset](https://msdn.microsoft.com/en-us/library/ms720986.aspx)|强制|是|  
|[IRowsetInfo](https://msdn.microsoft.com/en-us/library/ms724541.aspx)|强制|是|  
|[IChapteredRowset](https://msdn.microsoft.com/en-us/library/ms718180.aspx)|Optional|No|  
|[IColumnsInfo2](https://msdn.microsoft.com/en-us/library/ms712953.aspx)|Optional|No|  
|[IColumnsRowset](https://msdn.microsoft.com/en-us/library/ms722657.aspx)|Optional|No|  
|[IConnectionPointContainer](http://msdn.microsoft.com/library/windows/desktop/ms683857)|Optional|是 （通过 ATL)|  
|[IDBAsynchStatus](https://msdn.microsoft.com/en-us/library/ms709832.aspx)|Optional|No|  
|[IGetRow](https://msdn.microsoft.com/en-us/library/ms718047.aspx)|Optional|No|  
|[IRowsetChange](https://msdn.microsoft.com/en-us/library/ms715790.aspx)|Optional|是|  
|[IRowsetChapterMember](https://msdn.microsoft.com/en-us/library/ms725430.aspx)|Optional|No|  
|[IRowsetCurrentIndex](https://msdn.microsoft.com/en-us/library/ms709700.aspx)|Optional|No|  
|[IRowsetFind](https://msdn.microsoft.com/en-us/library/ms724221.aspx)|Optional|No|  
|[IRowsetIdentity](https://msdn.microsoft.com/en-us/library/ms715913.aspx)|可选 （但对于级别 0 提供程序为必需）|是|  
|[IRowsetIndex](https://msdn.microsoft.com/en-us/library/ms719604.aspx)|Optional|No|  
|[IRowsetLocate](https://msdn.microsoft.com/en-us/library/ms721190.aspx)|Optional|是|  
|[IRowsetRefresh](https://msdn.microsoft.com/en-us/library/ms714892.aspx)|Optional|No|  
|[IRowsetScroll](https://msdn.microsoft.com/en-us/library/ms712984.aspx)|Optional|No|  
|[IRowsetUpdate](https://msdn.microsoft.com/en-us/library/ms714401.aspx)|Optional|是|  
|[IRowsetView](https://msdn.microsoft.com/en-us/library/ms709755.aspx)|Optional|No|  
|[ISupportErrorInfo](https://msdn.microsoft.com/en-us/library/ms715816.aspx)|Optional|是|  
|[IRowsetBookmark](https://msdn.microsoft.com/en-us/library/ms714246.aspx)|Optional|No|  
  
 向导生成行集对象实现`IAccessor`， `IRowset`，和`IRowsetInfo`通过继承。 `IAccessorImpl`将这两个输出列绑定。 `IRowset`接口处理提取行和数据。 `IRowsetInfo`接口处理的行集属性。  
  
## <a name="see-also"></a>另请参阅  
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)