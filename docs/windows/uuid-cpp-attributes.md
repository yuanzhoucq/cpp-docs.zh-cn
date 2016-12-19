---
title: "uuid (C++ Attributes) | Microsoft Docs"
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
  - "vc-attr.uuid"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "uuid attribute"
ms.assetid: 90562a94-5e28-451b-a4b0-cadda7f66efe
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# uuid (C++ Attributes)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

为类或接口指定唯一 ID。  
  
## 语法  
  
```  
  
      [ uuid(  
   "uuid"  
) ]  
```  
  
#### 参数  
 *uuid*  
 128 位，唯一标识符。  
  
## 备注  
 如果接口的定义或类不指定 `uuid` C\+\+ 特性，则 Visual C\+\+ 编译器将提供一。  当指定 `uuid`时，必须包含引号。  
  
 如果未指定 `uuid`，则编译器在计算机上生成接口或类相同的 GUID 具有相同名称具有不同特性的项目。  
  
 可以使用 Uuidgen.exe 或 Guidgen.exe 生成拥有唯一 ID。  \(运行这些工具、在菜单中单击 **开始** 然后单击 **运行** 之一。  然后输入所需的工具的名称。\)  
  
 当在不使用 ATL 项目，指定 `uuid` 属性是否与指定 [uuid](../cpp/uuid-cpp.md) \_\_declspec 修饰符。  若要检索类的 `uuid` ，可以使用 [\_\_uuidof](../cpp/uuidof-operator.md)  
  
## 示例  
 请参见 [可绑定](../windows/bindable.md) 示例为 `uuid`的示例使用。  
  
## 要求  
  
### 属性上下文  
  
|||  
|-|-|  
|**适用对象**|**类**， `struct`， `interface`， **联合**， `enum`|  
|**可重复**|否|  
|**必需的特性**|无|  
|**无效的特性**|无|  
  
 有关属性上下文的更多信息，请参见 [属性上下文](../windows/attribute-contexts.md)。  
  
## 请参阅  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Interface Attributes](../windows/interface-attributes.md)   
 [Class Attributes](../windows/class-attributes.md)   
 [Typedef, Enum, Union, and Struct Attributes](../windows/typedef-enum-union-and-struct-attributes.md)   
 [uuid](http://msdn.microsoft.com/library/windows/desktop/aa367302)   
 [Attributes Samples](http://msdn.microsoft.com/zh-cn/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)