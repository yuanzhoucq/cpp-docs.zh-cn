---
title: "progid | Microsoft Docs"
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
  - "vc-attr.progid"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "progid attribute"
ms.assetid: afcf559c-e432-481f-aa9a-bd3bb72c02a8
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# progid
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

为 COM 对象指定 ProgID。  
  
## 语法  
  
```  
  
      [ progid(  
   name  
) ];  
```  
  
#### 参数  
 *name*  
 表示对象的 ProgID。  
  
 Progid 存在 \(CLSID\) 中使用的一个可读的版本类标识符标识 COM\/ActiveX 对象。  
  
## 备注  
 **progid** C\+\+ 特性可以为 COM 对象指定 ProgID。  ProgID 具有以下形式 *name1.name2.version*。  如果不为 ProgID 指定 *版本* 中，默认版本为 1。  如果未指定 *name1.name2*，默认名称为 *classname.classname**。* 如果未指定 **progid** ，并指定 **vi\_progid**， *name1.name2*从 **vi\_progid** 执行，并 \(下一个序号\) 版本追加。  
  
 如果特性块使用 **progid** 也不使用 `uuid`，编译器将检查注册表查看 `uuid` 是否为指定的 **progid**存在。  如果 **progid** 未指定，则此版本 \(和 coclass 名称，因此，如果创建 coclass\) 将用于生成 **progid**。  
  
 **progid** 提示 **coclass** 属性，即，因此，如果指定 **progid**，它是内容并指定 **coclass** 和 **progid** 属性相同。  
  
 **progid** 特性使类自动注册以指定的名称。  生成的 .idl 文件不会显示 **progid** 值。  
  
 当此属性在使用 ATL 项目中时，属性的行为更改。  除了上面的行为以外，信息指定与此特性用于 **GetProgID** 功能，插入已 **coclass** 属性。  有关更多信息，请参见 [coclass](../windows/coclass.md) 属性。  
  
## 示例  
 为 [coclass](../windows/coclass.md) 参见示例为 **progid**的示例使用。  
  
## 要求  
  
### 属性上下文  
  
|||  
|-|-|  
|**适用对象**|**类**， `struct`|  
|**可重复**|否|  
|**必需的特性**|无|  
|**无效的特性**|无|  
  
 有关属性上下文的更多信息，请参见 [属性上下文](../windows/attribute-contexts.md)。  
  
## 请参阅  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Class Attributes](../windows/class-attributes.md)   
 [Typedef, Enum, Union, and Struct Attributes](../windows/typedef-enum-union-and-struct-attributes.md)   
 [ProgID Key](http://msdn.microsoft.com/library/windows/desktop/dd542719)   
 [Attributes Samples](http://msdn.microsoft.com/zh-cn/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)