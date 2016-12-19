---
title: "&lt;paramref&gt; (Visual C++) | Microsoft Docs"
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
  - "paramref"
  - "<paramref>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<paramref> C++ XML 标记"
  - "paramref C++ XML 标记"
ms.assetid: c5730dc2-7159-421f-b2d5-bb971e307122
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# &lt;paramref&gt; (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

\<paramref\> 标记为您提供了一种指示单词是参数。  .xml 文件可以处理设置此参数以某种不同的方法。  
  
## 语法  
  
```  
<paramref name="name"/>  
```  
  
#### 参数  
 `name`  
 要引用的参数名。  名称括在单引号或双引号。  如果它没有找到 `name`，编译器会发出警告。  
  
## 备注  
 使用 [\/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) 进行编译可以将文档注释处理到文件中。  
  
## 示例  
  
```  
// xml_paramref_tag.cpp  
// compile with: /clr /doc /LD  
// post-build command: xdcmake xml_paramref_tag.dll  
/// Text for class MyClass.  
public ref class MyClass {  
   /// <summary>MyMethod is a method in the MyClass class.  
   /// The <paramref name="Int1"/> parameter takes a number.  
   /// </summary>  
   void MyMethod(int Int1) {}  
};  
```  
  
## 请参阅  
 [XML 文档](../ide/xml-documentation-visual-cpp.md)