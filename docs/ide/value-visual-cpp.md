---
title: "&lt;value&gt; (Visual C++) | Microsoft Docs"
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
  - "value"
  - "<value>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<value> C++ XML 标记"
  - "value C++ XML 标记"
ms.assetid: 0ba0a0d5-bcd7-4862-a169-83f2721ad80e
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# &lt;value&gt; (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

\<value\> 标记可以描述属性和属性访问器方法。  请注意，在添加具有一个代码向导的属性在 Visual Studio 集成开发环境 \(ide\)，它将添加新的属性的 [\<summary\>](../ide/summary-visual-cpp.md) 标记。  然后，应该手动添加 \<value\> 标记以描述该属性所表示的值。  
  
## 语法  
  
```  
<value>property-description</value>  
```  
  
#### 参数  
 `property-description`  
 属性的说明。  
  
## 备注  
 使用 [\/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) 进行编译可以将文档注释处理到文件中。  
  
## 示例  
  
```  
// xml_value_tag.cpp  
// compile with: /LD /clr /doc  
// post-build command: xdcmake xml_value_tag.dll  
using namespace System;  
/// Text for class Employee.  
public ref class Employee {  
private:  
   String ^ name;  
   /// <value>Name accesses the value of the name data member</value>  
public:  
   property String ^ Name {  
      String ^ get() {  
         return name;   
      }  
      void set(String ^ i) {  
         name = i;  
      }  
   }  
};  
```  
  
## 请参阅  
 [XML 文档](../ide/xml-documentation-visual-cpp.md)