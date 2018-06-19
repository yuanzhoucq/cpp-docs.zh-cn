---
title: 行集合对象接口 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- interfaces, OLE DB
- OLE DB, interfaces
- rowset objects [OLE DB]
- OLE DB provider templates, object interfaces
- interfaces, list of
ms.assetid: 0d7a5d48-2fe4-434f-a84b-157c1fdc3494
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: aaed092d0a67c80852216b6342d32820c7028c4b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33112753"
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
|[IChapteredRowset](https://msdn.microsoft.com/en-us/library/ms718180.aspx)|Optional|否|  
|[IColumnsInfo2](https://msdn.microsoft.com/en-us/library/ms712953.aspx)|Optional|否|  
|[IColumnsRowset](https://msdn.microsoft.com/en-us/library/ms722657.aspx)|Optional|否|  
|[IConnectionPointContainer](http://msdn.microsoft.com/library/windows/desktop/ms683857)|Optional|是 （通过 ATL)|  
|[IDBAsynchStatus](https://msdn.microsoft.com/en-us/library/ms709832.aspx)|Optional|否|  
|[IGetRow](https://msdn.microsoft.com/en-us/library/ms718047.aspx)|Optional|否|  
|[IRowsetChange](https://msdn.microsoft.com/en-us/library/ms715790.aspx)|Optional|是|  
|[IRowsetChapterMember](https://msdn.microsoft.com/en-us/library/ms725430.aspx)|Optional|否|  
|[IRowsetCurrentIndex](https://msdn.microsoft.com/en-us/library/ms709700.aspx)|Optional|否|  
|[IRowsetFind](https://msdn.microsoft.com/en-us/library/ms724221.aspx)|Optional|否|  
|[IRowsetIdentity](https://msdn.microsoft.com/en-us/library/ms715913.aspx)|可选 （但对于级别 0 提供程序为必需）|是|  
|[IRowsetIndex](https://msdn.microsoft.com/en-us/library/ms719604.aspx)|Optional|否|  
|[IRowsetLocate](https://msdn.microsoft.com/en-us/library/ms721190.aspx)|Optional|是|  
|[IRowsetRefresh](https://msdn.microsoft.com/en-us/library/ms714892.aspx)|Optional|否|  
|[IRowsetScroll](https://msdn.microsoft.com/en-us/library/ms712984.aspx)|Optional|否|  
|[IRowsetUpdate](https://msdn.microsoft.com/en-us/library/ms714401.aspx)|Optional|是|  
|[IRowsetView](https://msdn.microsoft.com/en-us/library/ms709755.aspx)|Optional|否|  
|[ISupportErrorInfo](https://msdn.microsoft.com/en-us/library/ms715816.aspx)|Optional|是|  
|[IRowsetBookmark](https://msdn.microsoft.com/en-us/library/ms714246.aspx)|Optional|否|  
  
 向导生成行集对象实现`IAccessor`， `IRowset`，和`IRowsetInfo`通过继承。 `IAccessorImpl`将这两个输出列绑定。 `IRowset`接口处理提取行和数据。 `IRowsetInfo`接口处理的行集属性。  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)