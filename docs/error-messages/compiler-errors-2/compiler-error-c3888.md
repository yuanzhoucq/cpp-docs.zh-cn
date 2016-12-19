---
title: "编译器错误 C3888 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3888"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3888"
ms.assetid: 40820812-79c5-4dcd-a19d-b4164d25fc8a
caps.latest.revision: 3
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3888
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“name”：C\+\+\/CLI 不支持与此 literal 数据成员关联的常量表达式  
  
 使用 [literal](../../windows/literal-cpp-component-extensions.md) 关键字声明的*名称*数据成员是使用编译器不支持的值初始化的。 编译器仅支持常量整型、枚举或字符串类型。**C3888** 错误可能的原因是数据成员是使用字节数组初始化的。  
  
### 更正此错误  
  
1.  检查声明的 literal 数据成员是否是支持的类型。  
  
## 请参阅  
 [文本](../../windows/literal-cpp-component-extensions.md)