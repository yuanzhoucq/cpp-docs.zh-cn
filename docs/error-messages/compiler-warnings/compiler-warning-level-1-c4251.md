---
title: "编译器警告（等级 1）C4251 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4251"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4251"
ms.assetid: a9992038-f0c2-4fc4-a9be-4509442cbc1e
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4251
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“identifier”: 类“type”需要由类“type2”的客户端使用 dll 接口  
  
 要在使用 [\_\_declspec\(dllexport\)](../../cpp/dllexport-dllimport.md) 导出类时使数据损坏的可能性降到最小，请确保：  
  
-   通过从 DLL 导出的函数访问所有静态数据。  
  
-   类的任何内联方法都不能修改静态数据。  
  
-   类的所有内联方法都不使用 CRT 函数或其他使用静态数据的库函数（有关更多信息，请参见[跨 DLL 边界传递 CRT 对象时可能的错误](../../c-runtime-library/potential-errors-passing-crt-objects-across-dll-boundaries.md)）。  
  
-   如果 EXE 和 DLL 中的实例化具有静态数据差异时，类的任何方法（无论是否为内联）都不能使用类型。  
  
 通过定义一个 DLL 可以避免导出类，该 DLL 定义一个具有虚函数的类，您可以调用这些函数对该类型的对象进行实例化和删除。然后在该类型上调用虚函数即可。  
  
 有关导出模板的更多信息，请 [http:\/\/support.microsoft.com\/default.aspx?scid\=KB;EN\-US;168958](http://support.microsoft.com/default.aspx?scid=KB;EN-US;168958)参见。  
  
 如果要从标准 C\+\+ 库中的类型派生，并且要编译调试版本 \(**\/MTd**\)，而且编译器错误消息引用 \_Container\_base，则可以忽略 C4251。  
  
```  
// C4251.cpp  
// compile with: /EHsc /MTd /W2 /c  
#include <vector>  
using namespace std;  
class Node;  
class __declspec(dllimport) VecWrapper : vector<Node *> {};   // C4251  
```