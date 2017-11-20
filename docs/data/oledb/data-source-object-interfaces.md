---
title: "数据源对象接口 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- data source objects [C++], interfaces
- data source objects [C++]
- interfaces [C++], OLE DB
- interfaces [C++], list of
- OLE DB provider templates [C++], object interfaces
- OLE DB [C++], interfaces
ms.assetid: 929e100c-c08c-4b64-8437-d8d1357226f6
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9d71fa9303f1b837e9d7b7110f83718a1360b91e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="data-source-object-interfaces"></a>数据源对象接口
下表显示由 OLE DB 数据源对象定义的必需和可选接口。  
  
|接口|是否必需？|实现的 OLE DB 模板？|  
|---------------|---------------|--------------------------------------|  
|`IDBCreateSession`|强制|是|  
|`IDBInitialize`|强制|是|  
|`IDBProperties`|强制|是|  
|[IPersist](http://msdn.microsoft.com/library/windows/desktop/ms688695)|强制|是|  
|[IConnectionPointContainer](http://msdn.microsoft.com/library/windows/desktop/ms683857)|Optional|No|  
|`IDBDataSourceAdmin`|Optional|No|  
|`IDBInfo`|Optional|No|  
|[为 IPersistFile](http://msdn.microsoft.com/library/windows/desktop/ms687223)|Optional|No|  
|`ISupportErrorInfo`|Optional|No|  
  
 数据源对象实现`IDBProperties`， `IDBInitialize`，和`IDBCreateSession`通过继承的接口。 你可以选择通过从继承或不继承这些实现类之一来支持其他功能。 如果你想要支持`IDBDataSourceAdmin`必须从继承的接口，`IDBDataSourceAdminImpl`类。  
  
## <a name="see-also"></a>另请参阅  
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)