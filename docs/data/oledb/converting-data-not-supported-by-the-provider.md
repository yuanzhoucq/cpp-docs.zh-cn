---
title: 转换不受提供程序支持的数据
ms.date: 10/29/2018
helpviewer_keywords:
- OLE DB provider templates, unsupported data types
ms.assetid: f495e50f-530a-4fab-ab54-e0c359785845
ms.openlocfilehash: e87aebc4d6f23343af9a2f966d2c522e95b304ea
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211492"
---
# <a name="converting-data-not-supported-by-the-provider"></a>转换不受提供程序支持的数据

当使用者请求提供程序不支持的数据类型时，`IRowsetImpl::GetData` 的 OLE DB 提供程序模板代码将调用 Msdadc 来转换数据类型。

如果实现的接口需要数据转换，如 `IRowsetChange`，则可以调用 Msdaenum 来执行转换。 例如，使用为 atldb.h 中定义的 `GetData`。

## <a name="see-also"></a>另请参阅

[使用 OLE DB 提供程序模板](../../data/oledb/working-with-ole-db-provider-templates.md)
