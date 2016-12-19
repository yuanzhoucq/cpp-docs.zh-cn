---
title: "如何：访问 System::String 中的字符 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "字符 [C++], 在 System::String 中访问"
  - "示例 [C++], 字符串"
  - "字符串 [C++], 访问字符"
ms.assetid: cfc89756-aef3-4988-907e-fb236dcb7087
caps.latest.revision: 11
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：访问 System::String 中的字符
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可以访问 <xref:System.String> 对象的字符，以实现对接受 `wchar_t*` 字符串的非托管函数的高性能调用。  该方法将生成指向 <xref:System.String> 对象的第一个字符的内部指针。  可直接操作此指针，也可以将其固定然后再传递给需要普通 `wchar_t` 字符串的函数。  
  
## 示例  
 `PtrToStringChars` 返回 <xref:System.Char>，后者是一个内部指针（也称为 `byref`）。  因此，将对它进行垃圾回收。  除非要将此指针传递给本机函数，否则不必固定它。  
  
 考虑下列代码。由于 `ppchar` 是内部指针，因此不需要进行固定，并且如果垃圾回收器移动该指针所指向的字符串，则它也将更新 `ppchar`。  不使用 [pin\_ptr \(C\+\+\/CLI\)](../windows/pin-ptr-cpp-cli.md)，代码将正常运行，并且不会因为固定而对性能造成影响。  
  
 如果要将 `ppchar`  传递给本机函数，则它必须是固定指针；垃圾回收器将不能更新非托管堆栈帧上的任何指针。  
  
```  
// PtrToStringChars.cpp  
// compile with: /clr  
#include<vcclr.h>  
using namespace System;  
  
int main() {  
   String ^ mystring = "abcdefg";  
  
   interior_ptr<const Char> ppchar = PtrToStringChars( mystring );  
  
   for ( ; *ppchar != L'\0'; ++ppchar )  
      Console::Write(*ppchar);  
}  
```  
  
  **abcdefg**   
## 示例  
 此示例演示需要固定的情况。  
  
```  
// PtrToStringChars_2.cpp  
// compile with: /clr  
#include <string.h>  
#include <vcclr.h>  
// using namespace System;  
  
size_t getlen(System::String ^ s) {  
   // Since this is an outside string, we want to be secure.  
   // To be secure, we need a maximum size.  
   size_t maxsize = 256;  
   // make sure it doesn't move during the unmanaged call  
   pin_ptr<const wchar_t> pinchars = PtrToStringChars(s);  
   return wcsnlen(pinchars, maxsize);  
};  
  
int main() {  
   System::Console::WriteLine(getlen("testing"));  
}  
```  
  
 **7**   
## 示例  
 内部指针具有本机 C\+\+ 指针的所有属性。  例如，可以使用它来浏览链接数据结构，并且只使用一个指针便可执行插入和删除操作：  
  
```  
// PtrToStringChars_3.cpp  
// compile with: /clr /LD  
using namespace System;  
ref struct ListNode {  
   Int32 elem;   
   ListNode ^ Next;  
};  
  
void deleteNode( ListNode ^ list, Int32 e ) {   
   interior_ptr<ListNode ^> ptrToNext = &list;  
   while (*ptrToNext != nullptr) {  
      if ( (*ptrToNext) -> elem == e )  
         *ptrToNext = (*ptrToNext) -> Next;   // delete node  
      else  
         ptrToNext = &(*ptrToNext) -> Next;   // move to next node  
   }  
}  
```  
  
## 请参阅  
 [使用 C\+\+ 互操作（隐式 PInvoke）](../dotnet/using-cpp-interop-implicit-pinvoke.md)