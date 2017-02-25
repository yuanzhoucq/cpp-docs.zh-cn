---
title: "名称中不含链接 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "枚举器 [C++], 链接"
  - "函数参数 [C++]"
  - "函数 [C++], 参数"
  - "名称 [C++], 无链接"
  - "typedef 名称, 链接"
ms.assetid: 7174c500-12d2-4572-8c16-63c27c758fb1
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 名称中不含链接
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

没有链接的唯一名称为：  
  
-   函数参数。  
  
-   未声明为 `extern` 或 **static** 的块范围名称。  
  
-   枚举数。  
  
-   在 `typedef` 语句中声明的名称。  当 `typedef` 语句用于为未命名类类型提供名称时发生的异常。  如果类具有外部链接，则名称可能随之具有外部链接。  以下示例演示 `typedef` 名称有外部链接的情况：  
  
    ```  
    // names_with_no_linkage.cpp  
    typedef struct  
    {  
       short x;  
       short y;  
    } POINT;  
  
    extern int MoveTo( POINT pt );  
  
    int main()  
    {  
    }  
    ```  
  
     `typedef` 名称 `POINT` 成为未命名结构的类名称。  它随后用于声明具有外部链接的函数。  
  
 由于 `typedef` 名称没有链接，因此其定义可能因翻译单元而异。  由于编译单独发生，因此编译器没有检测这些差异的方法。  因此，直到链接时才会检测到此类型的错误。  请考虑下列情形：  
  
```  
// Translation unit 1  
typedef int INT  
  
INT myInt;  
...  
  
// Translation unit 2  
typedef short INT  
  
extern INT myInt;  
...  
```  
  
 前面的代码在链接时生成了一个“无法解析的外部”错误。  
  
## 示例  
 只能在文件或类范围中定义 C\+\+ 函数。  以下示例阐释如何定义函数并显示错误的函数定义：  
  
```  
// function_definitions.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
void ShowChar( char ch );    // Declare function ShowChar.  
  
void ShowChar( char ch )     // Define function ShowChar.  
{                            // Function has file scope.  
   cout << ch;  
}  
  
struct Char                  // Define class Char.  
{  
    char Show();             // Declare Show function.  
    char Get();              // Declare Get function.  
    char ch;  
};  
  
char Char::Show()            // Define Show function  
{                            //  with class scope.  
    cout << ch;  
    return ch;  
}  
  
void GoodFuncDef( char ch )  // Define GoodFuncDef  
{                            //  with file scope.  
    int BadFuncDef( int i )  // C2601, Erroneous attempt to  
    {                        //  nest functions.  
        return i * 7;  
    }  
    for( int i = 0; i < BadFuncDef( 2 ); ++i )  
        cout << ch;  
    cout << "\n";  
}  
```  
  
## 请参阅  
 [程序和链接](../cpp/program-and-linkage-cpp.md)