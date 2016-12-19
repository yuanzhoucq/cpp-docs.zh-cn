---
title: "threading (C++) | Microsoft Docs"
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
  - "vc-attr.threading"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "threading attribute"
ms.assetid: 9b558cd6-fbf0-4602-aed5-31c068550ce3
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# threading (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

为 COM 对象指定线程模型。  
  
## 语法  
  
```  
  
      [ threading(  
   model=enumeration  
) ]  
```  
  
#### 参数  
 ***设计*** \(可选\)  
 下面的线程处理模型之一:  
  
-   **单元** \(单元线程\)  
  
-   **非** \(.NET 没有用户界面的框架元素\)  
  
-   **单个** \(简单的线程\)  
  
-   **免** \(自由线程处理\)  
  
-   **两个** \(单元和自由线程处理\)  
  
 默认值为 **单元**。  
  
## 备注  
 **线程处理** C\+\+ 属性不会显示在生成的 .idl 文件，但是 COM 对象的实现。  
  
 在 ATL 项目，因此，如果 [coclass](../windows/coclass.md) 属性存在， *设计* 指定的线程处理模型将作为模板参数传递到 [CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md) 类，插入 **coclass** 属性。  
  
 **线程处理** 属性来控制对 [event\_source](../windows/event-source.md)的访问。  
  
## 示例  
 请参见 [允许](../windows/licensed.md) 示例为 **线程处理**的示例使用。  
  
## 要求  
  
### 属性上下文  
  
|||  
|-|-|  
|**适用对象**|**类**， `struct`|  
|**可重复**|否|  
|**必需的特性**|**coclass**|  
|**无效的特性**|无|  
  
 有关属性上下文的更多信息，请参见 [属性上下文](../windows/attribute-contexts.md)。  
  
## 请参阅  
 [COM Attributes](../windows/com-attributes.md)   
 [Typedef, Enum, Union, and Struct Attributes](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Class Attributes](../windows/class-attributes.md)   
 [针对旧代码的多线程支持 \(Visual C\+\+\)](../parallel/multithreading-support-for-older-code-visual-cpp.md)   
 [Neutral Apartments](http://msdn.microsoft.com/library/windows/desktop/ms681813)   
 [Attributes Samples](http://msdn.microsoft.com/zh-cn/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)