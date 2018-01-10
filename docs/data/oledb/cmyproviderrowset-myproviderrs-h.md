---
title: "CMyProviderRowset (MyProviderRS.H) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- cmyproviderrowset
- myproviderrs.h
dev_langs: C++
helpviewer_keywords:
- OLE DB providers, wizard-generated files
- CMyProviderRowset class in MyProviderRS.H
ms.assetid: 7ba1a124-3842-40eb-a36b-302190a1af3a
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 702a86d600a1ff3623ce86c1ad36da9b15876c61
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cmyproviderrowset-myproviderrsh"></a>CMyProviderRowset (MyProviderRS.H)
向导将生成行集对象的条目。 在此例中，它称为 `CMyProviderRowset`。 `CMyProviderRowset`类继承的 OLE DB 提供程序类调用`CRowsetImpl`，该类可实现行集对象的所有必要的接口。 下面的代码演示的继承链`CRowsetImpl`:  
  
```  
template <class T, class Storage, class CreatorClass,   
   class ArrayType = CAtlArray<Storage> >  
class CMyRowsetImpl:  
   public CRowsetImpl<T, Storage, CreatorClass, ArrayType,   
      CSimpleRow, IRowsetLocateImpl< T > >  
```  
  
 `CRowsetImpl`此外使用`IAccessor`和`IColumnsInfo`接口。 它为表中的输出字段中使用这些接口。 此类还提供的实现**IRowsetIdentity**，这样的使用者确定两个行是否相同。 `IRowsetInfo`接口实现行集对象的属性。 **IConvertType**接口允许提供商联系以解决请求的使用者的数据类型和所使用的提供程序之间的差异。  
  
 `IRowset`接口实际处理数据检索。 使用者首先调用调用的方法`GetNextRows`将处理返回的行，称为**HROW**。 然后，使用者调用**irowset:: Getdata**与**HROW**以检索请求的数据。  
  
 `CRowsetImpl`此外采用多个模板参数。 这些参数允许你确定如何`CRowsetImpl`类处理数据。 `ArrayType`自变量可以确定哪些存储机制用于存储行数据。 **RowClass**参数指定哪些类包含**HROW**。  
  
 **RowsetInterface**参数使你可以还使用`IRowsetLocate`或`IRowsetScroll`接口。 `IRowsetLocate`和`IRowsetScroll`接口都继承自`IRowset`。 因此，OLE DB 提供程序模板必须为这些接口提供特殊处理。 如果你想要使用这些接口之一，你需要使用此参数。  
  
## <a name="see-also"></a>请参阅  
 [提供程序向导生成的文件](../../data/oledb/provider-wizard-generated-files.md)