---
title: "用户记录 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "COLUMN_ENTRY_MAP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "访问器 [C++], 行集合"
  - "访问器 [C++], static"
  - "BEGIN_ACCESSOR 宏, 示例"
  - "BEGIN_ACCESSOR_MAP 宏"
  - "CAccessor 类, 示例"
  - "COLUMN_ENTRY 宏"
  - "COLUMN_ENTRY_MAP 宏"
  - "OLE DB 使用者模板, 用户记录"
  - "行集合 [C++], 访问器"
  - "用户记录, OLE DB 使用者模板"
ms.assetid: 2de9e5eb-53ce-42b1-80fa-57d46600a80c
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 用户记录
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

若要使用静态访问器，即从 **CAccessor** 派生的访问器，则使用者必须具有用户记录。  用户记录是包含用于处理输入或输出的数据元素的 C\+\+ 类。  “ATL OLE DB 使用者向导”为使用者生成用户记录。  您可以向用户记录中添加方法以处理一些可选任务，如处理命令等。  
  
 下列代码显示一个处理命令的记录示例。  在此用户记录中，`BEGIN_COLUMN_MAP` 表示从提供程序传递到使用者的数据行集。  `BEGIN_PARAM_MAP` 表示一组命令参数。  该示例使用 [CCommand](../../data/oledb/ccommand-class.md) 类处理命令参数。  映射项中的数据成员表示在每个类实例所占用的连续内存块中的偏移量。  `COLUMN_ENTRY` 宏与提供程序一端的 `PROVIDER_COLUMN_ENTRY` 宏相对应。  
  
 有关 **COLUMN\_MAP** 和 **PARAM\_MAP** 宏的更多信息，请参见 [OLE DB 使用者模板宏](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)。  
  
```  
class CArtists  
{  
public:  
// Data Elements  
   CHAR m_szFirstName[20];  
   CHAR m_szLastName[30];  
   short m_nAge;  
  
// Column binding map  
BEGIN_COLUMN_MAP(CArtists)  
   COLUMN_ENTRY(1, m_szFirstName)  
   COLUMN_ENTRY(2, m_szLastName)  
   COLUMN_ENTRY(3, m_nAge)  
END_COLUMN_MAP()  
  
// Parameter binding map  
BEGIN_PARAM_MAP(CArtists)  
   COLUMN_ENTRY(1, m_nAge)  
END_PARAM_MAP()  
};  
```  
  
## 向导生成的用户记录  
 如果使用“ATL OLE DB 使用者向导”生成使用者，则可以选择使用 OLE DB 模板或 OLE DB 特性。  每种情况下生成的代码都不同。  有关这些代码的更多信息，请参见[使用者向导生成的类](../../data/oledb/consumer-wizard-generated-classes.md)。  
  
## 多个访问器的用户记录支持  
 有关需要使用多个访问器的方案的详细讨论，请参见[在一个行集合上使用多个访问器](../../data/oledb/using-multiple-accessors-on-a-rowset.md)。  
  
 下面的示例显示经过修改以支持行集合上的多个访问器的用户记录。  对于每个访问器，它使用 [BEGIN\_ACCESSOR\_MAP](../../data/oledb/begin-accessor-map.md) 和 [BEGIN\_ACCESSOR](../../data/oledb/begin-accessor.md)，而不是使用 `BEGIN_COLUMN_MAP` 和 `END_COLUMN_MAP`。  `BEGIN_ACCESSOR` 宏指定访问器编号（距离零的偏移量）以及该访问器是否为自动访问器。  自动访问器在调用 [MoveNext](../../data/oledb/crowset-movenext.md) 时将调用 `GetData` 以自动检索数据。  非自动访问器要求您显式检索数据。  如果要绑定到一个大型数据字段（如位图图像）并且可能不想为每条记录检索它，则使用非自动访问器。  
  
```  
class CMultiArtists  
{  
public:  
// Data Elements  
   CHAR m_szFirstName[20];  
   CHAR m_szLastName[30];  
   short m_nAge;  
  
// Column binding map  
BEGIN_ACCESSOR_MAP(CMultiArtists, 2)  
   BEGIN_ACCESSOR(0, true)    // true specifies an auto accessor  
    COLUMN_ENTRY(1, m_szFirstName)  
    COLUMN_ENTRY(2, m_szLastName)  
   END_ACCESSOR()  
   BEGIN_ACCESSOR(1, false)   // false specifies a manual accessor  
    COLUMN_ENTRY(3, m_nAge)  
   END_ACCESSOR()  
END_ACCESSOR_MAP()  
};  
```  
  
## 请参阅  
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)