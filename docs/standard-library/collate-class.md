---
title: "collate 类 | Microsoft Docs"
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
  - "std::collate"
  - "locale/std::collate"
  - "std.collate"
  - "collate"
  - "Collate"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "collate 类"
ms.assetid: 92168798-9628-4a2e-be6e-fa62dcd4d6a6
caps.latest.revision: 18
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# collate 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

一种模板类，用于描述一个对象来充当区域设置 facet，以控制字符串中字符的排序和分组、这些字符之间的比较以及字符串的哈希处理。  
  
## 语法  
  
```  
template <class CharType >  
   class collate : public locale::facet;  
```  
  
#### 参数  
 `CharType`  
 在程序中用于对字符进行编码的类型。  
  
## 备注  
 对于任何区域设置 facet，静态对象 ID 的初始存储值为零。  首次尝试访问其存储值后，将在 **id** 中存储唯一正值。在某些语言中，多个字符作为单个字符分组和处理，在其他语言中，单个字符被作为两个字符进行处理。  通过排序规则类提供的排序规则服务，可以在这些情况下进行排序。  
  
### 构造函数  
  
|||  
|-|-|  
|[collate](../Topic/collate::collate.md)|用作区域设置 facet 以处理字符串排序转换的 `collate` 类的对象的构造函数。|  
  
### Typedef  
  
|||  
|-|-|  
|[char\_type](../Topic/collate::char_type.md)|一种类型，此类型描述 `CharType` 类型字符。|  
|[string\_type](../Topic/collate::string_type.md)|一种类型，此类型描述包含 `CharType` 类型字符的 `basic_string` 类型字符串。|  
  
### 成员函数  
  
|||  
|-|-|  
|[compare](../Topic/collate::compare.md)|根据两个字符序列的特定于 facet 的规则，比较这两个字符序列是否相等。|  
|[do\_compare](../Topic/collate::do_compare.md)|一种虚拟函数，通过调用此函数可根据两个字符序列的特定于 facet 的规则来比较这两个序列是否相等。|  
|[do\_hash](../Topic/collate::do_hash.md)|一种虚拟函数，通过调用此函数可根据序列的特定于 facet 的规则来确定它们的哈希值。|  
|[do\_transform](../Topic/collate::do_transform.md)|一种虚拟函数，通过调用此函数可将字符序列从区域设置转换为字符串，可使用此字符串与以类似方式从同一区域设置转换的其他字符序列按字典顺序进行比较。|  
|[hash](../Topic/collate::hash.md)|根据序列的特定于 facet 的规则来确定它们的哈希值。|  
|[transform](../Topic/collate::transform.md)|将字符序列从区域设置转换为字符串，可使用此字符串与以类似方式从同一区域设置转换的其他字符序列按字典顺序进行比较。|  
  
## 要求  
 **标头：**\<locale\>  
  
 **命名空间:**  std  
  
## 请参阅  
 [\<locale\>](../standard-library/locale.md)   
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)