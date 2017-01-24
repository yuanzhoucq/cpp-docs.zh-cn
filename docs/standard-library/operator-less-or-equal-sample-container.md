---
title: "operator&lt;= (&lt;sample container&gt;) | Microsoft Docs"
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
  - "std::<="
  - "std.operator<="
  - "operator<="
  - "std.<="
  - "std::operator<="
  - "<="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<= 运算符"
  - "<= 运算符, 具有特定对象"
  - "运算符 <="
  - "operator<="
ms.assetid: 338577dd-dc88-4a2b-9e12-0379c54fc8a2
caps.latest.revision: 9
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# operator&lt;= (&lt;sample container&gt;)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  本主题介绍 Visual C\+\+ 文档作为使用标准 C\+\+ 库的容器的非运行的示例。  有关更多信息，请参见 [STL 容器](../standard-library/stl-containers.md)。  
  
 重载相比模板类 [容器 \(O\)](../standard-library/sample-container-class.md)两个对象的 **operator\=\<**。  
  
## 语法  
  
```  
  
   template<class Ty>  
bool operator<=(  
   const Container <Ty>& _Left,  
   const Container <Ty>& _Right  
);  
```  
  
## 返回值  
 返回 \#\#\#\!\(\_Right \< \_Left\)。  
  
## 请参阅  
 [\<sample container\>](../standard-library/sample-container.md)