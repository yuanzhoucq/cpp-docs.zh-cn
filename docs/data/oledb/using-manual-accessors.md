---
title: 使用手动访问器 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- command handling, OLE DB Templates
- manual accessors
- accessors [C++], manual
ms.assetid: 29f00a89-0240-482b-8413-4120b9644672
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5aa7f72cc76f80e2304faf93ca0c6198c505e88a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46101632"
---
# <a name="using-manual-accessors"></a>使用手动访问器

有四件事情时处理未知的命令：  
  
- 确定参数  
  
- 执行命令  
  
- 确定输出列  
  
- 查看是否有多个返回行集  
  
若要使用 OLE DB 使用者模板执行此操作，请使用`CManualAccessor`类，请执行以下步骤：  
  
1. 打开`CCommand`对象与`CManualAccessor`作为模板参数。  
  
    ```cpp  
    CCommand<CManualAccessor, CRowset, CMultipleResults> rs;  
    ```  
  
1. 查询的会话`IDBSchemaRowset`接口，并使用过程参数行集。 如果`IDBSchemaRowset`接口不可用，查询`ICommandWithParameters`接口。 调用`GetParameterInfo`有关信息。 如果两个接口都可用，可以假定没有任何参数。  
  
1. 对于每个参数，调用`AddParameterEntry`以添加参数并将其设置。  
  
1. 打开行集，但将绑定参数设置为**false**。  
  
1. 调用`GetColumnInfo`检索输出列。 使用`AddBindEntry`向绑定添加输出列。  
  
1. 调用`GetNextResult`以确定多个行集是否可用。 重复步骤 2 到 5。  
  
手动访问器的示例，请参阅`CDBListView::CallProcedure`中[DBVIEWER](https://github.com/Microsoft/VCSamples)示例。  
  
## <a name="see-also"></a>请参阅  

[使用访问器](../../data/oledb/using-accessors.md)