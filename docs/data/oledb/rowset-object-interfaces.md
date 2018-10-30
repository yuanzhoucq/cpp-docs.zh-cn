---
title: 行集对象接口 |Microsoft Docs
ms.custom: ''
ms.date: 10/24/2018
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
ms.openlocfilehash: dc9ec134321b2acf9994ad7dfb43c5b14bf0e75f
ms.sourcegitcommit: 840033ddcfab51543072604ccd5656fc6d4a5d3a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/29/2018
ms.locfileid: "50216443"
---
# <a name="rowset-object-interfaces"></a>行集合对象接口

下表显示了由 OLE DB 行集对象定义的必需和可选接口。

|接口|是否必需？|实现的 OLE DB 模板？|
|---------------|---------------|--------------------------------------|
|[IAccessor](/previous-versions/windows/desktop/ms719672)|必需|是|
|[IColumnsInfo](/previous-versions/windows/desktop/ms724541)|必需|是|
|[IConvertType](/previous-versions/windows/desktop/ms715926)|必需|是|
|[IRowset](/previous-versions/windows/desktop/ms720986)|必需|是|
|[IRowsetInfo](/previous-versions/windows/desktop/ms724541)|必需|是|
|[IChapteredRowset](/previous-versions/windows/desktop/ms718180)|可选|否|
|[IColumnsInfo2](/previous-versions/windows/desktop/ms712953)|可选|否|
|[IColumnsRowset](/previous-versions/windows/desktop/ms722657)|可选|否|
|[IConnectionPointContainer](/windows/desktop/api/ocidl/nn-ocidl-iconnectionpointcontainer)|可选|是 （通过 ATL)|
|[IDBAsynchStatus](/previous-versions/windows/desktop/ms709832)|可选|否|
|[IGetRow](/previous-versions/windows/desktop/ms718047)|可选|否|
|[IRowsetChange](/previous-versions/windows/desktop/ms715790)|可选|是|
|[IRowsetChapterMember](/previous-versions/windows/desktop/ms725430)|可选|否|
|[IRowsetCurrentIndex](/previous-versions/windows/desktop/ms709700)|可选|否|
|[IRowsetFind](/previous-versions/windows/desktop/ms724221)|可选|否|
|[IRowsetIdentity](/previous-versions/windows/desktop/ms715913)|可选 （但对于级别 0 提供程序为必需）|是|
|[IRowsetIndex](/previous-versions/windows/desktop/ms719604)|可选|否|
|[IRowsetLocate](/previous-versions/windows/desktop/ms721190)|可选|是|
|[IRowsetRefresh](/previous-versions/windows/desktop/ms714892)|可选|否|
|[IRowsetScroll](/previous-versions/windows/desktop/ms712984)|可选|否|
|[IRowsetUpdate](/previous-versions/windows/desktop/ms714401)|可选|是|
|[IRowsetView](/previous-versions/windows/desktop/ms709755)|可选|否|
|[ISupportErrorInfo](/previous-versions/windows/desktop/ms715816)|可选|是|
|[IRowsetBookmark](/previous-versions/windows/desktop/ms714246)|可选|否|

该向导生成行集对象实现`IAccessor`， `IRowset`，和`IRowsetInfo`通过继承。 `IAccessorImpl`将这两个输出的列。 `IRowset`接口处理提取行和数据。 `IRowsetInfo`接口处理行集属性。

## <a name="see-also"></a>请参阅

[OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
