---
title: "operator== (&lt;sample container&gt;) | Microsoft Docs"
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
  - "std.=="
  - "std::=="
  - "operator=="
  - "std.operator=="
  - "std::operator=="
  - "=="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "== 运算符, 具有特定的标准 C++ 对象"
  - "运算符 ==, 容器"
  - "operator==, 容器"
ms.assetid: d3d8754e-5157-4b8b-bf9c-da41856f5eed
caps.latest.revision: 9
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# operator== (&lt;sample container&gt;)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  本主题介绍 Visual C\+\+ 文档作为使用标准 C\+\+ 库的容器的非运行的示例。  有关更多信息，请参见 [STL 容器](../standard-library/stl-containers.md)。  
  
 重载模板比较两个对象的 `operator==` 类。[容器 \(O\)](../standard-library/sample-container-class.md)  
  
## 语法  
  
```  
  
   template<class Ty>  
bool operator==(  
   const Container <Ty>& _Left,  
   const Container <Ty>& _Right  
);  
```  
  
## 返回值  
 返回 `_Left`\#\#\#.`_Right`[范围](../standard-library/container-class-size.md) **\=\= .size  equal &&** \(\_Left \#\#\#. [开始](../standard-library/container-class-begin.md)，`_Left`。  [结束时间](../standard-library/container-class-end.md)*，\_Right***.begin**\)。  
  
## 请参阅  
 [\<sample container\>](../standard-library/sample-container.md)