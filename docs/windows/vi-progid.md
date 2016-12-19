---
title: "vi_progid | Microsoft Docs"
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
  - "vc-attr.vi_progid"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "vi_progid attribute"
ms.assetid: a52449be-b93e-4111-b883-44bb8da53261
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# vi_progid
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定 ProgID 的一个版本中立性窗体。  
  
## 语法  
  
```  
  
      [ vi_progid(  
   name  
) ];  
```  
  
#### 参数  
 *name*  
 表示对象的版本中立性 ProgID。  
  
 Progid 存在 \(CLSID\) 中使用的一个可读的版本类标识符标识 COM\/ActiveX 对象。  
  
## 备注  
 **vi\_progid** C\+\+ 特性可以为 COM 对象指定一版本中立性 ProgID。  ProgID 具有以下形式 *name1.name2.version*。  一版本中立性 ProgID 没有一个 *版本*。  指定 **progid** 和 **vi\_progid** 属性在 coclass 是可能的。  如果未指定 **vi\_progid**，版本中立性 ProgID 是 [progid](../windows/progid.md) 属性指定的值。  
  
 **vi\_progid** 提示 **coclass** 属性，即，因此，如果指定 **vi\_progid**，它是内容并指定 **coclass** 和 **vi\_progid** 属性相同。  
  
 **vi\_progid** 特性使类自动注册以指定的名称。  生成的 .idl 文件不会显示 ProgID 值。  
  
 在 ATL 项目，因此，如果 [coclass](../windows/coclass.md) 属性存在， **GetVersionIndependentProgID** 函数使用指定的 ProgID \(插入 **coclass** 属性\)。  
  
## 示例  
 请参见 [coclass](../windows/coclass.md) 示例为 **vi\_progid**的示例使用。  
  
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
 [Typedef, Enum, Union, and Struct Attributes](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Class Attributes](../windows/class-attributes.md)   
 [ProgID Key](http://msdn.microsoft.com/library/windows/desktop/dd542719)   
 [Attributes Samples](http://msdn.microsoft.com/zh-cn/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)