---
title: "修改 RMyProviderRowset 的继承 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "继承 [C++]"
  - "RMyProviderRowset"
ms.assetid: 33089c90-98a4-43e7-8e67-d4bb137e267e
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 修改 RMyProviderRowset 的继承
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

若要将 `IRowsetLocate` 接口添加到简单只读提供程序示例，请修改 **RMyProviderRowset** 的继承。  开始时，**RMyProviderRowset** 从 `CRowsetImpl` 继承。  需要修改它以从 **CRowsetBaseImpl** 继承。  
  
 若要执行此操作，请在 MyProviderRS.h 文件中创建新类 `CMyRowsetImpl`：  
  
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
  
 现在，在 MyProviderRS.h 中将 COM 接口映射编辑成下面这样：  
  
```  
BEGIN_COM_MAP(CMyRowsetImpl)  
   COM_INTERFACE_ENTRY(IRowsetLocate)  
   COM_INTERFACE_ENTRY_CHAIN(_RowsetBaseClass)  
END_COM_MAP()  
```  
  
 这将创建通知 `CMyRowsetImpl` 为 `IRowset` 和 `IRowsetLocate` 接口都调用 **QueryInterface** 的 COM 接口映射。  为获取其他行集合类的所有实现，该映射将 `CMyRowsetImpl` 类链接回 OLE DB 模板定义的 **CRowsetBaseImpl** 类；该映射使用 COM\_INTERFACE\_ENTRY\_CHAIN 宏，通知 OLE DB 模板扫描 **CRowsetBaseImpl** 中的 COM 映射以响应 `QueryInterface` 调用。  
  
 最后，通过修改 `RAgentRowset` 从 `CMyRowsetImpl` 继承，将 `RAgentRowset` 链接到 `CMyRowsetBaseImpl`，如下所示：  
  
```  
class RAgentRowset : public CMyRowsetImpl<RAgentRowset, CAgentMan, CMyProviderCommand>  
```  
  
 `RAgentRowset` 现在可以使用 `IRowsetLocate` 接口，同时利用行集合类的其余实现。  
  
 当这些完成后，可以[动态确定返回给使用者的列](../../data/oledb/dynamically-determining-columns-returned-to-the-consumer.md)。  
  
## 请参阅  
 [增强简单的只读提供程序](../../data/oledb/enhancing-the-simple-read-only-provider.md)