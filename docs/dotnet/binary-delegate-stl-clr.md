---
title: "binary_delegate (STL/CLR) | Microsoft Docs"
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
  - "cliext::binary_delegate"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "binary_delegate 函数 [STL/CLR]"
ms.assetid: 52a9291a-e354-4b9e-a035-78dac1179ec5
caps.latest.revision: 14
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# binary_delegate (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

genereic 类描述一委托参数。  使用该指定委托根据其参数和返回类型。  
  
## 语法  
  
```  
generic<typename Arg1,  
    typename Arg2,  
    typename Result>  
    delegate Result binary_delegate(Arg1, Arg2);  
```  
  
#### 参数  
 Arg1  
 第一个参数的类型。  
  
 Arg2  
 第二个参数的类型为 。  
  
 结果  
 返回类型 。  
  
## 备注  
 委托 genereic 描述两参数函数。  
  
 请注意：  
  
 `binary_delegate<int, int, int> Fun1;`  
  
 `binary_delegate<int, int, int> Fun2;`  
  
 `Fun1` 和 `Fun2` 类型是同义词，那么，当进行针对：  
  
 `delegate int Fun1(int, int);`  
  
 `delegate int Fun2(int, int);`  
  
 它们不是同一类型。  
  
## 示例  
  
```  
// cliext_binary_delegate.cpp   
// compile with: /clr   
#include <cliext/functional>   
  
bool key_compare(wchar_t left, wchar_t right)   
    {   
    return (left < right);   
    }   
  
typedef cliext::binary_delegate<wchar_t, wchar_t, bool> Mydelegate;   
int main()   
    {   
    Mydelegate^ kcomp = gcnew Mydelegate(&key_compare);   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **比较\(L'a', L'a'\) \= False**  
**比较 \(L'a，L'b\) \= true**  
**比较\(L'b', L'a'\) \= False**   
## 要求  
 **Header:** \<cliext\/functional\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [binary\_delegate\_noreturn](../dotnet/binary-delegate-noreturn-stl-clr.md)   
 [unary\_delegate](../dotnet/unary-delegate-stl-clr.md)   
 [unary\_delegate\_noreturn](../dotnet/unary-delegate-noreturn-stl-clr.md)