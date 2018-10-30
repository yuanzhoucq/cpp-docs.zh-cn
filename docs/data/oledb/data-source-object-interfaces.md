---
title: 数据源对象接口 |Microsoft Docs
ms.custom: ''
ms.date: 10/24/2018
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- data source objects [C++], interfaces
- data source objects [C++]
- interfaces [C++], OLE DB
- interfaces [C++], list of
- OLE DB provider templates [C++], object interfaces
- OLE DB [C++], interfaces
ms.assetid: 929e100c-c08c-4b64-8437-d8d1357226f6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: d6b76dd8423abd18359081a8fc30050c23e0b161
ms.sourcegitcommit: 840033ddcfab51543072604ccd5656fc6d4a5d3a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/29/2018
ms.locfileid: "50216274"
---
# <a name="data-source-object-interfaces"></a>数据源对象接口

下表显示了由 OLE DB 定义的数据源对象的必需和可选接口。

|接口|是否必需？|实现的 OLE DB 模板？|
|---------------|---------------|--------------------------------------|
|`IDBCreateSession`|必需|是|
|`IDBInitialize`|必需|是|
|`IDBProperties`|必需|是|
|[IPersist](/windows/desktop/api/objidl/nn-objidl-ipersist)|必需|是|
|[IConnectionPointContainer](/windows/desktop/api/ocidl/nn-ocidl-iconnectionpointcontainer)|可选|否|
|`IDBDataSourceAdmin`|可选|否|
|`IDBInfo`|可选|否|
|[IPersistFile](/windows/desktop/api/objidl/nn-objidl-ipersistfile)|可选|否|
|`ISupportErrorInfo`|可选|否|

数据源对象实现`IDBProperties`， `IDBInitialize`，和`IDBCreateSession`通过继承的接口。 您可以选择通过继承或不从这些实现类之一继承来支持其他功能。 如果你想要支持`IDBDataSourceAdmin`接口，则必须从`IDBDataSourceAdminImpl`类。

## <a name="see-also"></a>请参阅

[OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
