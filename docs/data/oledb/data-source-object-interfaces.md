---
title: 数据源对象接口
ms.date: 10/24/2018
helpviewer_keywords:
- data source objects [C++], interfaces
- data source objects [C++]
- interfaces [C++], OLE DB
- interfaces [C++], list of
- OLE DB provider templates [C++], object interfaces
- OLE DB [C++], interfaces
ms.assetid: 929e100c-c08c-4b64-8437-d8d1357226f6
ms.openlocfilehash: aaa9e90996750b0518999803487fcb39729c76f9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50519635"
---
# <a name="data-source-object-interfaces"></a>数据源对象接口

下表显示了由 OLE DB 定义的数据源对象的必需和可选接口。

|接口|是否必需？|实现的 OLE DB 模板？|
|---------------|---------------|--------------------------------------|
|`IDBCreateSession`|强制|是|
|`IDBInitialize`|强制|是|
|`IDBProperties`|强制|是|
|[IPersist](/windows/desktop/api/objidl/nn-objidl-ipersist)|强制|是|
|[IConnectionPointContainer](/windows/desktop/api/ocidl/nn-ocidl-iconnectionpointcontainer)|Optional|否|
|`IDBDataSourceAdmin`|Optional|否|
|`IDBInfo`|Optional|否|
|[IPersistFile](/windows/desktop/api/objidl/nn-objidl-ipersistfile)|Optional|否|
|`ISupportErrorInfo`|Optional|否|

数据源对象实现`IDBProperties`， `IDBInitialize`，和`IDBCreateSession`通过继承的接口。 您可以选择通过继承或不从这些实现类之一继承来支持其他功能。 如果你想要支持`IDBDataSourceAdmin`接口，则必须从`IDBDataSourceAdminImpl`类。

## <a name="see-also"></a>请参阅

[OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
