---
title: CCustomRowset (CustomRS.H) |Microsoft Docs
ms.custom: ''
ms.date: 10/22/2018
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- cmyproviderrowset
- myproviderrs.h
- ccustomrowset
- customrs.h
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, wizard-generated files
- CMyProviderRowset class in MyProviderRS.H
- CCustomRowset class in CustomRS.H
ms.assetid: 7ba1a124-3842-40eb-a36b-302190a1af3a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4808f9165fa6f139b0d3b576620e9db80eb360d3
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50076992"
---
# <a name="ccustomrowset-customrsh"></a>CCustomRowset (CustomRS.H)

该向导生成的行集对象的项。 在此例中，它称为 `CCustomRowset`。 `CCustomRowset`类继承自调用一个 OLE DB 提供程序类`CRowsetImpl`，它可实现行集对象的所有必要的接口。 下面的代码演示的继承链`CRowsetImpl`:

```cpp
template <class T, class Storage, class CreatorClass,
   class ArrayType = CAtlArray<Storage>>
class CMyRowsetImpl:
   public CRowsetImpl<T, Storage, CreatorClass, ArrayType,
      CSimpleRow, IRowsetLocateImpl< T >>
```

`CRowsetImpl` 此外使用`IAccessor`和`IColumnsInfo`接口。 它使用这些接口在表中的输出字段。 类还提供一个实现`IRowsetIdentity`，它允许使用方以确定两个行是否相同。 `IRowsetInfo`接口实现行集对象的属性。 `IConvertType`接口允许提供商联系以解决请求的使用者的数据类型和所使用的提供程序之间的差异。

`IRowset`接口实际上处理数据检索。 使用者首先调用调用的方法`GetNextRows`若要返回的句柄到行中称为`HROW`。 然后，使用者调用`IRowset::GetData`考虑到这`HROW`来检索所请求的数据。

`CRowsetImpl` 此外使用几个模板参数。 这些参数可用于确定如何`CRowsetImpl`类处理数据。 `ArrayType`参数允许您确定哪些存储机制，用于存储行数据。 *RowClass*参数指定哪些类包含`HROW`。

*RowsetInterface*参数，可使用`IRowsetLocate`或`IRowsetScroll`接口。 `IRowsetLocate`并`IRowsetScroll`接口都继承自`IRowset`。 因此，OLE DB 提供程序模板必须为这些接口提供特殊处理。 如果你想要使用这些接口，您需要使用此参数。

## <a name="see-also"></a>请参阅

[提供程序向导生成的文件](../../data/oledb/provider-wizard-generated-files.md)