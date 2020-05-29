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
ms.openlocfilehash: a615694a9db75cdaf3b187cf6d29248bd26ef978
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "79544602"
---
# <a name="data-source-object-interfaces"></a>数据源对象接口

下表显示了 OLE DB 为数据源对象定义的必需和可选接口。

|接口|必需？|由 OLE DB 模板实现？|
|---------------|---------------|--------------------------------------|
|`IDBCreateSession`|必需|是|
|`IDBInitialize`|必需|是|
|`IDBProperties`|必需|是|
|[IPersist](/windows/win32/api/objidl/nn-objidl-ipersist)|必需|是|
|[IConnectionPointContainer](/windows/win32/api/ocidl/nn-ocidl-iconnectionpointcontainer)|可选|否|
|`IDBDataSourceAdmin`|可选|否|
|`IDBInfo`|可选|否|
|[IPersistFile](/windows/win32/api/objidl/nn-objidl-ipersistfile)|可选|否|
|`ISupportErrorInfo`|可选|否|

数据源对象通过继承实现 `IDBProperties`、`IDBInitialize`和 `IDBCreateSession` 接口。 可以通过继承或不从这些实现类之一继承来选择支持其他功能。 如果要支持 `IDBDataSourceAdmin` 接口，则必须从 `IDBDataSourceAdminImpl` 类继承。

## <a name="see-also"></a>另请参阅

[OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
