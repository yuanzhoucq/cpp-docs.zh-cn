---
title: CCustomRowset (CustomRS.H)
ms.date: 10/22/2018
f1_keywords:
- cmyproviderrowset
- ccustomrowset
helpviewer_keywords:
- OLE DB providers, wizard-generated files
- CMyProviderRowset class in MyProviderRS.H
- CCustomRowset class in CustomRS.H
ms.assetid: 7ba1a124-3842-40eb-a36b-302190a1af3a
ms.openlocfilehash: 2c84ff359bdbb39f281928fa0135edd40b1f7d20
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79545803"
---
# <a name="ccustomrowset-customrsh"></a>CCustomRowset (CustomRS.H)

向导将生成行集对象的条目。 在这种情况下，它被称为 `CCustomRowset`。 `CCustomRowset` 类继承自名为 `CRowsetImpl`的 OLE DB 提供程序类，后者实现行集对象的所有必需接口。 下面的代码演示 `CRowsetImpl`的继承链：

```cpp
template <class T, class Storage, class CreatorClass, 
   class ArrayType = CAtlArray<Storage>>
class CMyRowsetImpl:
   public CRowsetImpl<T, Storage, CreatorClass, ArrayType, 
      CSimpleRow, IRowsetLocateImpl< T >>
```

`CRowsetImpl` 还使用 `IAccessor` 和 `IColumnsInfo` 接口。 它将这些接口用于表中的输出字段。 类还为 `IRowsetIdentity`提供了一个实现，该实现允许使用者确定两行是否相同。 `IRowsetInfo` 接口实现行集对象的属性。 `IConvertType` 接口允许提供程序解决使用者请求的数据类型与提供程序使用的数据类型之间的差异。

`IRowset` 接口实际处理数据检索。 使用者首先调用名为 `GetNextRows` 的方法，以返回称为 `HROW`的行的句柄。 然后，使用者使用该 `HROW` 调用 `IRowset::GetData` 以检索请求的数据。

`CRowsetImpl` 也使用几个模板参数。 这些参数使你可以确定 `CRowsetImpl` 类如何处理数据。 `ArrayType` 参数允许您确定用于存储行数据的存储机制。 *RowClass*参数指定哪个类包含 `HROW`。

使用*RowsetInterface*参数，还可以使用 `IRowsetLocate` 或 `IRowsetScroll` 接口。 `IRowsetLocate` 和 `IRowsetScroll` 接口都继承自 `IRowset`。 因此，OLE DB 提供程序模板必须为这些接口提供特殊处理。 如果要使用这两个接口中的任何一个，则需要使用此参数。

## <a name="see-also"></a>另请参阅

[提供程序向导生成的文件](../../data/oledb/provider-wizard-generated-files.md)<br/>
