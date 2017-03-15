---
title: "如何：使用 for each 循环访问数组 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "数组 [C++], 与每个交互"
ms.assetid: ddc88ce2-69e1-44fc-af84-5b6f62fcb9e3
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# 如何：使用 for each 循环访问数组
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主题演示如何对数组使用的不同类型的 [for each，in](../dotnet/for-each-in.md) 关键字。  
  
## 示例  
 此示例演示如何对的数组 `for each` 引用类型。注意，如果一个维数组的所有维数多为零，`for each` 循环不循环访问数组。  
  
```  
// for_each_arrays.cpp  
// compile with: /clr  
using namespace System;  
ref struct MyClass {  
   void Test() { Console::WriteLine("in MyClass"); }  
};  
  
ref struct MyClass2 {  
   void Test() { Console::WriteLine("in MyClass2"); }  
};  
  
int main() {  
   array<MyClass ^> ^ MyArray = gcnew array<MyClass ^>(2);  
  
   int i = 0;  
   for each ( MyClass ^ c in MyArray ) {  
      Console::Write("{0} = ", i++);  
      c -> Test();  
   }  
  
   Console::WriteLine();  
  
   array< MyClass2 ^, 2 > ^ MyArray2 = gcnew array< MyClass2 ^, 2 >(2, 2);  
   i = 0;  
   for each ( MyClass2 ^ c in MyArray2 ) {  
      Console::Write("{0} = ", i++);  
      c -> Test();  
   }  
  
   array< MyClass2 ^, 2 > ^ MyArray3 = gcnew array< MyClass2 ^, 2 >(2, 0);  
   i = 0;  
   for each ( MyClass2 ^ c in MyArray3 ) {  
      Console::Write("{0} = ", i++);  
      c -> Test();  
   }  
}  
```  
  
  **0 \= 在 MyClass**  
**1 \= 在 MyClass**  
**0 \= 在 MyClass2**  
**1 \= 在 MyClass2**  
**2 \= 在 MyClass2**  
**3 \= 在 MyClass2**   
## 示例  
 此示例将循环访问 <xref:System.Collections.ArrayList>中的每种显示，请实现 <xref:System.Collections.IEnumerable>。  
  
```  
// for_each_arrays_2.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::Collections;  
  
int main() {  
   int retval = 0;  
  
   ArrayList ^ arr = gcnew ArrayList();  
   arr->Add(10);  
   arr->Add(20);  
   arr->Add(30);  
  
   for each ( int c in arr )  
      retval += c;  
   Console::WriteLine(retval);  
}  
```  
  
  **60**   
## 示例  
 此示例演示如何循环访问数组。  
  
```  
// for_each_arrays_3.cpp  
// compile with: /clr  
using namespace System;  
  
#define ARRAY_SIZE 2  
  
int main() {  
   int i, j;  
  
   // Declares an array of managed arrays of Int32.  
   array< array< Int32 > ^ > ^ IntArray = gcnew array<array< Int32 > ^>(ARRAY_SIZE);  
  
   for (i = 0 ; i < ARRAY_SIZE ; i++) {  
      IntArray[i] = gcnew array< Int32 >(ARRAY_SIZE);  
         for ( int j = 0 ; j < ARRAY_SIZE ; j++ )   
            IntArray[i][j] = i + 10;  
   }  
  
   for (i = 0 ; i < ARRAY_SIZE ; i++)  
      for (int j = 0 ; j < ARRAY_SIZE ; j++)  
         Console::WriteLine("IntArray[{0}] = {1}", i, IntArray[i][j]);  
   Console::WriteLine();  
  
   for each (array<Int32> ^ xyz in IntArray)  
      for each ( int c in xyz )  
         Console::WriteLine(c);  
}  
```  
  
  **IntArray\[0\] \= 10**  
**IntArray\[0\] \= 10**  
**IntArray\[1\] \= 11**  
**IntArray\[1\] \= 11**  
**10**  
**10**  
**11**  
**11**   
## 请参阅  
 [for each，in](../dotnet/for-each-in.md)