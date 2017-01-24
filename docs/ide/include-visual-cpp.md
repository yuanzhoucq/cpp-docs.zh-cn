---
title: "&lt;include&gt; (Visual C++) | Microsoft Docs"
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
  - "include"
  - "<include>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<include> C++ XML 标记"
  - "include C++ XML 标记"
ms.assetid: 392a3e61-0371-4617-8362-446650876ce3
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# &lt;include&gt; (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

\<include\> 标记使您得以引用描述源代码中类型和成员的另一文件中的注释。  这是除了将文档注释直接置于源代码文件中之外的另一种可选方法。  例如，可以使用 \<include\> 到使用在团队或公司中的插入标准“的”注释。  
  
## 语法  
  
```  
<include file='filename' path='tagpath' />  
```  
  
#### 参数  
 `filename`  
 包含文档的文件名。  该文件名可用路径加以限定。  名称括在单引号或双引号。  如果它没有找到 `filename`，编译器会发出警告。  
  
 `tagpath`  
 选择所需的节点集文件中包含的有效的 XPath 表达式。  
  
 `name`  
 注释前边的标记中的名称说明符；`name` 具有一个 `id`。  
  
 `id`  
 位于注释之前的标记的 ID。  名称括在单引号或双引号。  
  
## 备注  
 \<include\> 标记使用 XML XPath 语法。  使用 \<include\>，引用方法的 XPath 文档自定义。  
  
 使用 [\/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) 进行编译可以将文档注释处理到文件中。  
  
## 示例  
 以下是一个多文件示例。  第一个文件，使用 \<include\>，包含以下文档注释：  
  
```  
// xml_include_tag.cpp  
// compile with: /clr /doc /LD  
// post-build command: xdcmake xml_include_tag.dll  
  
/// <include file='xml_include_tag.doc' path='MyDocs/MyMembers[@name="test"]/*' />  
public ref class Test {  
   void TestMethod() {  
   }  
};  
  
/// <include file='xml_include_tag.doc' path='MyDocs/MyMembers[@name="test2"]/*' />  
public ref class Test2 {  
   void Test() {  
   }  
};  
```  
  
 第二个文件 xml\_include\_tag.doc 包含下列文档注释：  
  
```  
<MyDocs>  
  
<MyMembers name="test">  
<summary>  
The summary for this type.  
</summary>  
</MyMembers>  
  
<MyMembers name="test2">  
<summary>  
The summary for this other type.  
</summary>  
</MyMembers>  
  
</MyDocs>  
```  
  
## 程序输出  
  
```  
<?xml version="1.0"?>  
<doc>  
    <assembly>  
        <name>t2</name>  
    </assembly>  
    <members>  
        <member name="T:Test">  
            <summary>  
The summary for this type.  
</summary>  
        </member>  
        <member name="T:Test2">  
            <summary>  
The summary for this other type.  
</summary>  
        </member>  
    </members>  
</doc>  
```  
  
## 请参阅  
 [XML 文档](../ide/xml-documentation-visual-cpp.md)