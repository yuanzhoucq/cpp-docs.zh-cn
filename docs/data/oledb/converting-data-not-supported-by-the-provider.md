---
title: 转换不受提供程序支持的数据
ms.date: 10/29/2018
helpviewer_keywords:
- OLE DB provider templates, unsupported data types
ms.assetid: f495e50f-530a-4fab-ab54-e0c359785845
ms.openlocfilehash: e60f6cd4f7dca1ed3e176cabefc42f69946436a4
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59033834"
---
# <a name="converting-data-not-supported-by-the-provider"></a>转换不受提供程序支持的数据

当使用者请求提供程序不支持的数据类型时，OLE DB 提供程序模板的代码`IRowsetImpl::GetData`调用 Msdadc.dll 要转换的数据类型。

如果实现类似的接口`IRowsetChange`要求进行数据转换，可以调用 Msdaenum.dll 进行转换。 使用`GetData`Atldb.h，作为示例中定义。

## <a name="see-also"></a>请参阅

[使用 OLE DB 提供程序模板](../../data/oledb/working-with-ole-db-provider-templates.md)