---
title: 在提供程序中引用属性
ms.date: 11/04/2016
helpviewer_keywords:
- OLE DB providers, properties
- references, to properties in providers
- referencing properties in providers
ms.assetid: bfbb3851-5eed-467a-a179-4a97a9515525
ms.openlocfilehash: d8c775af8f887deb7bf49016f9716fa0a76d2439
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57415937"
---
# <a name="referencing-a-property-in-your-provider"></a>在提供程序中引用属性

找到所需的属性的属性组和属性 ID。 有关详细信息，请参阅[OLE DB 属性](/previous-versions/windows/desktop/ms722734(v=vs.85))中**OLE DB 程序员参考**。

下面的示例假定你正在尝试获取从行集中的属性。 使用会话或命令的代码类似，但使用不同的接口。

创建[CDBPropSet](../../data/oledb/cdbpropset-class.md)对象作为构造函数的参数中使用属性组。 例如：

```cpp
CDBPropSet propset(DBPROPSET_ROWSET);
```

调用[AddProperty](../../data/oledb/cdbpropset-addproperty.md)，将其传递属性 ID 和要分配给属性的值。 值的类型取决于正在使用的属性。

```cpp
CDBPropSet propset(DBPROPSET_ROWSET);

propset.AddProperty(DBPROP_IRowsetChange, true);

propset.AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_INSERT | DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_DELETE);
```

使用`IRowset`接口来调用`GetProperties`。 将属性设置作为参数传递。 下面是最终代码：

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

## <a name="see-also"></a>请参阅

[使用 OLE DB 提供程序模板](../../data/oledb/working-with-ole-db-provider-templates.md)