---
title: "编译器警告 C4801 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4801"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4801"
ms.assetid: 05b29dff-15ef-42ca-9712-dc993afc4fd6
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告 C4801
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

引用的返回不可验证：原因  
  
 无法将跟踪引用存储到局部变量中，然后对其进行可验证的返回。  
  
 只有满足以下条件，某个引用才能可验证地返回：验证程序可以对该引用进行从创建点到返回点的跟踪，并且该引用是对数组元素或类成员的引用。  
  
 有关详细信息，请参阅[Peverify.exe（PEVerify 工具）](../Topic/Peverify.exe%20\(PEVerify%20Tool\).md)。  
  
 某个引用从创建到返回必须一直在堆栈中，才是可验证的。  
  
 C4801 始终作为错误发出。可以使用 `#pragma warning` 或 **\/wd** 关闭此警告；有关更多信息，请参见 [警告](../../preprocessor/warning.md) 或 [\/w、\/Wn、\/WX、\/Wall、\/wln、\/wdn、\/wen、\/won（警告等级）](../../build/reference/compiler-option-warning-level.md)。  
  
## 示例  
 如果验证程序看不到采用的地址，将生成 C4801。因此，必须假定这可能是一个无法验证的引用。  下面的示例生成 C4801。  
  
```  
// C4801.cpp  
// compile with: /clr:safe /c  
int% f(int% p) {  
   return p;   // C4801  
}  
```  
  
## 示例  
 下面的示例生成 C4801。  
  
```  
// C4801_b.cpp  
// compile with: /clr:safe /c  
  
int% f(int i, array<int>^ ar) {  
   int x;  
   int% bri = x;   // cannot return a byref to a local.  
   if (i < ar->Length) {  
      bri = ar[i];   // this byref is ok.  
   }  
  
   return bri;   // C4801 not returned within the basic block  
}  
```  
  
## 示例  
 如果尝试取消引用并返回 try 块中的引用值，也会生成 C4801。  这将导致代码无法验证，因为在 try 块的结尾处清除了堆栈，破坏了堆栈的任何返回值。  请改为取消对引用类型的引用并为其赋予一个变量，以确保不会引发任何异常。  然后，在函数的末尾，再次取消对引用类型的引用并将其返回。  
  
 下面的示例生成 C4801。  
  
```  
// C4801_c.cpp  
// compile with: /clr:safe  
using namespace System;  
  
ref class StackEmptyException : public System::Exception {};  
ref class StackFullException : public System::Exception {};  
  
template <typename T>  
ref struct Stack {  
  
   Stack() {  
      topElem = -1;   // initialize stack  
      stackPtr = gcnew array<T>(10);  
   }  
  
   void push(const T%);  
   T% top();  
  
private:  
   int topElem;    
   array<T>^ stackPtr;    
};  
  
template <typename T>   
T% Stack<T>::top() {  
   try {  
      return stackPtr[topElem];   // C4801  
      // Try the following line instead.  
      // T% deadstore = stackPtr[topElem] ;  
   }  
  
   catch (System::IndexOutOfRangeException ^ e) {  
      throw gcnew StackEmptyException();  
   }  
  
   catch (System::Exception ^ e) {  
      throw;  
   }  
  
   return stackPtr[topElem] ;  
}  
  
int main() {  
   typedef Stack<Int32> IntStack;  
   IntStack ^ is = gcnew IntStack();  
  
   int i = 1;  
   while (1) {  
      try {  
         is->push(i++);  
      }  
      catch (System::Exception ^ e) {  
         break;  
      }  
      Console::Write("{0} ", is->top());  
   }  
}  
```