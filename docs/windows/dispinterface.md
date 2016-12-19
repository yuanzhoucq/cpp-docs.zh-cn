---
title: "dispinterface | Microsoft Docs"
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
  - "vc-attr.dispinterface"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "dispinterface 特性"
ms.assetid: 61c5a4a1-ae92-47e9-8ee4-f847be90172b
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# dispinterface
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

将一个接口作为调度接口置于 .idl 文件中。  
  
## 语法  
  
```  
  
[dispinterface]  
  
```  
  
## 备注  
 当 **dispinterface** C\+\+ 属性优先于接口时，会导致将接口置于生成的 .idl 文件中的 library 块中。  
  
 除非指定基类，否则调度接口派生自 `IDispatch`。 必须为调度接口的成员指定 [id](../windows/id.md)。  
  
 MIDL 文档中的 [dispinterface](http://msdn.microsoft.com/library/windows/desktop/aa366802) 用法示例：  
  
```  
dispinterface helloPro   
   { interface hello; };   
```  
  
 对于 **dispinterface** 属性无效。  
  
## 示例  
 有关如何使用 **dispinterface** 的示例，请参阅 [bindable](../windows/bindable.md) 示例。  
  
## 要求  
  
### 特性上下文  
  
|||  
|-|-|  
|**适用对象**|`interface`|  
|**可重复**|No|  
|**必需的特性**|无|  
|**无效的特性**|**dual**、**object**、**oleautomation**、`local`、**ms\_union**|  
  
 有关详细信息，请参见[特性上下文](../windows/attribute-contexts.md)。  
  
## 请参阅  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Attributes by Usage](../windows/attributes-by-usage.md)   
 [uuid](../windows/uuid-cpp-attributes.md)   
 [dual](../windows/dual.md)   
 [custom](../windows/custom-cpp.md)   
 [object](../windows/object-cpp.md)   
 [\_\_interface](../cpp/interface.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-cn/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)