---
title: "&lt;seealso&gt; (Visual C++) | Microsoft Docs"
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
  - "<seealso>"
  - "seealso"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<seealso> C++ XML 标记"
  - "seealso C++ XML 标记"
ms.assetid: cb33d100-9c50-4485-8d0c-573429eff155
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# &lt;seealso&gt; (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

\<seealso\> 标记使您得以指定希望在“请参见”一节中出现的文本。  使用 [\<see\>](../ide/see-visual-cpp.md) 从文本内指定链接。  
  
## 语法  
  
```  
<seealso cref="member"/>  
```  
  
#### 参数  
 `member`  
 对可以通过当前编译环境进行调用的成员或字段的引用。  名称括在单引号或双引号。  
  
 编译器将检查特定代码元素是否存在并解决 `member` 到输出 XML 元素名称。  如果它没有找到 `member`，编译器会发出警告。  
  
 有关如何创建对泛型类型的 cref 引用的信息，请参见 [\<see\>](../ide/see-visual-cpp.md)。  
  
## 备注  
 使用 [\/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) 进行编译可以将文档注释处理到文件中。  
  
 有关使用示例 \<seealso\>参见 [\<summary\>](../ide/summary-visual-cpp.md) 。  
  
 Visual C\+\+ 编译器在一个处理过程将尝试解决 cref 引用传递文档注释。  因此，因此，如果使用 C\+\+ 查找规则，编译器没有找到符号引用将被标记为未解析。  
  
## 示例  
 在下面的示例中，未解析的符号在 cref 引用。  cref 的 XML 注释到 B::Test 将是 `<seealso cref="!:B::Test" />`，，而对 A::Test 的引用是格式良好的 `<seealso cref="M:A.Test" />`。  
  
```  
// xml_seealso_tag.cpp  
// compile with: /LD /clr /doc  
// post-build command: xdcmake xml_seealso_tag.dll  
  
/// Text for class A.  
public ref struct A {  
   /// <summary><seealso cref="A::Test"/>  
   /// <seealso cref="B::Test"/>  
   /// </summary>  
   void MyMethod(int Int1) {}  
  
   /// text  
   void Test() {}  
};  
  
/// Text for class B.  
public ref struct B {  
   void Test() {}  
};  
```  
  
## 请参阅  
 [XML 文档](../ide/xml-documentation-visual-cpp.md)