---
title: "编译器警告（等级 2）C4275 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4275"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4275"
ms.assetid: 18de967a-0a44-4dbc-a2e8-fc4c067ba909
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# 编译器警告（等级 2）C4275
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

非 DLL 接口类键“identifier”作为 DLL 接口类键“identifier”的基使用  
  
 导出的类是从未导出的类派生的。  
  
 要在使用 [\_\_declspec\(dllexport\)](../../cpp/dllexport-dllimport.md) 导出类时使数据损坏的可能性降到最小，请确保：  
  
-   所有静态数据都是通过从 DLL 导出的函数进行访问的。  
  
-   类的任何内联方法都不能修改静态数据。  
  
-   类的所有内联方法都不使用 CRT 函数或其他使用静态数据的库函数。  
  
-   内联类函数都不使用 CRT 函数或其他库函数（例如，可从中访问静态数据的库函数）。  
  
-   如果 EXE 和 DLL 中的实例化具有静态数据差异时，类的任何方法（无论是否为内联）都不能使用类型。  
  
 通过定义一个 DLL 可以避免导出类，该 DLL 定义一个具有虚函数的类，您可以调用这些函数对该类型的对象进行实例化和删除。然后在该类型上调用虚函数即可。  
  
 有关导出模板的更多信息，请 [http:\/\/support.microsoft.com\/default.aspx?scid\=KB;EN\-US;168958](http://support.microsoft.com/default.aspx?scid=KB;EN-US;168958)参见。  
  
 如果要从标准 C\+\+ 库中的类型派生，并且要编译调试版本 \(**\/MTd**\)，而且编译器错误消息引用 \_Container\_base，则在 Visual C\+\+ 中可以忽略 C4275。  
  
```  
// C4275.cpp  
// compile with: /EHsc /MTd /W2 /c  
#include <vector>  
using namespace std;  
class Node;  
class __declspec(dllimport) VecWrapper : vector<Node *> {};   // C4275  
```