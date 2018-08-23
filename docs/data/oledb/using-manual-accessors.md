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
ms.openlocfilehash: 236fd1809fa012262f3a98f0f1856f3bbff6b454
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/30/2018
ms.locfileid: "39340859"
---
# <a name="using-manual-accessors"></a>使用手动访问器
有四件事情时处理未知的命令：  
  
-   确定参数  
  
-   执行命令  
  
-   确定输出列  
  
-   查看是否有多个返回行集  
  
 若要使用 OLE DB 使用者模板执行此操作，请使用`CManualAccessor`类，请执行以下步骤：  
  
1.  打开`CCommand`对象与`CManualAccessor`作为模板参数。  
  
    ```cpp  
    CCommand<CManualAccessor, CRowset, CMultipleResults> rs;  
    ```  
  
2.  查询的会话`IDBSchemaRowset`接口，并使用过程参数行集。 如果`IDBSchemaRowset`接口不可用，查询`ICommandWithParameters`接口。 调用`GetParameterInfo`有关信息。 如果两个接口都可用，可以假定没有任何参数。  
  
3.  对于每个参数，调用`AddParameterEntry`以添加参数并将其设置。  
  
4.  打开行集，但将绑定参数设置为**false**。  
  
5.  调用`GetColumnInfo`检索输出列。 使用`AddBindEntry`向绑定添加输出列。  
  
6.  调用`GetNextResult`以确定多个行集是否可用。 重复步骤 2 到 5。  
  
 手动访问器的示例，请参阅`CDBListView::CallProcedure`中[DBVIEWER](http://msdn.microsoft.com/07620f99-c347-4d09-9ebc-2459e8049832)示例。  
  
## <a name="see-also"></a>请参阅  
 [使用访问器](../../data/oledb/using-accessors.md)