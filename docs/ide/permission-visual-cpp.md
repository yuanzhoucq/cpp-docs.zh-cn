---
title: "&lt;permission&gt; (Visual C++) | Microsoft Docs"
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
  - "permission"
  - "<permission>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<permission> C++ XML 标记"
  - "permission C++ XML 标记"
ms.assetid: 537ee2bc-95bd-48e4-9ce6-3420c3da87f4
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# &lt;permission&gt; (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

\<permission\> 标记使您得以将成员的访问记入文档。  <xref:System.Security.PermissionSet> 允许您指定访问成员。  
  
## 语法  
  
```  
<permission cref="member">description</permission>  
```  
  
#### 参数  
 `member`  
 对可以通过当前编译环境进行调用的成员或字段的引用。  编译器检查给定的代码元素是否存在，并将 `member` 转换为输出 XML 中的规范化元素名称。  名称括在单引号或双引号。  
  
 如果它没有找到 `member`，编译器会发出警告。  
  
 有关如何创建对泛型类型的 cref 引用的信息，请参见 [\<see\>](../ide/see-visual-cpp.md)。  
  
 `description`  
 对成员的访问的说明。  
  
## 备注  
 使用 [\/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) 进行编译可以将文档注释处理到文件中。  
  
 Visual C\+\+ 编译器在一个处理过程将尝试解决 cref 引用传递文档注释。  因此，因此，如果使用 C\+\+ 查找规则，编译器没有找到符号引用将被标记为未解析。  有关更多信息，请参见[\<seealso\>](../ide/seealso-visual-cpp.md)。  
  
## 示例  
  
```  
// xml_permission_tag.cpp  
// compile with: /clr /doc /LD  
// post-build command: xdcmake xml_permission_tag.dll  
using namespace System;  
/// Text for class TestClass.  
public ref class TestClass {  
   /// <permission cref="System::Security::PermissionSet">Everyone can access this method.</permission>  
   void Test() {}  
};  
```  
  
## 请参阅  
 [XML 文档](../ide/xml-documentation-visual-cpp.md)