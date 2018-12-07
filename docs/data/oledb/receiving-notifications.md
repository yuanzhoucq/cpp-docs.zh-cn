---
title: 接收通知
ms.date: 10/24/2018
helpviewer_keywords:
- notifications [C++], OLE DB consumers
- receiving notifications in OLE DB
- events [C++], notifications in OLE DB
- notifications [C++], events
- OLE DB consumers, notifications
- rowsets, event notifications
- OLE DB providers, notifications
ms.assetid: 305a1103-0c87-40c8-94bc-7fbbdd52ae32
ms.openlocfilehash: 491da4d1735a32eba4e6e5bd8bee6604da4aeb73
ms.sourcegitcommit: c40469825b6101baac87d43e5f4aed6df6b078f5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/12/2018
ms.locfileid: "51556330"
---
# <a name="receiving-notifications"></a>接收通知

OLE DB 提供用于在事件发生时接收通知的接口。 中介绍了这些[OLE DB 对象通知](https://docs.microsoft.com/previous-versions/windows/desktop/ms725406(v=vs.85))中**OLE DB 程序员参考**。 这些事件的安装程序将使用标准的 COM 连接点机制。 例如，想要检索事件通过的 ATL 对象`IRowsetNotify`实现`IRowsetNotify`接口通过添加`IRowsetNotify`到派生类的列表并将其公开通过 COM_INTERFACE_ENTRY 宏。

`IRowsetNotify` 有三个方法，可以在不同时间调用。 如果你想要响应的下列方法之一，则可以使用[IRowsetNotifyImpl](../../data/oledb/irowsetnotifyimpl-class.md)类，该类不感兴趣的方法返回 E_NOTIMPL。

在创建行集时，你必须告知提供程序希望返回的行集对象以支持`IConnectionPointContainer`，需要设置通知。

下面的代码演示如何从 ATL 对象打开行集，并使用`AtlAdvise`函数来通知接收器设置。 `AtlAdvise` 返回在调用时使用的 cookie `AtlUnadvise`。

```cpp
CDBPropSet propset(DBPROPSET_ROWSET);
propset.AddProperty(DBPROP_IConnectionPointContainer, true);
```

然后，使用以下代码：

```cpp
product.Open(session, _T("Products"), &propset);

AtlAdvise(product.m_spRowset, GetUnknown(), IID_IRowsetNotify, &m_dwCookie);
```

## <a name="see-also"></a>请参阅

[使用访问器](../../data/oledb/using-accessors.md)