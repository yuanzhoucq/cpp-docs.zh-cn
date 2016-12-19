---
title: "编译器错误 CS1654 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1654"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1654"
ms.assetid: 471c1298-1908-449d-b765-8dc3cd81a11d
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS1654
无法修改“variable”的成员，因为它是只读变量类型  
  
 当你尝试修改因在特殊构造中而只读的变量的成员时，将出现此错误。  
  
 发生这种情况的一个常见区域是在 [foreach](../Topic/foreach,%20in%20\(C%23%20Reference\).md) 循环内部。 它是修改集合元素的值时导致的编译时错误。 因此，你不能对[值类型](../Topic/Value%20Types%20\(C%23%20Reference\).md)（其中包括[结构](../Topic/Structs%20\(C%23%20Programming%20Guide\).md)）的元素做任何修改。 在其元素为[引用类型](../Topic/Reference%20Types%20\(C%23%20Reference\).md)的集合中，你可以修改每个元素的成员，但尝试添加、删除或更换全部元素将生成[Compiler Error CS1656](../Topic/Compiler%20Error%20CS1656.md)。  
  
## 示例  
 下面的示例生成错误 CS1654，因为 `Book` 是 `struct`。 若要修复此错误，请将 `struct` 更改为[类](../Topic/class%20\(C%23%20Reference\).md)。  
  
```  
using System.Collections.Generic; using System.Text; namespace CS1654 { struct Book { public string Title; public string Author; public double Price; public Book(string t, string a, double p) { Title=t; Author=a; Price=p; } } class Program { List<Book> list; static void Main(string[] args) { //Use a collection initializer to initialize the list Program prog = new Program(); prog.list = new List<Book>(); prog.list.Add(new Book ("The C# Programming Language", "Hejlsberg, Wiltamuth, Golde", 29.95)); prog.list.Add(new Book ("The C++ Programming Language", "Stroustrup", 29.95)); prog.list.Add(new Book ("The C Programming Language", "Kernighan, Ritchie", 29.95)); foreach(Book b in prog.list) { //Compile error if Book is a struct //Make Book a class to modify its members b.Price +=9.95; // CS1654 } } } }  
  
```