---
title: "带有一个参数（int 或 long）的输出流操控器 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "输出流, int 或 long 参数操控器"
ms.assetid: 338f3164-b5e2-4c5a-a605-7d9dc3629ca1
caps.latest.revision: 8
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 带有一个参数（int 或 long）的输出流操控器
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

iostream 类库提供用于创建参数化的操控提供一组宏。  使用一个 `int` 或 `long` 参数的操控器是一种特殊情况。  创建接受单个 `int` 或 `long` 参数的输出流操控器 \(如 `setw`\)，必须使用\_Smanip 宏，在 \<iomanip\>定义。  此示例定义插入 null 指定数量的到流的一个 `fillblank` 移动：  
  
## 示例  
  
```  
// output_stream_manip.cpp  
// compile with: /GR /EHsc  
#include <iostream>  
#include <iomanip>  
using namespace std;  
  
void fb( ios_base& os, int l )  
{  
   ostream *pos = dynamic_cast<ostream*>(&os);  
   if (pos)  
   {  
      for( int i=0; i < l; i++ )  
      (*pos) << ' ';  
   };  
}  
  
_Smanip<int>  
   __cdecl fillblank(int no)  
   {     
   return (_Smanip<int>(&fb, no));  
   }  
  
int main( )  
{  
   cout << "10 blanks follow" << fillblank( 10 ) << ".\n";  
}  
```  
  
## 请参阅  
 [带参数的自定义操控器](../standard-library/custom-manipulators-with-arguments.md)