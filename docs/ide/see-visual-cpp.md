---
title: "&lt;see&gt; (Visual C++) | Microsoft Docs"
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
  - "<see>"
  - "see"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<see> C++ XML 标记"
  - "see C++ XML 标记"
ms.assetid: 20ef66f4-b278-45cf-8613-63919edf5720
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# &lt;see&gt; (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

\<see\> 标记使您得以从文本内指定链接。  使用 [\<seealso\>](../ide/seealso-visual-cpp.md) 指示文本您可能希望中显示区分请参见。  
  
## 语法  
  
```  
<see cref="member"/>  
```  
  
#### 参数  
 `member`  
 对可以通过当前编译环境进行调用的成员或字段的引用。  名称括在单引号或双引号。  
  
 编译器将检查特定代码元素是否存在并解决 `member` 到输出 XML 元素名称。  如果它没有找到 `member`，编译器会发出警告。  
  
## 备注  
 使用 [\/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) 进行编译可以将文档注释处理到文件中。  
  
 有关使用示例 \<see\>参见 [\<summary\>](../ide/summary-visual-cpp.md)。  
  
 Visual C\+\+ 编译器在一个处理过程将尝试解决 cref 引用传递文档注释。  因此，因此，如果使用 C\+\+ 查找规则，编译器没有找到符号引用将被标记为未解析。  有关更多信息，请参见[\<seealso\>](../ide/seealso-visual-cpp.md)。  
  
## 示例  
 下面的示例演示如何使 cref 对泛型类型，因此，编译器将引用解析。  
  
```  
// xml_see_cref_example.cpp  
// compile with: /LD /clr /doc  
// the following cref shows how to specify the reference, such that,  
// the compiler will resolve the reference  
/// <see cref="C{T}">  
/// </see>  
ref class A {};  
  
// the following cref shows another way to specify the reference,   
// such that, the compiler will resolve the reference  
/// <see cref="C < T >"/>  
  
// the following cref shows how to hard-code the reference  
/// <see cref="T:C`1">  
/// </see>  
ref class B {};  
  
/// <see cref="A">  
/// </see>  
/// <typeparam name="T"></typeparam>  
generic<class T>  
ref class C {};  
```  
  
## 请参阅  
 [XML 文档](../ide/xml-documentation-visual-cpp.md)