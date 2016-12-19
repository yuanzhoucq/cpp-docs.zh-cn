---
title: "synchronize | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.synchronize"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "synchronize attribute"
ms.assetid: 15fc8544-955d-4765-b3d5-0f619c8b3f40
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# synchronize
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

同步到目标方法。  
  
## 语法  
  
```  
  
[synchronize]  
  
```  
  
## 备注  
 **同步** C\+\+ 属性实现为同步对象的目标方法支持。  同步允许多个对象通过控制目标方法的访问使用公共资源 \(例如类的方法\)。  
  
 此特性插入的代码在目标方法开始时调用适当的 `Lock` 方法 \(取决于线程模型\)。  当方法退出时， `Unlock` 自动调用。  有关这些功能的更多信息，请参见 [CComAutoThreadModule:: 锁定](../Topic/CComAutoThreadModule::Lock.md)  
  
 此特性要求 [coclass](../windows/coclass.md)、 [progid](../windows/progid.md)或 [vi\_progid](../windows/vi-progid.md) 属性 \(或表示这些中为\) 的其他特性也适用于同一元素。  如果使用任何单一属性，自动应用其他两个。  例如，因此，如果 **progid** 是应用的，也适用 **vi\_progid** 和 **coclass** 。  
  
## 示例  
 下面的代码为 `CMyClass` 对象的 `UpdateBalance` 方法提供同步。  
  
```  
// cpp_attr_ref_synchronize.cpp  
// compile with: /LD  
#define _ATL_ATTRIBUTES  
#include "atlbase.h"  
#include "atlcom.h"  
  
[module(name="SYNC")];  
  
[coclass,  
 threading(both),  
 vi_progid("MyProject.MyClass"),  
 progid("MyProject.MyClass.1"),  
 uuid("7a7baa0d-59b8-4576-b754-79d07e1d1cc3")  
]  
class CMyClass {  
   float m_nBalance;  
  
   [synchronize]  
   void UpdateBalance(float nAdjust) {  
      m_nBalance += nAdjust;  
   }  
};  
```  
  
## 要求  
  
### 属性上下文  
  
|||  
|-|-|  
|**适用对象**|类方法，方法|  
|**可重复**|否|  
|**必需的特性**|一个或多个以下各项: **coclass**、 **progid**或 **vi\_progid**。|  
|**无效的特性**|无|  
  
 有关属性上下文的更多信息，请参见 [属性上下文](../windows/attribute-contexts.md)。  
  
## 请参阅  
 [COM Attributes](../windows/com-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-cn/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)