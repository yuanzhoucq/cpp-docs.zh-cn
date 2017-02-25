---
title: "CDBPropSet::AddProperty | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDBPropSet::AddProperty"
  - "CDBPropSet.AddProperty"
  - "AddProperty"
  - "ATL::CDBPropSet::AddProperty"
  - "ATL.CDBPropSet.AddProperty"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AddProperty 方法"
ms.assetid: dc9539d3-1ee4-40f3-9281-2068e6d65e93
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# CDBPropSet::AddProperty
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将属性添加到属性集。  
  
## 语法  
  
```  
  
      bool AddProperty(   
   DWORD dwPropertyID,   
   const VARIANT& var,   
   DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED    
) throw( );  
bool AddProperty(  
   DWORD dwPropertyID,  
   LPCSTR szValue,  
   DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED    
) throw( );  
bool AddProperty(  
   DWORD dwPropertyID,  
   LPCWSTR szValue,   
   DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED    
) throw( );  
bool AddProperty(  
   DWORD dwPropertyID,  
   bool bValue,  
   DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED    
) throw( );  
bool AddProperty(  
   DWORD dwPropertyID,  
   BYTE bValue,  
   DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED    
);  
bool AddProperty(  
   DWORD dwPropertyID,  
   short nValue,  
   DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED    
);  
bool AddProperty(  
   DWORD dwPropertyID,  
   long nValue,  
   DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED    
);  
bool AddProperty(  
   DWORD dwPropertyID,  
   float fltValue,  
   DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED    
);  
bool AddProperty(  
   DWORD dwPropertyID,  
   double dblValue,  
   DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED    
) throw( );  
bool AddProperty(  
   DWORD dwPropertyID,  
   CY cyValue,  
   DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED    
) throw( );  
```  
  
#### 参数  
 *dwPropertyID*  
 \[in\] 要添加的属性指定的 ID。  用于初始化 `DBPROP` 结构的 **dwPropertyID** 添加到属性集。  
  
 `var`  
 \[in\] 用于的变量初始化 `DBPROP` 结构的属性值添加到属性集。  
  
 `szValue`  
 \[in\] 用于字符串初始化 `DBPROP` 结构的属性值添加到属性集。  
  
 `bValue`  
 \[in\] 用于的 **BYTE** 或布尔值初始化 `DBPROP` 结构的属性值添加到属性集。  
  
 `nValue`  
 \[in\] 用于的整数值初始化 `DBPROP` 结构的属性值添加到属性集。  
  
 *fltValue*  
 \[in\] 使用的浮点值初始化 `DBPROP` 结构的属性值添加到属性集。  
  
 `dblValue`  
 \[in\] 用于的双精度浮点值初始化 `DBPROP` 结构的属性值添加到属性集。  
  
 `cyValue`  
 \[in\] 用于的 CY 货币值初始化 `DBPROP` 结构的属性值添加到属性集。  
  
## 返回值  
 **true** 属性，则说明已成功添加元素。  否则为 **false**。  
  
## 要求  
 **标头:** atldbcli.h  
  
## 请参阅  
 [CDBPropSet 类](../../data/oledb/cdbpropset-class.md)   
 [DBPROP Structure](https://msdn.microsoft.com/en-us/library/ms717970.aspx)