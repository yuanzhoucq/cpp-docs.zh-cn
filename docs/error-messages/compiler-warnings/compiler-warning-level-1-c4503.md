---
title: "编译器警告 （等级 1） C4503 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4503
dev_langs: C++
helpviewer_keywords: C4503
ms.assetid: 7c5a98ae-5b6d-41d8-b881-12d3ffd5e392
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b174ac92abb0f095895eb587afcba860f4abbe0d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4503"></a>编译器警告（等级 1）C4503
identifier： 修饰名的长度超出，名称已被截断  
  
 修饰的名的长度超出编译器限制 (4096)，已被截断。 若要避免此警告和截断，减少参数的数目或使用标识符名称长度。  
  
 会发出此警告的一种情况是当你的代码包含模板上专用化模板重复。  例如，映射 （从 c + + 标准库） 的映射。  在此情况下，你可以创建你 typedefs 包含映射的类型 （例如结构）。  
  
 但是，你可能会决定不重构你的代码。  可以提供的应用程序生成 C4503，但如果在上截断符号链接时错误，它将会更加难以确定错误中的符号的类型。  调试将也会更困难;调试器也将具有难度就越大映射要键入名称的符号名称。  正确的程序，但是，不受截断的名称。  
  
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
  
 下面的示例演示一种方法重写你的代码以解决 c4503 的方法：  
  
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