---
title: 修改 RMyProviderRowset 的继承 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- RMyProviderRowset
- inheritance [C++]
ms.assetid: 33089c90-98a4-43e7-8e67-d4bb137e267e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 407406683f03dbba2d582b1ae24d5cc3bb8680a5
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/30/2018
ms.locfileid: "39336460"
---
# <a name="modifying-the-inheritance-of-rmyproviderrowset"></a>修改 RMyProviderRowset 的继承
若要添加`IRowsetLocate`接口与简单的只读提供程序的示例中，修改的继承`RMyProviderRowset`。 最初，`RMyProviderRowset`继承`CRowsetImpl`。 您需要修改它以继承`CRowsetBaseImpl`。  
  
 若要执行此操作，创建一个新类， `CMyRowsetImpl`，MyProviderRS.h 中：  
  
```cpp
////////////////////////////////////////////////////////////////////////  
// MyProviderRS.h  
  
template <class T, class Storage, class CreatorClass, class ArrayType = CAtlArray<Storage>>  
class CMyRowsetImpl:  
   public CRowsetImpl<T, Storage, CreatorClass, ArrayType, CSimpleRow, IRowsetLocateImpl< T, IRowsetLocate >>  
{  
...  
};  
```  
  
 现在，编辑 COM 接口映射中 MyProviderRS.h 可按如下所示：  
  
```cpp  
BEGIN_COM_MAP(CMyRowsetImpl)  
   COM_INTERFACE_ENTRY(IRowsetLocate)  
   COM_INTERFACE_ENTRY_CHAIN(_RowsetBaseClass)  
END_COM_MAP()  
```  
  
 这将创建一个 COM 接口映射，以告知`CMyRowsetImpl`来调用`QueryInterface`同时`IRowset`和`IRowsetLocate`接口。 若要获取所有其他行集的实现类，映射链接`CMyRowsetImpl`类返回到`CRowsetBaseImpl`类定义由 OLE DB 模板; 该映射使用 COM_INTERFACE_ENTRY_CHAIN 宏，它指示要扫描的 COM 映射中的 OLE DB 模板`CRowsetBaseImpl`响应`QueryInterface`调用。  
  
 最后，链接`RAgentRowset`到`CMyRowsetBaseImpl`通过修改`RAgentRowset`继承`CMyRowsetImpl`，按如下所示：  
  
```cpp  
class RAgentRowset : public CMyRowsetImpl<RAgentRowset, CAgentMan, CMyProviderCommand>  
```  
  
 `RAgentRowset` 现在，可以使用`IRowsetLocate`接口，同时利用行集类的实现的其余部分。  
  
 完成此操作后，你可以[动态确定返回给使用者的列](../../data/oledb/dynamically-determining-columns-returned-to-the-consumer.md)。  
  
## <a name="see-also"></a>请参阅  
 [增强简单的只读提供程序](../../data/oledb/enhancing-the-simple-read-only-provider.md)