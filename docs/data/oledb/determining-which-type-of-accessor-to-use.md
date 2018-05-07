---
title: 确定要使用的访问器类型 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- rowsets [C++], data types
- accessors [C++], types
ms.assetid: 22483dd2-f4e0-4dcb-8e4d-cd43a9c1a3db
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 89a55127b8f7e5e0e7d338a9e7ba4f85e8c568d2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="determining-which-type-of-accessor-to-use"></a>确定要使用的访问器类型
在编译时或在运行时，你可以确定行集上的数据类型。  
  
 如果你需要在编译时确定数据类型，使用静态的访问器 (如`CAccessor`)。 手动或通过使用 ATL OLE DB 使用者向导，你可以确定数据类型。  
  
 如果你需要在运行时确定的数据类型，使用动态 (`CDynamicAccessor`或其子级) 或手动访问器 (`CManualAccessor`)。 在这些情况下，你可以调用`GetColumnInfo`行集返回的列绑定信息，从中你可以确定类型上。  
  
 下表列出的使用者模板中提供的访问器的类型。 每个访问器都有优点和缺点。 具体取决于你的情况，一个访问器类型应适合你的需求。  
  
|访问器类|绑定|参数|注释|  
|--------------------|-------------|---------------|-------------|  
|`CAccessor`|创建的用户记录`COLUMN_ENTRY`宏。 宏将该记录中的数据成员绑定到访问器中。 当创建行集时，列不能为未绑定。|是，通过使用**PARAM_MAP**宏条目。 绑定后，参数不能为未绑定。|由于少量的代码的最快访问器。|  
|`CDynamicAccessor`|自动。|不是。|如果你不知道在行集中的数据的类型很有用。|  
|`CDynamicParameterAccessor`|自动进行的但可以是[中被重写](../../data/oledb/overriding-a-dynamic-accessor.md)。|是的如果该提供程序支持`ICommandWithParameters`。 自动绑定参数。|低于`CDynamicAccessor`但用于调用泛型存储的过程。|  
|**CDynamicStringAccessor[A,W]**|自动。|不是。|检索访问从数据存储区作为字符串数据的数据。|  
|`CManualAccessor`|手动使用`AddBindEntry`。|使用手动`AddParameterEntry`。|非常快;参数和列绑定仅一次。 确定要使用数据的类型。 (请参阅[DBVIEWER](http://msdn.microsoft.com/en-us/07620f99-c347-4d09-9ebc-2459e8049832)示例的示例。)需要更多代码比`CDynamicAccessor`或`CAccessor`。 而是要直接调用 OLE DB。|  
|`CXMLAccessor`|自动。|不是。|检索从数据存储区作为字符串数据访问的数据，并将其格式化为 XML 标记数据。|  
  
## <a name="see-also"></a>请参阅  
 [使用访问器](../../data/oledb/using-accessors.md)