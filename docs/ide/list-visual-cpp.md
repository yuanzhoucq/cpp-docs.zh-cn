---
title: "&lt;list&gt; (Visual C++) | Microsoft Docs"
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
  - "list"
  - "<list>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<list> C++ XML 标记"
  - "list C++ XML 标记"
ms.assetid: c792a10b-0451-422c-9aa0-604116e69d64
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# &lt;list&gt; (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

\<listheader\> 块用于定义表或定义列表中的标题行。  定义表时，只需为标题中的项提供一个项。  
  
## 语法  
  
```  
<list type="bullet" | "number" | "table">  
   <listheader>  
      <term>term</term>  
      <description>description</description>  
   </listheader>  
   <item>  
      <term>term</term>  
      <description>description</description>  
   </item>  
</list>  
```  
  
#### 参数  
 `term`  
 要定义的项，该项将在 `description` 中定义。  
  
 `description`  
 项目符号列表或编号列表中的项或者 `term` 的定义。  
  
## 备注  
 列表中的每一项都用一个 \<item\> 块来描述。  创建定义列表时，既需要指定 `term` 也需要指定 `description`。  但是，对于表、项目符号列表或编号列表，只需为 `description` 提供一个项。  
  
 列表或表所拥有的 \<item\> 块数可以根据需要而定。  
  
 使用 [\/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) 进行编译可以将文档注释处理到文件中。  
  
## 示例  
  
```  
// xml_list_tag.cpp  
// compile with: /doc /LD  
// post-build command: xdcmake xml_list_tag.dll  
/// <remarks>Here is an example of a bulleted list:  
/// <list type="bullet">  
/// <item>  
/// <description>Item 1.</description>  
/// </item>  
/// <item>  
/// <description>Item 2.</description>  
/// </item>  
/// </list>  
/// </remarks>  
class MyClass {};  
```  
  
## 请参阅  
 [XML 文档](../ide/xml-documentation-visual-cpp.md)