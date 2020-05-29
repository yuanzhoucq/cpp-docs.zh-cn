---
title: Rowset 对象接口
ms.date: 10/24/2018
helpviewer_keywords:
- interfaces, OLE DB
- OLE DB, interfaces
- rowset objects [OLE DB]
- OLE DB provider templates, object interfaces
- interfaces, list of
ms.assetid: 0d7a5d48-2fe4-434f-a84b-157c1fdc3494
ms.openlocfilehash: d9c2c61714a98d9de09d8657352a14f296e35a58
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "79544542"
---
# <a name="rowset-object-interfaces"></a>Rowset 对象接口

下表显示了 OLE DB 为行集对象定义的必需和可选接口。

|接口|必需？|由 OLE DB 模板实现？|
|---------------|---------------|--------------------------------------|
|[IAccessor](/previous-versions/windows/desktop/ms719672(v=vs.85))|必需|是|
|[IColumnsInfo](/previous-versions/windows/desktop/ms724541(v=vs.85))|必需|是|
|[IConvertType](/previous-versions/windows/desktop/ms715926(v=vs.85))|必需|是|
|[IRowset](/previous-versions/windows/desktop/ms720986(v=vs.85))|必需|是|
|[IRowsetInfo](/previous-versions/windows/desktop/ms724541(v=vs.85))|必需|是|
|[IChapteredRowset](/previous-versions/windows/desktop/ms718180(v=vs.85))|可选|否|
|[IColumnsInfo2](/previous-versions/windows/desktop/ms712953(v=vs.85))|可选|否|
|[IColumnsRowset](/previous-versions/windows/desktop/ms722657(v=vs.85))|可选|否|
|[IConnectionPointContainer](/windows/win32/api/ocidl/nn-ocidl-iconnectionpointcontainer)|可选|是（通过 ATL）|
|[IDBAsynchStatus](/previous-versions/windows/desktop/ms709832(v=vs.85))|可选|否|
|[IGetRow](/previous-versions/windows/desktop/ms718047(v=vs.85))|可选|否|
|[IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85))|可选|是|
|[IRowsetChapterMember](/previous-versions/windows/desktop/ms725430(v=vs.85))|可选|否|
|[IRowsetCurrentIndex](/previous-versions/windows/desktop/ms709700(v=vs.85))|可选|否|
|[IRowsetFind](/previous-versions/windows/desktop/ms724221(v=vs.85))|可选|否|
|[IRowsetIdentity](/previous-versions/windows/desktop/ms715913(v=vs.85))|可选（但对于级别0提供程序是必需的）|是|
|[IRowsetIndex](/previous-versions/windows/desktop/ms719604(v=vs.85))|可选|否|
|[IRowsetLocate](/previous-versions/windows/desktop/ms721190(v=vs.85))|可选|是|
|[IRowsetRefresh](/previous-versions/windows/desktop/ms714892(v=vs.85))|可选|否|
|[IRowsetScroll](/previous-versions/windows/desktop/ms712984(v=vs.85))|可选|否|
|[IRowsetUpdate](/previous-versions/windows/desktop/ms714401(v=vs.85))|可选|是|
|[IRowsetView](/previous-versions/windows/desktop/ms709755(v=vs.85))|可选|否|
|[ISupportErrorInfo](/previous-versions/windows/desktop/ms715816(v=vs.85))|可选|是|
|[IRowsetBookmark](/previous-versions/windows/desktop/ms714246(v=vs.85))|可选|否|

向导生成的行集对象通过继承实现 `IAccessor`、`IRowset`和 `IRowsetInfo`。 `IAccessorImpl` 绑定两个输出列。 `IRowset` 接口处理提取行和数据。 `IRowsetInfo` 接口处理行集属性。

## <a name="see-also"></a>另请参阅

[OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
