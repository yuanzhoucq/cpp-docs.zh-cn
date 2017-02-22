---
title: "CUtlProps::IsValidValue | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CUtlProps::IsValidValue"
  - "CUtlProps.IsValidValue"
  - "IsValidValue"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IsValidValue 方法"
ms.assetid: 1164556e-8d98-429c-a396-fc9a699e0e97
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CUtlProps::IsValidValue
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

用于在设置属性前验证值。  
  
## 语法  
  
```  
  
      virtual HRESULT CUtlPropsBase::IsValidValue(  
   ULONG /* iCurSet */,  
   DBPROP* pDBProp   
);  
```  
  
#### 参数  
 `iCurSet`  
 索引属性设置数组中；如果只有一个属性设置则为零。  
  
 `pDBProp`  
 在 [DBPROP](https://msdn.microsoft.com/en-us/library/ms717970.aspx) 结构中的属性 ID 和新值。  
  
## 返回值  
 标准版`HRESULT`。  默认返回值为 `S_OK`。  
  
## 备注  
 如果含有任何想要运行在要设置属性的值上的验证运行时，应重写此函数。  例如，可以验证**DBPROP\_AUTH\_PASSWORD** 的密码表确定有效值。  
  
## 要求  
 **头文件：** atldb.h  
  
## 请参阅  
 [CUtlProps 类](../../data/oledb/cutlprops-class.md)