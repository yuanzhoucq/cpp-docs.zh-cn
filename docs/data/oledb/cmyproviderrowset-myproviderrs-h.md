---
title: "CMyProviderRowset (MyProviderRS.H) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cmyproviderrowset"
  - ""myproviderrs.h""
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MyProviderRS.H 中的 CMyProviderRowset 类"
  - "OLE DB 提供程序, 向导生成的文件"
ms.assetid: 7ba1a124-3842-40eb-a36b-302190a1af3a
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMyProviderRowset (MyProviderRS.H)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

向导生成行集合对象的项。  此例中它称为 `CMyProviderRowset`。  `CMyProviderRowset` 类从 OLE DB 提供程序类 `CRowsetImpl` 继承，该类可实现行集合对象所需的全部接口。  以下代码显示 `CRowsetImpl` 的继承链：  
  
```  
template <class T, class Storage, class CreatorClass,   
   class ArrayType = CAtlArray<Storage> >  
class CMyRowsetImpl:  
   public CRowsetImpl<T, Storage, CreatorClass, ArrayType,   
      CSimpleRow, IRowsetLocateImpl< T > >  
```  
  
 `CRowsetImpl` 也使用 `IAccessor` 和 `IColumnsInfo` 接口。  它对表中的输出字段使用这些接口。  该类还提供 **IRowsetIdentity** 的实现，该实现可确定两行是否相同。  `IRowsetInfo` 接口实现行集合对象的属性。  **IConvertType** 接口允许提供程序解析使用者请求的数据类型和提供程序使用的数据类型之间的差异。  
  
 `IRowset` 接口实际处理数据检索。  使用者首先调用名为 `GetNextRows` 的方法，将处理返回给称为 **HROW** 的行。  然后使用者用该 **HROW** 调用 **IRowset::GetData** 以检索请求的数据。  
  
 `CRowsetImpl` 还使用若干模板参数。  使用这些参数可确定 `CRowsetImpl` 类处理数据的方式。  `ArrayType` 参数使您得以确定用于存储行数据的存储机制。  **RowClass** 参数指定包含 **HROW** 的类。  
  
 使用 **RowsetInterface** 参数还可以使用 `IRowsetLocate` 或 `IRowsetScroll` 接口。  `IRowsetLocate` 和 `IRowsetScroll` 接口都从 `IRowset` 继承。  因此，OLE DB 提供程序模板必须为这些接口提供特殊处理。  如果要使用这两个接口中的任何一个，都需要使用此参数。  
  
## 请参阅  
 [提供程序向导生成的文件](../../data/oledb/provider-wizard-generated-files.md)