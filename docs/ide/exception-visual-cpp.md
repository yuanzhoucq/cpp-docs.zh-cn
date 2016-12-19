---
title: "&lt;exception&gt; (Visual C++) | Microsoft Docs"
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
  - "exception"
  - "<exception>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<exception> C++ XML 标记"
  - "exception C++ XML 标记"
ms.assetid: 24451e79-9b89-4b77-98fb-702c6516b818
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# &lt;exception&gt; (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

\<exception\> 标记使您可以指定哪些异常可被引发。  该标记应用于方法定义。  
  
## 语法  
  
```  
<exception cref="member">description</exception>  
```  
  
#### 参数  
 `member`  
 对可从当前编译环境中获取的异常的引用。  使用名称查找规则，编译器将检查特定异常存在，并将 `member` 对输出 XML 的规范元素名称。  如果它没有找到 `member`，编译器会发出警告。  
  
 名称括在单引号或双引号。  
  
 有关如何创建对泛型类型的 cref 引用的信息，请参见 [\<see\>](../ide/see-visual-cpp.md)。  
  
 `description`  
 说明。  
  
## 备注  
 使用 [\/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) 进行编译可以将文档注释处理到文件中。  
  
 Visual C\+\+ 编译器在一个处理过程将尝试解决 cref 引用传递文档注释。  因此，因此，如果使用 C\+\+ 查找规则，编译器没有找到符号引用将被标记为未解析。  有关更多信息，请参见[\<seealso\>](../ide/seealso-visual-cpp.md)。  
  
## 示例  
  
```  
// xml_exception_tag.cpp  
// compile with: /clr /doc /LD  
// post-build command: xdcmake xml_exception_tag.dll  
using namespace System;  
  
/// Text for class EClass.  
public ref class EClass : public Exception {  
   // class definition ...  
};  
  
/// <exception cref="System.Exception">Thrown when... .</exception>  
public ref class TestClass {  
   void Test() {  
      try {  
      }  
      catch(EClass^) {  
      }  
   }  
};  
```  
  
## 请参阅  
 [XML 文档](../ide/xml-documentation-visual-cpp.md)