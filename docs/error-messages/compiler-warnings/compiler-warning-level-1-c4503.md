---
title: "编译器警告 （等级 1） C4503 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4503
dev_langs:
- C++
helpviewer_keywords:
- C4503
ms.assetid: 7c5a98ae-5b6d-41d8-b881-12d3ffd5e392
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3f69f0c3176d2fbe19e11ce08c071691a72d858d
ms.openlocfilehash: f999fcb73860bfd2fabb3484e78f313a32240dee
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-1-c4503"></a>编译器警告（等级 1）C4503
identifier︰ 修饰名的长度超过了，名称被截断  
  
 修饰的名的长度超出编译器限制 (4096)，且已被截断。 若要避免此警告和截断，减少参数的数目或使用标识符的名称长度。  
  
 一种情况会发出此警告时您的代码包含模板上专用化模板重复。  例如，映射 （从 c + + 标准库） 的映射。  在这种情况下，可以增强您的 typedef 设置包含该映射的类型 （例如，结构）。  
  
 但是，您可能会决定不重构你的代码。  可以提供的应用程序生成 C4503，但如果在截断符号链接时错误，它将会更加难以确定的错误中的符号的类型。  调试将也会更加困难;调试器还将有难度就越大映射的符号名称，键入名称。  正确的程序，但是，不受截断的名称。  
  
 下面的示例生成 C4503:  
  
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
  
 下面的示例演示一种重写代码以解决 c4503 的方法︰  
  
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
