---
title: 修改的 RCustomRowset
ms.date: 10/26/2018
helpviewer_keywords:
- RMyProviderRowset
- inheritance [C++]
- RCustomRowset
ms.assetid: 33089c90-98a4-43e7-8e67-d4bb137e267e
ms.openlocfilehash: 51cca65b6b55de8b628cb5d233ab06f0101f466d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50637952"
---
# <a name="modifying-the-inheritance-of-rcustomrowset"></a>修改的 RCustomRowset

若要添加`IRowsetLocate`接口与简单的只读提供程序的示例中，修改的继承`RCustomRowset`。 最初，`RCustomRowset`继承`CRowsetImpl`。 您需要修改它以继承`CRowsetBaseImpl`。

若要执行此操作，创建一个新类， `CCustomRowsetImpl`，CustomRS.h 中：

```cpp
////////////////////////////////////////////////////////////////////////
// CustomRS.h

template <class T, class Storage, class CreatorClass, class ArrayType = CAtlArray<Storage>>
class CMyRowsetImpl:
   public CRowsetImpl<T, Storage, CreatorClass, ArrayType, CSimpleRow, IRowsetLocateImpl< T, IRowsetLocate >>
{
...
};
```

现在，编辑中的 COM 接口映射*自定义*RS.h 可按如下所示：

```cpp
BEGIN_COM_MAP(CMyRowsetImpl)
   COM_INTERFACE_ENTRY(IRowsetLocate)
   COM_INTERFACE_ENTRY_CHAIN(_RowsetBaseClass)
END_COM_MAP()
```

此代码将创建一个 COM 接口映射，以告知`CMyRowsetImpl`来调用`QueryInterface`同时`IRowset`和`IRowsetLocate`接口。 若要获取所有其他行集的实现类，映射链接`CMyRowsetImpl`类返回到`CRowsetBaseImpl`类定义由 OLE DB 模板; 该映射使用 COM_INTERFACE_ENTRY_CHAIN 宏，它指示要扫描的 COM 映射中的 OLE DB 模板`CRowsetBaseImpl`响应`QueryInterface`调用。

最后，链接`RAgentRowset`到`CMyRowsetBaseImpl`通过修改`RAgentRowset`继承`CMyRowsetImpl`，按如下所示：

```cpp
class RAgentRowset : public CMyRowsetImpl<RAgentRowset, CAgentMan, CCustomCommand>
```

`RAgentRowset` 现在，可以使用`IRowsetLocate`接口，同时利用行集类的实现的其余部分。

完成此操作后，你可以[动态确定返回给使用者的列](../../data/oledb/dynamically-determining-columns-returned-to-the-consumer.md)。

## <a name="see-also"></a>请参阅

[增强简单的只读提供程序](../../data/oledb/enhancing-the-simple-read-only-provider.md)<br/>
