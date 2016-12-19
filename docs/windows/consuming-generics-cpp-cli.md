---
title: "从其他 .NET 语言中使用的一般 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "普通 [C++], 使用来自 .NET 语言"
ms.assetid: e6330ef5-e907-432e-b527-7a22f5899639
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 从其他 .NET 语言中使用的一般
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

一种 .NET 语言编写泛型可能在其他 .NET 语言。  不同于常规模板，则在已编译的程序集仍保存一般。  因此，一个比泛型类型定义的程序集能实例化泛型类型在不同程序集甚至在其他语言。  
  
## 备注  
 有关详细信息，请参阅：  
  
-   [泛型介绍](../Topic/Introduction%20to%20Generics%20\(C%23%20Programming%20Guide\).md)  
  
-   [Visual Basic 中的泛型类型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)  
  
## 示例  
  
### 说明  
 此示例中演示 C\# 定义的泛型类。  
  
### 代码  
  
```  
// consuming_generics_from_other_NET_languages.cs  
// compile with: /target:library  
// a C# program  
public class CircularList<ItemType> {  
   class ListNode    {  
      public ItemType m_item;  
      public ListNode next;  
      public ListNode(ItemType item) {  
         m_item = item;  
      }  
   }  
  
   ListNode first, last;  
  
   public CircularList() {}  
  
   public void Add(ItemType item) {  
      ListNode newnode = new ListNode(item);  
      if (first == null) {  
         first = last = newnode;  
         first.next = newnode;  
         last.next = first;  
      }  
      else {  
         newnode.next = first;  
         first = newnode;  
         last.next = first;  
      }   
   }  
  
   public void Remove(ItemType item) {  
      ListNode iter = first;  
      if (first.m_item.Equals( item )) {  
         first =   
         last.next = first.next;  
      }  
      for ( ; iter != last ; iter = iter.next )  
         if (iter.next.m_item.Equals( item )) {  
              if (iter.next == last)  
                  last = iter;  
              iter.next = iter.next.next;  
              return;  
          }  
   }  
  
   public void PrintAll() {  
      ListNode iter = first;  
      do {  
         System.Console.WriteLine( iter.m_item );  
         iter = iter.next;  
      } while (iter != last);  
   }  
}  
```  
  
## 示例  
  
### 说明  
 此示例使用 C\# 编写的程序集。  
  
### 代码  
  
```  
// consuming_generics_from_other_NET_languages_2.cpp  
// compile with: /clr  
#using <consuming_generics_from_other_NET_languages.dll>  
using namespace System;  
class NativeClass {};  
ref class MgdClass {};  
  
int main() {  
   CircularList<int>^ circ1 = gcnew CircularList<int>();  
   CircularList<MgdClass^>^ circ2 = gcnew CircularList<MgdClass^>();  
  
   for (int i = 0 ; i < 100 ; i += 10)  
      circ1->Add(i);  
   circ1->Remove(50);  
   circ1->PrintAll();  
}  
```  
  
### Output  
  
```  
90  
80  
70  
60  
40  
30  
20  
10  
```  
  
## 请参阅  
 [泛型](../windows/generics-cpp-component-extensions.md)