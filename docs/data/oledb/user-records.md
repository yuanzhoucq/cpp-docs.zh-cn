---
title: 用户记录 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- COLUMN_ENTRY_MAP
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: aea6b4b2ebb1a02e4ef669b437fbe7eb30937f9b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="user-records"></a>用户记录
若要使用静态的访问器 (一个访问器，它是派生自**CAccessor)**，你使用者都必须有用户记录。 用户记录是一个 c + + 类，其中包含用于处理输入或输出的数据元素。 ATL OLE DB 使用者向导生成为你的使用者的用户记录。 可以将方法添加到可选任务，例如处理命令的用户记录中。  
  
 下面的代码显示处理命令的示例记录。 用户记录中`BEGIN_COLUMN_MAP`表示从提供程序传递给使用者的数据行集。 `BEGIN_PARAM_MAP` 表示一组命令参数。 此示例使用[CCommand](../../data/oledb/ccommand-class.md)类来处理命令参数。 映射条目中的数据成员表示到一个连续每个类实例的内存块的偏移量。 `COLUMN_ENTRY`宏对应于`PROVIDER_COLUMN_ENTRY`提供商一侧上的宏。  
  
 有关详细信息**COLUMN_MAP**和**PARAM_MAP**宏，请参阅[用于 OLE DB 使用者模板的宏](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)。  
  
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
  
## <a name="wizard-generated-user-records"></a>向导生成的用户记录  
 如果你使用 ATL OLE DB 使用者向导生成一个使用者，则必须选择使用 OLE DB 模板或 OLE DB 属性。 生成的代码是在每个用例中不同。 有关此代码的详细信息，请参阅[使用者向导生成类](../../data/oledb/consumer-wizard-generated-classes.md)。  
  
## <a name="user-record-support-for-multiple-accessors"></a>用户记录支持多个访问器  
 你需要使用多个访问器的方案的详细讨论，请参阅[行集上使用多个访问器](../../data/oledb/using-multiple-accessors-on-a-rowset.md)。  
  
 下面的示例演示了修改，可在行集上支持多个访问器的用户记录。 而不是`BEGIN_COLUMN_MAP`和`END_COLUMN_MAP`，它使用[BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md)和[BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)为每个访问器。 `BEGIN_ACCESSOR`宏会指定访问器数 （从零偏移量） 和访问器是否为自动访问器。 Autoaccessors 调用`GetData`以检索自动上调用数据[MoveNext](../../data/oledb/crowset-movenext.md)。 非自动访问器要求你显式检索数据。 如果你正在绑定到可能不想为每个记录检索一个较大的数据字段 （如位图图像），请使用非自动访问器。  
  
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
  
## <a name="see-also"></a>请参阅  
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)