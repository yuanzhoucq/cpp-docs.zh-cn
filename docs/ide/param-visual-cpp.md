---
title: "&lt;param&gt; (Visual C++) | Microsoft Docs"
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
  - "param"
  - "<param>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<param> C++ XML 标记"
  - "param C++ XML 标记"
ms.assetid: 66c1a1c3-4f98-4bcf-8c7d-9a40308982fb
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# &lt;param&gt; (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

\<param\> 标记应当用于方法声明的注释中，以描述方法的一个参数。  
  
## 语法  
  
```  
<param name='name'>description</param>  
```  
  
#### 参数  
 `name`  
 方法参数名。  名称括在单引号或双引号。  如果它没有找到 `name`，编译器会发出警告。  
  
 `description`  
 参数说明。  
  
## 备注  
 \<param\> 标记的文本将显示在 IntelliSense，[对象浏览器](http://msdn.microsoft.com/zh-cn/f89acfc5-1152-413d-9f56-3dc16e3f0470)以及代码注释 Web 报告。  
  
 使用 [\/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) 进行编译可以将文档注释处理到文件中。  
  
## 示例  
  
```  
// xml_param_tag.cpp  
// compile with: /clr /doc /LD  
// post-build command: xdcmake xml_param_tag.dll  
/// Text for class MyClass.  
public ref class MyClass {  
   /// <param name="Int1">Used to indicate status.</param>  
   void MyMethod(int Int1) {  
   }  
};  
```  
  
## 请参阅  
 [XML 文档](../ide/xml-documentation-visual-cpp.md)