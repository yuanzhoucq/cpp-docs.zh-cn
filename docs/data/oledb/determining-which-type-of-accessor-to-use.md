---
title: 确定要使用的访问器类型
ms.date: 05/09/2019
helpviewer_keywords:
- rowsets [C++], data types
- accessors [C++], types
ms.assetid: 22483dd2-f4e0-4dcb-8e4d-cd43a9c1a3db
ms.openlocfilehash: d729e2cf5b08ae227d0cc2e4d5ab7f8ac865cdc4
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079658"
---
# <a name="determining-which-type-of-accessor-to-use"></a>确定要使用的访问器类型

可以在编译时或运行时确定行集的数据类型。

如果需要在编译时确定数据类型，请使用静态取值函数（如 `CAccessor`）。

如果需要在运行时确定数据类型，请使用动态取值函数（`CDynamicAccessor` 或其子级）或手动取值函数 (`CManualAccessor`)。 在这种情况下，可以对行集调用 `GetColumnInfo`，以返回从中能确定类型的列绑定信息。

下表列出了使用者模板中提供的取值函数类型。 每种取值函数都有各自的优点和缺点。 应有一种取值函数类型能够满足你的需求，具体视情况而定。

|访问器类|绑定|参数|注释|
|--------------------|-------------|---------------|-------------|
|`CAccessor`|使用 COLUMN_ENTRY 宏创建用户记录。 宏将此记录中的数据成员绑定到取值函数。 在行集创建后，就无法解除绑定列。|是，通过使用 PARAM_MAP 宏条目。 一旦绑定，就无法解除绑定参数。|最快的取值函数，因为只有少量代码。|
|`CDynamicAccessor`|自动。|不是。|如果不知道行集的数据类型，便会发现此取值函数很有用。|
|`CDynamicParameterAccessor`|自动，但可以[重写](../../data/oledb/overriding-a-dynamic-accessor.md)。|是，前提是提供程序支持 `ICommandWithParameters`。 参数自动绑定。|比 `CDynamicAccessor` 慢，但对调用泛型存储过程很有用。|
|`CDynamicStringAccessor[A,W]`|自动。|不是。|将从数据存储中取值的数据作为字符串数据进行检索。|
|`CManualAccessor`|手动使用 `AddBindEntry`。|手动使用 `AddParameterEntry`。|快速；参数和列仅绑定一次。 你确定要使用的数据类型。 （有关示例，请参阅[DBVIEWER](https://github.com/Microsoft/VCSamples)示例。）需要的代码多于 `CDynamicAccessor` 或 `CAccessor`。 这更像是直接调用 OLE DB。|
|`CXMLAccessor`|自动。|不是。|将从数据存储中取值的数据作为字符串数据进行检索，并将它格式化为 XML 标记的数据。|

## <a name="see-also"></a>另请参阅

[使用访问器](../../data/oledb/using-accessors.md)