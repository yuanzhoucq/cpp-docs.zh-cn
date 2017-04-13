---
title: "编译器警告 （等级 1） C4342 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4342
dev_langs:
- C++
helpviewer_keywords:
- C4342
ms.assetid: 47d4d5ab-069f-4cdc-98c3-10d649577a37
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: c4a2afbc3ced186b0db63b22b3cc5c2b27204c71
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-level-1-c4342"></a>编译器警告（等级 1）C4342
行为更改:*函数*调用，但在早期版本中调用时是成员运算符  
  
 在 Visual Studio 2002 之前的 Visual c + + 版本中，已调用的成员，但此行为已更改和编译器现在在命名空间范围中找到最佳匹配。  
  
 如果找到一个成员运算符，编译器会以前不考虑任何命名空间范围运算符。 如果没有在命名空间范围更好的匹配，当前编译器正确调用它，而以前的编译器不予以考虑。  
  
 你已成功将代码移植到最新版本后，应禁用此警告。  编译器可能会误报，生成此警告的代码没有任何行为更改。  
  
 默认情况下，此警告处于关闭状态。 有关详细信息，请参阅[默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。  
  
 下面的示例生成 C4342:  
  
```cpp  
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
