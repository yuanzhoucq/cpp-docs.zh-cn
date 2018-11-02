---
title: 使用书签
ms.date: 10/24/2018
helpviewer_keywords:
- rowsets, bookmarks
- OLE DB provider templates, bookmarks
- bookmarks, OLE DB
- OLE DB providers, bookmark support
ms.assetid: 7fa1d1a8-5063-4aa9-93ee-815bb9c98fae
ms.openlocfilehash: 1f8ef4c25ad921dad66e5587f4005585b3e017f5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50635651"
---
# <a name="using-bookmarks"></a>使用书签

在打开行集之前，必须告知提供程序想要使用的书签。 若要执行此操作，设置`DBPROP_BOOKMARKS`属性设置为**true**在您的属性集。 提供程序检索书签作为列零，因此你必须使用特殊的宏 BOOKMARK_ENTRY 和`CBookmark`类如果您使用的静态访问器。 `CBookmark` 是一种模板类，其中的参数是以字节为单位的书签缓冲区的长度。 所需的书签缓冲区的长度取决于提供程序。 如果您使用 ODBC OLE DB 提供程序，如下面的示例中所示，缓冲区必须是 4 个字节。

```cpp
class CProducts
{
public:
   CBookmark<4> bookmark;

   BEGIN_COLUMN_MAP(CProducts)
      BOOKMARK_ENTRY(bookmark)
   END_COLUMN_MAP()
};
```

然后，使用以下代码：

```cpp
CDBPropSet propset(DBPROPSET_ROWSET);
propset.AddProperty(DBPROP_BOOKMARKS, true);

CTable<CAccessor<CProducts>> product;
CSession session;
product.Open(session, "Products", &propset);
```

如果使用`CDynamicAccessor`，在运行时动态设置缓冲区。 在这种情况下，可以使用的专用的版本`CBookmark`不为其指定缓冲区长度。 使用函数`GetBookmark`书签检索当前记录，如以下代码示例中所示：

```cpp
CTable<CDynamicAccessor> product;
CBookmark<> bookmark;
CDBPropSet propset(DBPROPSET_ROWSET);
CSession session;

propset.AddProperty(DBPROP_BOOKMARKS, true);
product.Open(session, "Products", &propset);
product.MoveNext();
product.GetBookmark(&bookmark);
```

在提供程序中支持书签的信息，请参阅[用于书签的提供程序支持](../../data/oledb/provider-support-for-bookmarks.md)。

## <a name="see-also"></a>请参阅

[使用访问器](../../data/oledb/using-accessors.md)