---
title: "IConvertTypeImpl 类 | Microsoft Docs"
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
  - "ATL.IConvertTypeImpl<T>"
  - "IConvertTypeImpl"
  - "ATL.IConvertTypeImpl"
  - "ATL::IConvertTypeImpl"
  - "ATL::IConvertTypeImpl<T>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IConvertTypeImpl 类"
ms.assetid: 7f81e79e-7d3f-4cbe-b93c-d632a94b15f6
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IConvertTypeImpl 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供[IConvertType](https://msdn.microsoft.com/en-us/library/ms715926.aspx)接口的实现。  
  
## 语法  
  
```  
template <class T>  
class ATL_NO_VTABLE IConvertTypeImpl   
   : public IConvertType, public CConvertHelper  
```  
  
#### 参数  
 `T`  
 类是从`IConvertTypeImpl` 中派生的。  
  
## 成员  
  
### 接口方法  
  
|||  
|-|-|  
|[CanConvert](../../data/oledb/iconverttypeimpl-canconvert.md)|提供有关类型转换的状态信息命令或对行集合。|  
  
## 备注  
 此接口是必须是命令索引、行集合和行集合。  通过委托转换 OLE DB 提供的对象实现**IConvertTypeImpl** 接口。  
  
## 要求  
 **头文件:** atldb.h  
  
## 请参阅  
 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)