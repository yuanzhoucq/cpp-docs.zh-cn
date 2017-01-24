---
title: "IRowsetInfoImpl 类 | Microsoft Docs"
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
  - "ATL.IRowsetInfoImpl"
  - "IRowsetInfoImpl"
  - "ATL::IRowsetInfoImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IRowsetInfoImpl 类"
ms.assetid: 9c654155-7727-464e-bd31-143e68391a47
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IRowsetInfoImpl 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供了 [IRowsetInfo](https://msdn.microsoft.com/en-us/library/ms724541.aspx) 接口的实现。  
  
## 语法  
  
```  
template <class T, class PropClass = T>  
class ATL_NO_VTABLE IRowsetInfoImpl :   
   public IRowsetInfo,    
   public CUtlProps<PropClass>  
```  
  
#### 参数  
 `T`  
 类是从`IRowsetInfoImpl` 中派生的。  
  
 `PropClass`  
 该用户可定义的属性类默认为 `T`。  
  
## 成员  
  
### 接口方法  
  
|||  
|-|-|  
|[获得属性](../../data/oledb/irowsetinfoimpl-getproperties.md)|返回行集合支持的所有属性的当前设置。|  
|[GetReferencedRowset](../../data/oledb/irowsetinfoimpl-getreferencedrowset.md)|返回指向对其应用书签或章节的行集合的接口指针。|  
|[GetSpecification](../../data/oledb/irowsetinfoimpl-getspecification.md)|返回对象（命令或会话）上用于创建此行集合的接口指针。|  
  
## 备注  
 对行集合所必须的接口。  实现该命令类使用 [属性集映射](../../data/oledb/begin-propset-map.md)定义的行集合属性。  虽然使用命令行集合类将类的属性设置为，行集的供应与其运行时属性自己的复制，由命令，则会话或对象时创建。  
  
## 要求  
 **头文件：**altdb.h  
  
## 请参阅  
 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)