---
title: "CRowsetImpl 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CRowsetImpl"
  - "ATL.CRowsetImpl"
  - "ATL::CRowsetImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CRowsetImpl 类"
ms.assetid: e97614b3-b11d-4806-a0d3-b9401331473f
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# CRowsetImpl 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供标准 OLE DB 行集合，而无需实现许多实现多个接口继承。  
  
## 语法  
  
```  
template <  
   class T,  
   class Storage,  
   class CreatorClass,  
   class ArrayType = CAtlArray<Storage>,   
   class RowClass = CSimpleRow,   
   class RowsetInterface = IRowsetImpl < T, IRowset >   
>  
class CRowsetImpl :    
   public CComObjectRootEx<CreatorClass::_ThreadModel>,   
   public CRowsetBaseImpl<T, Storage, ArrayType, RowsetInterface>,   
   public IRowsetInfoImpl<T, CreatorClass::_PropClass>  
```  
  
#### 参数  
 `T`  
 从 `CRowsetImpl`派生的用户的类。  
  
 `Storage`  
 用户记录类。  
  
 `CreatorClass`  
 包含行集合属性的类；典型命令。  
  
 `ArrayType`  
 将行集合数据的存储空间中的类。  此参数默认为 `CAtlArray`，但也可以是必需，支持功能的任何类。  
  
## 成员  
  
### 方法  
  
|||  
|-|-|  
|[NameFromDBID](../../data/oledb/crowsetimpl-namefromdbid.md)|从 **DBID** 的字符串并将它传递的 `bstr`。|  
|[SetCommandText](../../data/oledb/crowsetimpl-setcommandtext.md)|验证和存储在两字符串的 **DBID**。[m\_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) \(和\)。[m\_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)|  
  
### 可重写的方法  
  
|||  
|-|-|  
|[GetColumnInfo](../../data/oledb/crowsetimpl-getcolumninfo.md)|检索特定客户端请求的列信息。|  
|[GetCommandFromID](../../data/oledb/crowsetimpl-getcommandfromid.md)|检查任何一个或者两个参数是否包含字符串值，如果可用，将字符串值转换为数据成员和 [m\_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)[m\_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)。|  
|[ValidateCommandID](../../data/oledb/crowsetimpl-validatecommandid.md)|检查任何一个或者两个 **DBID**数组是否包含字符串值，如果可用，将其复制到其数据成员和 [m\_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)[m\_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)。|  
  
### 数据成员  
  
|||  
|-|-|  
|[m\_rgRowData](../../data/oledb/crowsetimpl-m-rgrowdata.md)|默认情况下，在用户记录模板参数 templatizes 为 `CRowsetImpl`的 `CAtlArray`。  其他数组类类型可以通过更改 `CRowsetImpl`的 `ArrayType` 模板参数使用。|  
|[m\_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)|包含行集合的第的命令。|  
|[m\_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)|包含行集合的起始索引。|  
  
## 备注  
 以静态的向上转换后的形式中，`CRowsetImpl` 提供的重写。  方法控制特定行集将验证命令文本。  您可以通过将多继承的接口实现您自己的 `CRowsetImpl`样式类。  必须提供实现的唯一方法为 **执行**。  根据类型的行集合，可以创建 Creator 方法将需要 **执行**不同的签名。  例如，在中，如果使用 `CRowsetImpl`\- 实现的派生类架构行集合，则 **执行** 方法将具有以下签名：  
  
 `HRESULT Execute(LONG* pcRows, ULONG cRestrictions, const VARIANT* rgRestrictions)`  
  
 如果创建 `CRowsetImpl`\- 实现的派生类命令或会话的行集合，则 **执行** 方法将具有以下签名：  
  
 `HRESULT Execute(LONG* pcRows, DBPARAMS* pParams)`  
  
 实现任意 `CRowsetImpl`派生的 **执行** 方法，您必须亲自填充：，其中填充内部数据缓冲区 \(\)。[m\_rgRowData](../../data/oledb/crowsetimpl-m-rgrowdata.md)  
  
## 要求  
 **页眉：** atldb.h