---
title: 使用现有 ADO 记录集
ms.date: 11/04/2016
helpviewer_keywords:
- ADO recordsets [C++]
- OLE DB consumer templates, ADO recordsets
- recordsets [C++], using in OLE DB
ms.assetid: a9b1de8a-d379-49b1-a26e-578741e9f6a8
ms.openlocfilehash: 48f6eb3bac34b37f495b9492e19b4197ed69cca3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209347"
---
# <a name="using-an-existing-ado-recordset"></a>使用现有 ADO 记录集

若要混合 OLE DB 使用者模板和活动数据对象（ADO），请使用 ADO 打开记录集（对应于 OLE DB 使用者模板中的行集）。 如果有记录集，请执行以下操作来连接到 OLE DB 行集：

1. 调用 `IRowset` 和 `IAccessor` 指针 `QueryInterface`。

    ```cpp
    IRowset* lpRowset = NULL;
    IAccessor* lpAccessor = NULL;
    lpUnk->QueryInterface(IID_IRowset, (void**)&lpRowset);
    lpUnk->QueryInterface(IID_IAccessor, (void**)&lpAccessor);
    ```

    > [!NOTE]
    > *lpUnk*指向 ADO 记录集的 `IUnknown` 对象。

1. 将访问器和行集附加到相应的 OLE DB 使用者模板类中。

    ```cpp
    CRowset rs;
    CAccessor accessor;

    accessor.AddAccessorInfo(0ul);      // 0 is the ordinal of an ADO accessor
    rs.m_spRowset.Attach(lpRowset);      // use the Attach method of CComPtr<>
    rs.SetAccessor(accessor);
    ```

## <a name="see-also"></a>另请参阅

[使用访问器](../../data/oledb/using-accessors.md)
