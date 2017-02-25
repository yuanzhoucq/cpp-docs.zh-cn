---
title: "CDataSource::GetProperty | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::CDataSource::GetProperty"
  - "ATL.CDataSource.GetProperty"
  - "CDataSource.GetProperty"
  - "CDataSource::GetProperty"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetProperty 方法"
ms.assetid: 6531147c-b164-4ab5-a4a7-509634b85b4d
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CDataSource::GetProperty
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

为连接的数据源对象返回指定属性的值。  
  
## 语法  
  
```  
  
      HRESULT GetProperty(   
   const GUID& guid,   
   DBPROPID propid,   
   VARIANT* pVariant    
) const throw( );  
```  
  
#### 参数  
 `guid`  
 \[in\] 标识返回属性的属性集的 GUID 。  
  
 `propid`  
 \[in\] 属性 ID 可以为属性返回。  
  
 *pVariant*  
 \[out\] 指向一个 **GetProperty** 返回属性值的变量的指针。  
  
## 返回值  
 标准版`HRESULT`。  
  
## 备注  
 要获取多个属性，请使用 [GetProperties](../../data/oledb/cdatasource-getproperties.md)。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CDataSource 类](../../data/oledb/cdatasource-class.md)