---
title: "修改 RMyProviderRowset 的继承 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- RMyProviderRowset
- inheritance [C++]
ms.assetid: 33089c90-98a4-43e7-8e67-d4bb137e267e
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ff6e953bf706e0e8767fe6f97fe1d31b70431d08
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="modifying-the-inheritance-of-rmyproviderrowset"></a>修改 RMyProviderRowset 的继承
若要添加`IRowsetLocate`接口与简单只读提供程序的示例中，修改的继承**RMyProviderRowset**。 最初， **RMyProviderRowset**继承自`CRowsetImpl`。 你需要修改从继承**CRowsetBaseImpl**。  
  
 若要执行此操作，创建一个新的类， `CMyRowsetImpl`，MyProviderRS.h 中：  
  
```  
////////////////////////////////////////////////////////////////////////  
// MyProviderRS.h  
  
template <class T, class Storage, class CreatorClass, class ArrayType = CAtlArray<Storage> >  
class CMyRowsetImpl:  
   public CRowsetImpl<T, Storage, CreatorClass, ArrayType, CSimpleRow, IRowsetLocateImpl< T, IRowsetLocate > >  
{  
...  
};  
```  
  
 现在，编辑中 MyProviderRS.h 要如下所示的 COM 接口映射：  
  
```  
BEGIN_COM_MAP(CMyRowsetImpl)  
   COM_INTERFACE_ENTRY(IRowsetLocate)  
   COM_INTERFACE_ENTRY_CHAIN(_RowsetBaseClass)  
END_COM_MAP()  
```  
  
 这将创建 COM 接口映射中，它告知`CMyRowsetImpl`调用**QueryInterface**两个`IRowset`和`IRowsetLocate`接口。 若要获取所有其他行集的实现类，映射链接`CMyRowsetImpl`类回**CRowsetBaseImpl**类定义由 OLE DB 模板; 地图使用 COM_INTERFACE_ENTRY_CHAIN 宏，它指示OLE DB 模板扫描 COM 映射中**CRowsetBaseImpl**以响应`QueryInterface`调用。  
  
 最后，链接`RAgentRowset`到`CMyRowsetBaseImpl`通过修改`RAgentRowset`要从其继承`CMyRowsetImpl`、，如下所示：  
  
```  
class RAgentRowset : public CMyRowsetImpl<RAgentRowset, CAgentMan, CMyProviderCommand>  
```  
  
 `RAgentRowset`现在可以使用`IRowsetLocate`接口，同时利用行集类的实现的其余部分。  
  
 完成此操作后，你可以[动态确定返回给使用者的列](../../data/oledb/dynamically-determining-columns-returned-to-the-consumer.md)。  
  
## <a name="see-also"></a>请参阅  
 [增强简单的只读提供程序](../../data/oledb/enhancing-the-simple-read-only-provider.md)