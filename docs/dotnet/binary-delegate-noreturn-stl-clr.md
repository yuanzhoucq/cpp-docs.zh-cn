---
title: "binary_delegate_noreturn (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::binary_delegate_noreturn"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "binary_delegate_noreturn 函数 [STL/CLR]"
ms.assetid: 055c7e9d-e5c3-48fe-9327-3f6316e8a51e
caps.latest.revision: 8
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# binary_delegate_noreturn (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

genereic 类描述返回 `void`的两参数委托。  使用该指定委托根据其参数。  
  
## 语法  
  
```  
generic<typename Arg1,  
    typename Arg2>  
    delegate void binary_delegate(Arg1, Arg2);  
```  
  
#### 参数  
 Arg1  
 第一个参数的类型。  
  
 Arg2  
 第二个参数的类型为 。  
  
## 备注  
 genereic 描述委托返回 `void`的两参数函数。  
  
 请注意：  
  
 `binary_delegate_noreturn<int, int> Fun1;`  
  
 `binary_delegate_noreturn<int, int> Fun2;`  
  
 `Fun1` 和 `Fun2` 类型是同义词，那么，当进行针对：  
  
 `delegate void Fun1(int, int);`  
  
 `delegate void Fun2(int, int);`  
  
 它们不是同一类型。  
  
## 示例  
  
```  
// cliext_binary_delegate_noreturn.cpp   
// compile with: /clr   
#include <cliext/functional>   
  
void key_compare(wchar_t left, wchar_t right)   
    {   
    System::Console::WriteLine("compare({0}, {1}) = {2}",   
        left, right, left < right);   
    }   
  
typedef cliext::binary_delegate_noreturn<wchar_t, wchar_t> Mydelegate;   
int main()   
    {   
    Mydelegate^ kcomp = gcnew Mydelegate(&key_compare);   
  
    kcomp(L'a', L'a');   
    kcomp(L'a', L'b');   
    kcomp(L'b', L'a');   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **比较 \(a,a\) \= false**  
**比较 \(a，b\) \= true**  
**比较 \(b，a\) \= false**   
## 要求  
 **头文件:** \<cliext\/functional\>  
  
 **Namespace:** cliext  
  
## 请参阅  
 [binary\_delegate](../dotnet/binary-delegate-stl-clr.md)   
 [unary\_delegate](../dotnet/unary-delegate-stl-clr.md)   
 [unary\_delegate\_noreturn](../dotnet/unary-delegate-noreturn-stl-clr.md)