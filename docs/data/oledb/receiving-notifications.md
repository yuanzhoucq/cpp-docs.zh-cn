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
ms.openlocfilehash: 4b630a9728770a5e35e6d6300cf465b90238350c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209760"
---
# <a name="receiving-notifications"></a>接收通知

OLE DB 提供在发生事件时接收通知的接口。 这些在**OLE DB 程序员参考**中的[OLE DB 对象通知](/previous-versions/windows/desktop/ms725406(v=vs.85))中进行了介绍。 这些事件的设置使用标准 COM 连接点机制。 例如，想要通过 `IRowsetNotify` 检索事件的 ATL 对象通过将 `IRowsetNotify` 添加到类派生列表并通过 COM_INTERFACE_ENTRY 宏进行公开来实现 `IRowsetNotify` 接口。

`IRowsetNotify` 具有三种方法，可在不同时间调用这些方法。 如果你只想对其中一种方法做出响应，则可以使用[IRowsetNotifyImpl](../../data/oledb/irowsetnotifyimpl-class.md)类，它为你不感兴趣的方法返回 E_NOTIMPL。

创建行集时，必须告知提供程序您希望返回的行集对象支持 `IConnectionPointContainer`，这是设置通知所必需的。

下面的代码演示如何从 ATL 对象打开行集，并使用 `AtlAdvise` 函数设置通知接收器。 `AtlAdvise` 返回调用 `AtlUnadvise`时使用的 cookie。

```cpp
CDBPropSet propset(DBPROPSET_ROWSET);
propset.AddProperty(DBPROP_IConnectionPointContainer, true);
```

然后，使用以下代码：

```cpp
product.Open(session, _T("Products"), &propset);

AtlAdvise(product.m_spRowset, GetUnknown(), IID_IRowsetNotify, &m_dwCookie);
```

## <a name="see-also"></a>另请参阅

[使用访问器](../../data/oledb/using-accessors.md)
