---
title: "IConvertTypeImpl::CanConvert | Microsoft Docs"
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
  - "IConvertTypeImpl.CanConvert"
  - "CanConvert"
  - "IConvertTypeImpl::CanConvert"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CanConvert 方法"
ms.assetid: bdad6e95-bc0b-4427-9b5e-eea51f09f392
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IConvertTypeImpl::CanConvert
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供有关类型转换的状态信息。命令或对行集合。  
  
## 语法  
  
```  
  
      STDMETHOD(CanConvert)(   
   DBTYPE wFromType,   
   DBTYPE wToType,   
   DBCONVERTFLAGS dwConvertFlags    
);  
```  
  
#### 参数  
 参阅《*OLE DB 程序员参考》\) 中的*[IConvertType::CanConvert](https://msdn.microsoft.com/en-us/library/ms711224.aspx)。  
  
## 备注  
 使用 OLE DB 中 `MSADC.DLL`的数据转换。  
  
## 要求  
 **页眉：** atldb.h  
  
## 请参阅  
 [IConvertTypeImpl 类](../../data/oledb/iconverttypeimpl-class.md)