---
title: "operator&gt; (&lt;sample container&gt;) | Microsoft Docs"
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
  - "std::operator>"
  - "std.>"
  - "std.operator>"
  - "operator>"
  - "std::>"
  - ">"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "> 运算符, 比较特定对象"
  - "运算符 >"
ms.assetid: 49bd417a-3305-4ffa-9884-39d3904ed87d
caps.latest.revision: 9
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# operator&gt; (&lt;sample container&gt;)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  本主题介绍 Visual C\+\+ 文档作为使用标准 C\+\+ 库的容器的非运行的示例。  有关更多信息，请参见 [STL 容器](../standard-library/stl-containers.md)。  
  
 重载模板比较两个对象的 **运算符\>** 类。[容器 \(O\)](../standard-library/sample-container-class.md)  
  
## 语法  
  
```  
  
   template<class Ty>  
bool operator*gt;(  
   const Container <Ty>& _Left,  
   const Container <Ty>& _Right  
);  
```  
  
## 返回值  
 返回\_Right \< \_Left。  
  
## 请参阅  
 [\<sample container\>](../standard-library/sample-container.md)