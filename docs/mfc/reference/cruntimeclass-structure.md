---
title: "CRuntimeClass Structure | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CRuntimeClass"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CRuntimeClass structure"
  - "dynamic class information"
  - "run-time class, CRuntimeClass structure"
  - "运行时, class information"
ms.assetid: de62b6ef-90d4-420f-8c70-f58b36976a2b
caps.latest.revision: 20
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRuntimeClass Structure
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

从 `CObject` 派生的每选件类与您可以使用获取有关对象的信息或其基类在运行时的 `CRuntimeClass` 结构。  
  
## 语法  
  
```  
struct CRuntimeClass  
```  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CRuntimeClass::CreateObject](../Topic/CRuntimeClass::CreateObject.md)|在运行时，将创建一个对象。|  
|[CRuntimeClass::FromName](../Topic/CRuntimeClass::FromName.md)|使用熟悉的类名，将创建一个对象在运行时。|  
|[CRuntimeClass::IsDerivedFrom](../Topic/CRuntimeClass::IsDerivedFrom.md)|确定选件类是否从指定的选件类派生。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CRuntimeClass::m\_lpszClassName](../Topic/CRuntimeClass::m_lpszClassName.md)|类的名称。|  
|[CRuntimeClass::m\_nObjectSize](../Topic/CRuntimeClass::m_nObjectSize.md)|以字节为单位的对象大小。|  
|[CRuntimeClass::m\_pBaseClass](../Topic/CRuntimeClass::m_pBaseClass.md)|指向基类的 `CRuntimeClass` 结构的指针。|  
|[CRuntimeClass::m\_pfnCreateObject](../Topic/CRuntimeClass::m_pfnCreateObject.md)|对动态创建对象的函数的指针。|  
|[CRuntimeClass::m\_pfnGetBaseClass](../Topic/CRuntimeClass::m_pfnGetBaseClass.md)|返回 `CRuntimeClass` 结构\(仅，在动态链接）。|  
|[CRuntimeClass::m\_wSchema](../Topic/CRuntimeClass::m_wSchema.md)|选件类的模式数字。|  
  
## 备注  
 `CRuntimeClass` 是结构并没有基类。  
  
 能够确定对象的选件类在运行时很有用，当函数参数的额外类型检查在需要时，或者，如果必须根据对象的选件类中编写特殊用途的代码。  运行时选件类信息不是直接由C\+\+语言支持。  
  
 `CRuntimeClass` 在相关C\+\+对象提供信息，例如指向基类和相关选件类的ASCII类名的 `CRuntimeClass`。  此结构实现可用于动态创建对象，指定对象的类型使用一个熟悉的名称并确定的各种功能相关选件类还是从特定选件类派生。  
  
 有关使用 `CRuntimeClass`的更多信息，请参见文章 [访问运行时选件类信息](../../mfc/accessing-run-time-class-information.md)。  
  
## 继承层次结构  
 `CRuntimeClass`  
  
## 要求  
 **Header:** afx.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CObject::GetRuntimeClass](../Topic/CObject::GetRuntimeClass.md)   
 [CObject::IsKindOf](../Topic/CObject::IsKindOf.md)   
 [RUNTIME\_CLASS](../Topic/RUNTIME_CLASS.md)   
 [IMPLEMENT\_DYNAMIC](../Topic/IMPLEMENT_DYNAMIC.md)   
 [IMPLEMENT\_DYNCREATE](../Topic/IMPLEMENT_DYNCREATE.md)   
 [IMPLEMENT\_SERIAL](../Topic/IMPLEMENT_SERIAL.md)