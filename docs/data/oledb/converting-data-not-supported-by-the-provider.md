---
title: 将数据提供程序不支持转换 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB provider templates, unsupported data types
ms.assetid: f495e50f-530a-4fab-ab54-e0c359785845
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: fa9fed1f7c779efc7104ec8138d618b85aeb2a33
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46081736"
---
# <a name="converting-data-not-supported-by-the-provider"></a>转换不受提供程序支持的数据

当使用者请求提供程序不支持的数据类型时，OLE DB 提供程序模板的代码`IRowsetImpl::GetData`调用 Msdadc.dll 要转换的数据类型。  
  
如果实现类似的接口`IRowsetChange`要求进行数据转换，可以调用 Msdaenum.dll 进行转换。 使用`GetData`Atldb.h，作为示例中定义。  
  
## <a name="see-also"></a>请参阅  

[使用 OLE DB 提供程序模板](../../data/oledb/working-with-ole-db-provider-templates.md)