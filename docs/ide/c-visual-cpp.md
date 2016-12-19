---
title: "&lt;c&gt; (Visual C++) | Microsoft Docs"
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
  - "<c>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<c> C++ XML 标记"
  - "c C++ XML 标记"
ms.assetid: 3b23fc0f-e10d-4dd0-b197-48a46cbddd9f
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# &lt;c&gt; (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

\<c\> 标记指示应标记在声明中的文本为代码。  使用 [\<code\>](../ide/code-visual-cpp.md) 将多行指示为代码。  
  
## 语法  
  
```  
<c>text</c>  
```  
  
#### 参数  
 `text`  
 要指示为编码的文本。  
  
## 备注  
 使用 [\/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) 进行编译可以将文档注释处理到文件中。  
  
## 示例  
  
```  
// xml_c_tag.cpp  
// compile with: /doc /LD  
// post-build command: xdcmake xml_c_tag.xdc  
  
/// Text for class MyClass.  
class MyClass {  
public:  
   int m_i;  
   MyClass() : m_i(0) {}  
  
   /// <summary><c>MyMethod</c> is a method in the <c>MyClass</c> class.  
   /// </summary>  
   int MyMethod(MyClass * a) {  
      return a -> m_i;  
   }  
};  
```  
  
## 请参阅  
 [XML 文档](../ide/xml-documentation-visual-cpp.md)