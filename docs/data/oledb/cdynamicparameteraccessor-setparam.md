---
title: "CDynamicParameterAccessor::SetParam | Microsoft Docs"
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
  - "ATL::CDynamicParameterAccessor::SetParam"
  - "ATL::CDynamicParameterAccessor::SetParam<ctype>"
  - "CDynamicParameterAccessor.SetParam"
  - "ATL.CDynamicParameterAccessor.SetParam"
  - "SetParam"
  - "CDynamicParameterAccessor:SetParam"
  - "CDynamicParameterAccessor::SetParam<ctype>"
  - "CDynamicParameterAccessor::SetParam"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetParam 方法"
ms.assetid: e2349220-545c-46ad-90da-9113ac52551a
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDynamicParameterAccessor::SetParam
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用指定的 \(非 Unicode 字符串\) 数据，将参数设置缓冲区。  
  
## 语法  
  
```  
  
      template < class   
      ctype >  
bool SetParam(  
   DBORDINAL nParam,  
   const ctype* pData,  
   DBSTATUS status = DBSTATUS_S_OK  
) throw( );  
template < class ctype >  
bool SetParam(  
   TCHAR* pParamName,  
   const ctype* pData,  
   DBSTATUS status = DBSTATUS_S_OK  
) throw( );  
```  
  
#### 参数  
 `ctype`  
 是数据类型的模板参数。  
  
 `nParam`  
 \[in\] 参数数目 \(偏离 1\)。  参数 0 用于返回值保留的。  参数编号是基于其用 SQL 或存储过程调用的参数的索引。  例如：  
  
 [!code-cpp[NVC_OLEDB_Consumer#8](../../data/oledb/codesnippet/CPP/cdynamicparameteraccessor-setparam_1.cpp)]  
  
 `pParamName`  
 \[in\] 参数名。  
  
 `pData`  
 \[in\] 到包含数据的内存的指针将写入缓冲区。  
  
 *status*  
 \[in\] `DBSTATUS` 列状态。  有关 `DBSTATUS` 值的信息，请参见在 *OLE DB 程序员参考》\) 中的*[状态](https://msdn.microsoft.com/en-us/library/ms722617.aspx) 或为 oledb.h 中搜索 `DBSTATUS`。  
  
## 返回值  
 在成功的返回 **true** 或 **false** 上失败。  
  
 使用 `SetParam` 将缓冲区的 nonstring 的参数数据。  使用 [SetParamString](../../data/oledb/cdynamicparameteraccessor-setparamstring.md) 设置字符串在缓冲区的参数数据。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CDynamicParameterAccessor 类](../../data/oledb/cdynamicparameteraccessor-class.md)