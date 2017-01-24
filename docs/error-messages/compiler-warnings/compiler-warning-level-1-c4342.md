---
title: "编译器警告（等级 1）C4342 | Microsoft Docs"
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
  - "C4342"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4342"
ms.assetid: 47d4d5ab-069f-4cdc-98c3-10d649577a37
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4342
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

行为更改: 调用了“function”，但在以前版本中调用的是成员运算符  
  
 在以前版本的 Visual C\+\+ 中调用了某个成员，但此行为已更改，编译器将在命名空间范围内查找最佳匹配。  
  
 以前在找到成员运算符以后，编译器便不再考虑任何命名空间范围运算符。  如果在命名空间范围内有更好的匹配，当前的编译器将对其进行正确的调用，而以前的编译器则不予以考虑。  
  
 在您将代码成功接入当前版本后，应禁用此警告。否则编译器可能会误报，对没有任何行为更改的代码生成此警告。  
  
 默认情况下关闭此警告。  有关详细信息，请参阅[默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。  
  
 下面的示例生成 C4342：  
  
```  
// C4342.cpp  
// compile with: /EHsc /W1  
#include <fstream>  
#pragma warning(default: 4342)  
using namespace std;  
struct X : public ofstream {  
   X();  
};  
  
X::X() {  
   open( "ofs_bug_ev.txt." );  
   if ( is_open() ) {  
      *this << "Text" << "<-should be text" << endl;   // C4342  
      *this << ' ' << "<-should be space symbol" << endl;   // C4342  
   }  
}  
  
int main() {  
   X b;  
   b << "Text" << "<-should be text" << endl;  
   b << ' ' << "<-should be space symbol" << endl;  
}  
```