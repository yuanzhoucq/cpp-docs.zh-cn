---
title: "&lt;returns&gt; (Visual C++) | Microsoft Docs"
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
  - "returns"
  - "<returns>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<returns> C++ XML 标记"
  - "returns C++ XML 标记"
ms.assetid: 5e3b0ed9-838d-4953-a93e-76d2d0a19fb9
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# &lt;returns&gt; (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

\<returns\> 标记应当用于方法声明的注释，以描述返回值。  
  
## 语法  
  
```  
<returns>description</returns>  
```  
  
#### 参数  
 `description`  
 返回值的说明。  
  
## 备注  
 使用 [\/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) 进行编译可以将文档注释处理到文件中。  
  
## 示例  
  
```  
// xml_returns_tag.cpp  
// compile with: /LD /clr /doc  
// post-build command: xdcmake xml_returns_tag.dll  
  
/// Text for class MyClass.  
public ref class MyClass {  
public:  
   /// <returns>Returns zero.</returns>  
   int GetZero() { return 0; }  
};  
```  
  
## 请参阅  
 [XML 文档](../ide/xml-documentation-visual-cpp.md)