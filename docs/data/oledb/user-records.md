---
title: 用户记录
ms.date: 05/09/2019
f1_keywords:
- COLUMN_ENTRY_MAP
helpviewer_keywords:
- rowsets [C++], accessors
- COLUMN_ENTRY macro
- COLUMN_ENTRY_MAP macro
- user records, OLE DB consumer templates
- OLE DB consumer templates, user records
- CAccessor class, example
- BEGIN_ACCESSOR_MAP macro
- accessors [C++], rowsets
- accessors [C++], static
- BEGIN_ACCESSOR macro, example
ms.assetid: 2de9e5eb-53ce-42b1-80fa-57d46600a80c
ms.openlocfilehash: c9c1126f0e8248f31ac739bb1d939f811bda678d
ms.sourcegitcommit: 00e26915924869cd7eb3c971a7d0604388abd316
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/10/2019
ms.locfileid: "65525288"
---
# <a name="user-records"></a>用户记录

> [!NOTE]
> ATL OLE DB 使用者向导不适用于 Visual Studio 2019 及更高版本。 但仍可以手动添加此功能。 有关详细信息，请参阅[不使用向导创建使用者](creating-a-consumer-without-using-a-wizard.md)。

使用者必须有用户记录，才能使用静态取值函数（即派生自 `CAccessor` 的取值函数）。 用户记录是 C++ 类，其中包含用于处理输入或输出的数据元素。 ATL OLE DB 使用者向导为使用者生成用户记录。 可以将方法添加到用户记录中，以执行处理命令等可选任务。

下面的代码展示了处理命令的示例记录。 在用户记录中，BEGIN_COLUMN_MAP 表示从提供程序传递给使用者的数据行集。 BEGIN_PARAM_MAP 表示一组命令参数。 此示例使用 [CCommand](../../data/oledb/ccommand-class.md) 类来处理命令参数。 映射条目中的数据成员表示类的每个实例在一个连续内存块中的偏移量。 COLUMN_ENTRY 宏对应于提供程序端的 PROVIDER_COLUMN_ENTRY 宏。

若要详细了解 COLUMN_MAP 和 PARAM_MAP 宏，请参阅[用于 OLE DB 使用者模板的宏](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)。

```cpp
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

## <a name="wizard-generated-user-records"></a>向导生成的用户记录

如果使用 ATL OLE DB 使用者向导生成使用者，可以选择是使用 OLE DB 模板，还是使用 OLE DB 特性。 生成的代码因具体情况而异。 若要详细了解此代码，请参阅[使用者向导生成的类](../../data/oledb/consumer-wizard-generated-classes.md)。

## <a name="user-record-support-for-multiple-accessors"></a>用户记录支持多个取值函数

有关需要使用多个取值函数的情况的详细讨论，请参阅[对行集使用多个取值函数](../../data/oledb/using-multiple-accessors-on-a-rowset.md)。

下面的示例展示了修改为支持对行集使用多个取值函数的用户记录。 它对每个取值函数使用 [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md) 和 [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)，而不是 BEGIN_COLUMN_MAP 和 END_COLUMN_MAP。 BEGIN_ACCESSOR 宏指定取值函数编号（从零开始的偏移量），以及取值函数是否为自动取值函数。 自动取值函数调用 `GetData`，以在调用 [MoveNext](../../data/oledb/crowset-movenext.md) 时自动检索数据。 非自动取值函数要求必须显式检索数据。 若要绑定到不建议为每条记录都检索数据的大型数据字段（如位图），请使用非自动取值函数。

```cpp
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

## <a name="see-also"></a>请参阅

[OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)