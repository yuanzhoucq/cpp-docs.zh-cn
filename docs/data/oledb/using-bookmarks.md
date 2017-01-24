---
title: "使用书签 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "书签, OLE DB"
  - "OLE DB 提供程序模板, 书签"
  - "OLE DB 提供程序, 书签支持"
  - "行集合, 书签"
ms.assetid: 7fa1d1a8-5063-4aa9-93ee-815bb9c98fae
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用书签
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在打开行集合之前，必须告知提供程序您希望使用书签。  为此，请在属性集中将 **DBPROP\_BOOKMARKS** 属性设置为 **true**。  提供程序将书签检索为列零，因此如果使用的是静态访问器，则必须使用特殊宏 `BOOKMARK_ENTRY` 和 `CBookmark` 类。  `CBookmark` 是模板类，其参数是书签缓冲区的长度（以字节为单位）。  书签所需的缓冲区长度取决于提供程序。  如果使用的是 ODBC OLE DB 提供程序（如下例所示），则此缓冲区必须为 4 个字节。  
  
```  
class CProducts  
{  
public:  
   CBookmark<4>   bookmark;  
  
   BEGIN_COLUMN_MAP(CProducts)  
      BOOKMARK_ENTRY(bookmark)  
   END_COLUMN_MAP()  
};  
  
CDBPropSet propset(DBPROPSET_ROWSET);  
propset.AddProperty(DBPROP_BOOKMARKS, true);  
  
CTable<CAccessor<CProducts> > product;  
product.Open(session, "Products", &propset);  
```  
  
 如果使用 `CDynamicAccessor`，则此缓冲区将在运行时动态分配。  在这种情况下，可以使用 `CBookmark` 的专用版本，从而不必指定缓冲区的长度。  使用 `GetBookmark` 函数从当前记录中检索书签，如下面的代码示例所示：  
  
```  
CTable<CDynamicAccessor> product;  
CBookmark<>              bookmark;  
CDBPropSet propset(DBPROPSET_ROWSET);  
  
propset.AddProperty(DBPROP_BOOKMARKS, true);  
product.Open(session, "Products", &propset);  
product.MoveNext();  
product.GetBookmark(&bookmark);  
```  
  
 有关在提供程序中支持书签的信息，请参见[提供程序的书签支持](../../data/oledb/provider-support-for-bookmarks.md)。  
  
## 请参阅  
 [使用访问器](../../data/oledb/using-accessors.md)