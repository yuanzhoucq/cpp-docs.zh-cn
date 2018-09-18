---
title: 用户记录 |Microsoft Docs
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
ms.openlocfilehash: 4389fdd35c36a8f7708361176889111b1665f2c6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46073639"
---
# <a name="user-records"></a>用户记录

若要使用静态访问器 (取值函数，它是派生自`CAccessor`)，使用者必须具有用户记录。 用户记录是包含用于处理输入或输出的数据元素的 c + + 类。 在 ATL OLE DB 使用者向导生成的使用者用户记录。 可以将方法添加到可选任务，如处理的命令的用户记录。  
  
下面的代码演示示例记录的处理命令。 用户记录中 BEGIN_COLUMN_MAP 表示传递给使用者从提供程序的数据行集。 BEGIN_PARAM_MAP 表示一组命令参数。 此示例使用[CCommand](../../data/oledb/ccommand-class.md)类来处理命令参数。 映射条目中的数据成员表示到一个连续的类的每个实例的内存块的偏移量。 COLUMN_ENTRY 宏对应于提供者端 PROVIDER_COLUMN_ENTRY 宏。  
  
有关 COLUMN_MAP 和 PARAM_MAP 宏的详细信息，请参阅[OLE DB 使用者模板的宏](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)。  
  
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

如果使用 ATL OLE DB 使用者向导生成一个使用者，您可以使用 OLE DB 模板或 OLE DB 属性的选择。 生成的代码是在每种情况不同。 有关此代码的详细信息，请参阅[使用者向导生成的类](../../data/oledb/consumer-wizard-generated-classes.md)。  
  
## <a name="user-record-support-for-multiple-accessors"></a>对多个访问器的用户记录支持  

您需要在其中使用多个访问器的方案的详细讨论，请参阅[行集上使用多个访问器](../../data/oledb/using-multiple-accessors-on-a-rowset.md)。  
  
下面的示例显示了修改，以在行集上支持多个访问器的用户记录。 而不是 BEGIN_COLUMN_MAP 和 END_COLUMN_MAP，它使用[BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md)并[BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)为每个访问器。 BEGIN_ACCESSOR 宏指定访问器数 （从零开始的偏移量） 以及访问器是否为自动访问器。 Autoaccessors 调用`GetData`来检索数据自动在调用[MoveNext](../../data/oledb/crowset-movenext.md)。 非自动访问器需要显式检索的数据。 如果要绑定到可能不想为每条记录检索一个较大的数据字段 （如位图图像），请使用非自动访问器。  
  
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