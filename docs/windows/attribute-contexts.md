---
title: "Attribute Contexts | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "attributes [C++], contexts"
ms.assetid: 3086351f-77a8-4048-99e9-3b6b041b9437
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Attribute Contexts
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用四个基本的字段， C\+\+ 特性可以描述:该目标。可以应用到 \(**适用于**\)，因此，如果与其他属性 \(**无效的特性**\) 的它们是可重复的或非 \(**可重复**\)，所需的显示其他属性 \(**必需的特性**\) 和不兼容。  这些字段在每个属性的一个附表中列出参考主题。  上述每个字段下述。  
  
## 适用于  
 此字段描述是指定属性的合法的目标的其他 C\+\+ 语言元素。  例如，因此，如果属性。 **适用于** 字段指定 “类”，则指示特性只能应用于合法的 C\+\+ 类。  如果将特性应用于类的成员函数，语法就会发生错误。  
  
 有关更多信息，请参见 [由用法的属性](../windows/attributes-by-usage.md)。  
  
## 可重复  
 此字段指示属性是否可重复应用于同一目标。  大多数属性不是可重复的。  
  
## 必需的特性  
 此字段列出了需要存在的其他属性 \(即应用于同一目标\) 以便指定的属性正常工作。  具有此字段的所有项属性极为少见。  
  
## 无效的特性  
 此字段列表与指定的属性不兼容的其他属性。  具有此字段的所有项属性极为少见。  
  
## 请参阅  
 [C\+\+ Attributes Reference](../windows/cpp-attributes-reference.md)