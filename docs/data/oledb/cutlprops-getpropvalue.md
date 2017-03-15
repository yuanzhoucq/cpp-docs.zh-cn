---
title: "CUtlProps::GetPropValue | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CUtlProps::GetPropValue"
  - "CUtlProps.GetPropValue"
  - "GetPropValue"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetPropValue 方法"
ms.assetid: 9a3fbadb-7814-48f7-96a4-b960fc4ecf2e
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CUtlProps::GetPropValue
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

从属性集合获取属性。  
  
## 语法  
  
```  
  
      OUT_OF_LINE HRESULT GetPropValue(  
   const GUID* pguidPropSet,  
   DBPROPID dwPropId,  
   VARIANT* pvValue   
);  
```  
  
#### 参数  
 `pguidPropSet`  
 \[in\] PropSet 的 GUID。  
  
 `dwPropId`  
 \[in\] 属性索引。  
  
 `pvValue`  
 \[in\] 将包含新属性值的变量的指针。  
  
## 返回值  
 在失败和 `S_OK` 的`Failure`，如果成功。  
  
## 要求  
 **头文件：** atldb.h  
  
## 请参阅  
 [CUtlProps 类](../../data/oledb/cutlprops-class.md)