---
title: 使用现有 ADO 记录集
ms.date: 11/04/2016
helpviewer_keywords:
- ADO recordsets [C++]
- OLE DB consumer templates, ADO recordsets
- recordsets [C++], using in OLE DB
ms.assetid: a9b1de8a-d379-49b1-a26e-578741e9f6a8
ms.openlocfilehash: 62e56b818a766bf3b7efddf9243ffd47ad2cb46f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50610595"
---
# <a name="using-an-existing-ado-recordset"></a>使用现有 ADO 记录集

若要混合使用 OLE DB 使用者模板和活动数据对象 (ADO)，使用 ADO 打开记录集 （对应于 OLE DB 使用者模板中的行集）。 在必须记录集，请执行以下操作来连接到 OLE DB 行集：

1. 调用`QueryInterface`有关`IRowset`和`IAccessor`指针。

    ```cpp
    IRowset* lpRowset = NULL;
    IAccessor* lpAccessor = NULL;
    lpUnk->QueryInterface(IID_IRowset, (void**)&lpRowset);
    lpUnk->QueryInterface(IID_IAccessor, (void**)&lpAccessor);
    ```

    > [!NOTE]
    > *lpUnk*指向`IUnknown`的 ADO 记录集对象。

1. 附加到其相应的 OLE DB 使用者模板类的访问器和行集。

    ```cpp
    CRowset rs;
    CAccessor accessor;

    accessor.AddAccessorInfo(0ul);      // 0 is the ordinal of an ADO accessor
    rs.m_spRowset.Attach(lpRowset);      // use the Attach method of CComPtr<>
    rs.SetAccessor(accessor);
    ```

## <a name="see-also"></a>请参阅

[使用访问器](../../data/oledb/using-accessors.md)