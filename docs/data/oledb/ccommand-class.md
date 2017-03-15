---
title: "CCommand 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::CCommand"
  - "CCommand"
  - "ATL.CCommand"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CCommand 类"
ms.assetid: 0760bfc5-b9ee-4aee-8e54-31bd78714d3a
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# CCommand 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供方法设置并执行命令。  
  
## 语法  
  
```  
template <  
   class TAccessor = CNoAccessor,  
   template < typename T > class TRowset = CRowset,  
   class TMultiple = CNoMultipleResults   
>  
class CCommand :   
   public CAccessorRowset <  
      TAccessor,   
      TRowset   
   >,  
   public CCommandBase,  
   public TMultiple  
```  
  
#### 参数  
 `TAccessor`  
 该访问器类型的类 \(如 `CDynamicParameterAccessor`、`CDynamicStringAccessor`或 `CEnumeratorAccessor`\)。想让命令使用。  默认为 `CNoAccessor`，指定该类不是支持参数或输出列。  
  
 `TRowset`  
 该访问器类型的类 \(如 `CArrayRowset`、`CNoRowset`或 \)。想让命令使用。  默认值为 `CRowset`。  
  
 `TMultiple`  
 若要使用中返回多个结果的 OLE DB 中，指定命令。[CMultipleResults](../../data/oledb/cmultipleresults-class.md) 否则，应使用 [CNoMultipleResults](../../data/oledb/cnomultipleresults-class.md)。  有关详细信息，请参见 [IMultipleResults](https://msdn.microsoft.com/en-us/library/ms721289.aspx)。  
  
## 成员  
  
### 方法  
  
|||  
|-|-|  
|[关闭](../../data/oledb/ccommand-close.md)|关闭当前选项卡。|  
|[GetNextResult](../../data/oledb/ccommand-getnextresult.md)|当使用多个结果集时，将下一结果。|  
|[打开](../../data/oledb/ccommand-open.md)|执行和可选的绑定命令。|  
  
### 继承的方法  
  
|||  
|-|-|  
|[Create](../../data/oledb/ccommand-create.md)|创建指定的会话的新命令，然后将该命令文本。|  
|[CreateCommand](../../data/oledb/ccommand-createcommand.md)|创建新命令。|  
|[GetParameterInfo](../../data/oledb/ccommand-getparameterinfo.md)|获取命令、其名称及其类型的列表。|  
|[准备](../../data/oledb/ccommand-prepare.md)|验证并优化当前命令。|  
|[ReleaseCommand](../../data/oledb/ccommand-releasecommand.md)|如有必要，释放参数访问器，然后释放命令。|  
|[SetParameterInfo](../../data/oledb/ccommand-setparameterinfo.md)|指定每个命令的本机类型。|  
|[Unprepare](../../data/oledb/ccommand-unprepare.md)|放弃当前命令执行计划。|  
  
## 备注  
 当需要执行基于参数的操作或执行命令时，请使用此类。  如果仅需要打开一简单行集合，请使用 [CTable](../../data/oledb/ctable-class.md)。  
  
 使用的访问器类来确定参数和数据绑定方法。  
  
 不能将存储过程与 Jet 的 OLE DB 提供程序一起使用，因为该提供程序不支持存储过程；查询字符串中只允许使用常数。  
  
## 要求  
 **Header:** atldbcli.h  
  
## 请参阅  
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)