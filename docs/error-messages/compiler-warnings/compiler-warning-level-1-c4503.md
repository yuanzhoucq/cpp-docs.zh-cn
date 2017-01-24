---
title: "编译器警告（等级 1）C4503 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4503"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4503"
ms.assetid: 7c5a98ae-5b6d-41d8-b881-12d3ffd5e392
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4503
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“identifier”: 修饰名的长度超出限制，名称被截断  
  
 修饰名的长度超出编译器限制 \(4096\)，被截断了。  若要避免出现此警告和截断，请减少所使用的参数数目或标识符的名称长度。  
  
 发出此警告的一种情况是当代码重复包含专用于模板的模板时。例如，映射的映射（来自标准 C\+\+ 库）。在这种情况下，可以将您的 typedef 设置为一个包含映射的类型（例如，结构）。  
  
 不过，您可能决定不重构自己的代码。可以发布生成 C4503 的应用程序，但如果收到关于截断符号的链接时错误，确定错误中符号的类型将更加困难。调试也将更加困难；调试器将符号名称映射到类型名称也会有困难。但是，程序的正确性不受截断名称的影响。  
  
 下面的示例生成 C4503：  
  
```  
// C4503.cpp  
// compile with: /W1 /EHsc /c  
// C4503 expected  
#include <string>  
#include <map>  
  
class Field{};  
  
typedef std::map<std::string, Field> Screen;  
typedef std::map<std::string, Screen> WebApp;  
typedef std::map<std::string, WebApp> WebAppTest;  
typedef std::map<std::string, WebAppTest> Hello;  
Hello MyWAT;  
```  
  
 下面的示例显示了一种通过重写代码来解决 C4503 的方法：  
  
```  
// C4503b.cpp  
// compile with: /W1 /EHsc /c  
#include <string>  
#include <map>  
  
class Field{};  
struct Screen2 {  
   std::map<std::string, Field> Element;  
};  
  
struct WebApp2 {  
   std::map<std::string, Screen2> Element;  
};  
  
struct WebAppTest2 {  
   std::map<std::string, WebApp2> Element;  
};  
  
struct Hello2 {  
   std::map<std::string, WebAppTest2> Element;  
};  
  
Hello2 MyWAT2;  
```