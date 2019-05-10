---
title: 行集合对象接口
ms.date: 10/24/2018
helpviewer_keywords:
- interfaces, OLE DB
- OLE DB, interfaces
- rowset objects [OLE DB]
- OLE DB provider templates, object interfaces
- interfaces, list of
ms.assetid: 0d7a5d48-2fe4-434f-a84b-157c1fdc3494
ms.openlocfilehash: 1f3e6066af4b6870c5fa90f7bde373bb7be476ce
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62243973"
---
# <a name="rowset-object-interfaces"></a>行集合对象接口

下表显示了由 OLE DB 行集对象定义的必需和可选接口。

|接口|是否必需？|实现的 OLE DB 模板？|
|---------------|---------------|--------------------------------------|
|[IAccessor](/previous-versions/windows/desktop/ms719672(v=vs.85))|强制|是|
|[IColumnsInfo](/previous-versions/windows/desktop/ms724541(v=vs.85))|强制|是|
|[IConvertType](/previous-versions/windows/desktop/ms715926(v=vs.85))|强制|是|
|[IRowset](/previous-versions/windows/desktop/ms720986(v=vs.85))|强制|是|
|[IRowsetInfo](/previous-versions/windows/desktop/ms724541(v=vs.85))|强制|是|
|[IChapteredRowset](/previous-versions/windows/desktop/ms718180(v=vs.85))|Optional|否|
|[IColumnsInfo2](/previous-versions/windows/desktop/ms712953(v=vs.85))|Optional|否|
|[IColumnsRowset](/previous-versions/windows/desktop/ms722657(v=vs.85))|Optional|否|
|[IConnectionPointContainer](/windows/desktop/api/ocidl/nn-ocidl-iconnectionpointcontainer)|Optional|是 （通过 ATL)|
|[IDBAsynchStatus](/previous-versions/windows/desktop/ms709832(v=vs.85))|Optional|否|
|[IGetRow](/previous-versions/windows/desktop/ms718047(v=vs.85))|Optional|否|
|[IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85))|Optional|是|
|[IRowsetChapterMember](/previous-versions/windows/desktop/ms725430(v=vs.85))|Optional|否|
|[IRowsetCurrentIndex](/previous-versions/windows/desktop/ms709700(v=vs.85))|Optional|否|
|[IRowsetFind](/previous-versions/windows/desktop/ms724221(v=vs.85))|Optional|否|
|[IRowsetIdentity](/previous-versions/windows/desktop/ms715913(v=vs.85))|可选 （但对于级别 0 提供程序为必需）|是|
|[IRowsetIndex](/previous-versions/windows/desktop/ms719604(v=vs.85))|Optional|否|
|[IRowsetLocate](/previous-versions/windows/desktop/ms721190(v=vs.85))|Optional|是|
|[IRowsetRefresh](/previous-versions/windows/desktop/ms714892(v=vs.85))|Optional|否|
|[IRowsetScroll](/previous-versions/windows/desktop/ms712984(v=vs.85))|Optional|否|
|[IRowsetUpdate](/previous-versions/windows/desktop/ms714401(v=vs.85))|Optional|是|
|[IRowsetView](/previous-versions/windows/desktop/ms709755(v=vs.85))|Optional|否|
|[ISupportErrorInfo](/previous-versions/windows/desktop/ms715816(v=vs.85))|Optional|是|
|[IRowsetBookmark](/previous-versions/windows/desktop/ms714246(v=vs.85))|Optional|否|

该向导生成行集对象实现`IAccessor`， `IRowset`，和`IRowsetInfo`通过继承。 `IAccessorImpl`将这两个输出的列。 `IRowset`接口处理提取行和数据。 `IRowsetInfo`接口处理行集属性。

## <a name="see-also"></a>请参阅

[OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
