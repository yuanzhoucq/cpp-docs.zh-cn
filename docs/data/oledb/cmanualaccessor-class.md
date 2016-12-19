---
title: "CManualAccessor 类 | Microsoft Docs"
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
  - "ATL::CManualAccessor"
  - "ATL.CManualAccessor"
  - "CManualAccessor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CManualAccessor 类"
ms.assetid: a0088074-7135-465c-b228-69097a50b8cc
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CManualAccessor 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示对高级用途使用的访问器类型。  
  
## 语法  
  
```  
class CManualAccessor : public CAccessorBase  
```  
  
## 成员  
  
### 方法  
  
|||  
|-|-|  
|[AddBindEntry](../../data/oledb/cmanualaccessor-addbindentry.md)|添加输入绑定到输出列。|  
|[AddParameterEntry](../../data/oledb/cmanualaccessor-addparameterentry.md)|将参数输入到参数访问器。|  
|[CreateAccessor](../../data/oledb/cmanualaccessor-createaccessor.md)|分配列绑定结构的内存并初始化列数据成员。|  
|[CreateParameterAccessor](../../data/oledb/cmanualaccessor-createparameteraccessor.md)|分配参数绑定结构的内存并初始化参数数据成员。|  
  
## 备注  
 使用 `CManualAccessor`，您可通过运行时函数调用指定参数和输出列绑定。  
  
## 要求  
 **Header:** atldbcli.h  
  
## 请参阅  
 [DBViewer](../../top/visual-cpp-samples.md)   
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [CAccessor 类](../../data/oledb/caccessor-class.md)   
 [CDynamicAccessor 类](../../data/oledb/cdynamicaccessor-class.md)   
 [CDynamicParameterAccessor 类](../../data/oledb/cdynamicparameteraccessor-class.md)