---
title: "&lt;summary&gt; (Visual C++) | Microsoft Docs"
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
  - "<summary>"
  - "summary"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<summary> C++ XML 标记"
  - "summary C++ XML 标记"
ms.assetid: cdeeefbb-1339-45d6-9002-10042a9a2726
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# &lt;summary&gt; (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

\<summary\> 标记应当用于描述类型或类型成员。  使用 [\<remarks\>](../ide/remarks-visual-cpp.md) 添加针对某个类型说明的补充信息。  
  
## 语法  
  
```  
<summary>description</summary>  
```  
  
#### 参数  
 `description`  
 对象的摘要。  
  
## 备注  
 \<summary\> 标记的文本是唯一的信息源有关类型的在 IntelliSense 还显示在 [对象浏览器](http://msdn.microsoft.com/zh-cn/f89acfc5-1152-413d-9f56-3dc16e3f0470) 以及代码注释 Web 报告。  
  
 使用 [\/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) 进行编译可以将文档注释处理到文件中。  
  
## 示例  
  
```  
// xml_summary_tag.cpp  
// compile with: /LD /clr /doc  
// post-build command: xdcmake xml_summary_tag.dll  
  
/// Text for class MyClass.  
public ref class MyClass {  
public:  
   /// <summary>MyMethod is a method in the MyClass class.  
   /// <para>Here's how you could make a second paragraph in a description. <see cref="System::Console::WriteLine"/> for information about output statements.</para>  
   /// <seealso cref="MyClass::MyMethod2"/>  
   /// </summary>  
   void MyMethod(int Int1) {}  
  
   /// text  
   void MyMethod2() {}  
};  
```  
  
## 请参阅  
 [XML 文档](../ide/xml-documentation-visual-cpp.md)