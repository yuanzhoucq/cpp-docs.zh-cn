---
title: "vector::assign (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::vector::assign"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "assign 成员 [STL/CLR]"
ms.assetid: 945e2048-6c61-4701-b13c-8241cbee3fa1
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# vector::assign (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

替换任何元素。  
  
## 语法  
  
```  
void assign(size_type count, value_type val);  
template<typename InIt>  
    void assign(InIt first, InIt last);  
void assign(System::Collections::Generic::IEnumerable<Value>^ right);  
```  
  
#### 参数  
 count  
 要插入的元素数。  
  
 first  
 插入范围的开头。  
  
 last  
 插入范围的末尾。  
  
 right  
 插入的枚举。  
  
 val  
 要插入的元素的值。  
  
## 备注  
 第一个成员函数用重复次的`val`元素替代`count`控制的序列。  使用它填充元素的容器具有的所有相同的默认值。  
  
 如果`InIt`是整型变量,第三个成员函数与`assign((size_type)``first``, (value_type)``last``)`行为相同。  否则，用序列 `[``first``,` `last``)` 替换受控序列。  使用会使控制序列复制另一个序列。  
  
 第三个成员函数为枚举数指定的顺序控制 `right`替换序列。  使用会使控制序列描述枚举器副本另一个序列。  
  
## 示例  
  
```  
// cliext_vector_assign.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// assign a repetition of values   
    cliext::vector<wchar_t> c2;   
    c2.assign(6, L'x');   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign an iterator range   
    c2.assign(c1.begin(), c1.end() - 1);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign an enumeration   
    c2.assign(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **x x x x x x**  
 **a b**  
 **a b c**   
## 要求  
 **标头:** \<cliext\/vector\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [向量](../dotnet/vector-stl-clr.md)   
 [vector::operator\=](../dotnet/vector-operator-assign-stl-clr.md)