---
title: 使用书签
ms.date: 10/24/2018
helpviewer_keywords:
- rowsets, bookmarks
- OLE DB provider templates, bookmarks
- bookmarks, OLE DB
- OLE DB providers, bookmark support
ms.assetid: 7fa1d1a8-5063-4aa9-93ee-815bb9c98fae
ms.openlocfilehash: 5a4a2d65ba7367b5568603b5f08a07c6d85cc4a5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209308"
---
# <a name="using-bookmarks"></a>使用书签

在打开行集之前，必须告知提供程序要使用书签。 为此，请将属性集中的 `DBPROP_BOOKMARKS` 属性设置为**true** 。 提供程序将书签检索为列零，因此，如果使用的是静态访问器，则必须使用特殊的宏 BOOKMARK_ENTRY 和 `CBookmark` 类。 `CBookmark` 是一个模板类，其中的参数是书签缓冲区的长度（以字节为单位）。 书签所需的缓冲区长度取决于提供程序。 如果使用的是 ODBC OLE DB 提供程序，如下面的示例中所示，缓冲区必须为4字节。

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

如果使用 `CDynamicAccessor`，则将在运行时动态设置缓冲区。 在这种情况下，你可以使用未指定缓冲区长度的 `CBookmark` 专用版本。 使用函数 `GetBookmark` 从当前记录中检索书签，如以下代码示例所示：

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

有关在提供程序中支持书签的信息，请参阅[提供程序支持书签](../../data/oledb/provider-support-for-bookmarks.md)。

## <a name="see-also"></a>另请参阅

[使用访问器](../../data/oledb/using-accessors.md)
