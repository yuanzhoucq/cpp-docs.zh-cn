---
title: 在提供程序中引用属性
ms.date: 11/04/2016
helpviewer_keywords:
- OLE DB providers, properties
- references, to properties in providers
- referencing properties in providers
ms.assetid: bfbb3851-5eed-467a-a179-4a97a9515525
ms.openlocfilehash: d70a1901c457d9fbdbe8712d84999e256a54d0c2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209755"
---
# <a name="referencing-a-property-in-your-provider"></a>在提供程序中引用属性

查找所需属性的属性组和属性 ID。 有关详细信息，请参阅**OLE DB 程序员参考**中的[OLE DB 属性](/previous-versions/windows/desktop/ms722734(v=vs.85))。

下面的示例假设你要尝试从行集中获取属性。 使用会话或命令的代码是类似的，但使用的是不同的接口。

使用属性组作为构造函数的参数，创建[CDBPropSet](../../data/oledb/cdbpropset-class.md)对象。 例如：

```cpp
CDBPropSet propset(DBPROPSET_ROWSET);
```

调用[AddProperty](../../data/oledb/cdbpropset-addproperty.md)，并向其传递要赋给属性的属性 ID 和值。 值的类型取决于所使用的属性。

```cpp
CDBPropSet propset(DBPROPSET_ROWSET);

propset.AddProperty(DBPROP_IRowsetChange, true);

propset.AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_INSERT | DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_DELETE);
```

使用 `IRowset` 接口来调用 `GetProperties`。 将属性集作为参数传递。 下面是最终代码：

```cpp
CAgentRowset<CCustomCommand>* pRowset = (CAgentRowset<CCustomCommand>*) pThis;

CComQIPtr<IRowsetInfo, &IID_IRowsetInfo> spRowsetProps = pRowset;

DBPROPIDSET set;
set.AddPropertyID(DBPROP_BOOKMARKS);

DBPROPSET* pPropSet = NULL;
ULONG ulPropSet = 0;

HRESULT hr;

if (spRowsetProps)
   hr = spRowsetProps->GetProperties(1, &set, &ulPropSet, &pPropSet);

if (pPropSet)
{
   CComVariant var = pPropSet->rgProperties[0].vValue;
   CoTaskMemFree(pPropSet->rgProperties);
   CoTaskMemFree(pPropSet);

   if (SUCCEEDED(hr) && (var.boolVal == VARIANT_TRUE))
   {
      ...  // Use property here
   }
}
```

## <a name="see-also"></a>另请参阅

[使用 OLE DB 提供程序模板](../../data/oledb/working-with-ole-db-provider-templates.md)
