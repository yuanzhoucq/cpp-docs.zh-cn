---
title: "字符串和 I/O 格式化（现代 C++） | Microsoft Docs"
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
ms.assetid: 3954e8de-a59b-4175-89c9-4ee842ab89ed
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 字符串和 I/O 格式化（现代 C++）
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

C\+\+ [iostreams](../standard-library/iostream.md) 能够格式化字符串 I\/O。  例如，以下代码显示如何设置 cout 以设定整数的输出格式为十六进制，首先保存关闭当前状态，稍后进行重新设置，因为一旦状态格式设置传递给 cout，它将保持此方式直到改变，而不仅仅针对一行代码。  
  
```fortran  
#include <iostream>  
#include <iomanip>  
  
using namespace std;  
  
int main()   
{  
    ios state(nullptr);  
  
    cout << "The answer in decimal is: " << 42 << endl;  
  
    state.copyfmt(cout); // save current formatting  
    cout << "In hex: 0x" // now load up a bunch of formatting modifiers  
        << hex   
        << uppercase   
        << setw(8)   
        << setfill('0')   
        << 42            // the actual value we wanted to print out  
        << endl;  
    cout.copyfmt(state); // restore previous formatting  
}  
  
```  
  
 在许多情况下这可能完全过于麻烦。  或者，可以使用来自 Boost C\+\+ 库的 Boost.Format，即使它是非标准的。  可以从 [Boost](http://www.boost.org/) 网站下载任何 Boost 库。  
  
 Boost.Format 的一些优点是：  
  
-   安全：类型安全和引发错误异常，例如指定过少或过多项。  
  
-   可扩展：适用于可进行流处理的任何类型。  
  
-   便利：标准 Posix 以及类似的格式字符串。  
  
 虽然 Boost.Format 是在 C\+\+ [iostreams](../standard-library/iostream-programming.md) 上生成的，安全且可扩展，但其性能仍然未得到优化。  当您需要优化性能时，请考虑 C [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) 和 [sprintf](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)，它们快速易用。  但是，它们不可展开或者没有安全漏洞。（安全版本已存在，但性能稍微有所下降。）  有关更多信息，请参见 [printf\_s、\_printf\_s\_l、wprintf\_s、\_wprintf\_s\_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md) 和 [sprintf\_s、\_sprintf\_s\_l、swprintf\_s、\_swprintf\_s\_l](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)）。  
  
 下面的代码演示了某些 Boost 格式设置功能。  
  
```cpp  
    string s = str( format("%2% %2% %1%\n") % "world" % "hello" );  
    // s contains "hello hello world"    
  
    for( auto i = 0; i < names.size(); ++i )  
        cout << format("%1% %2% %|40t|%3%\n") % first[i] % last[i] % tel[i];  
    // Georges Benjamin Clemenceau             +33 (0) 123 456 789  
    // Jean de Lattre de Tassigny              +33 (0) 987 654 321  
  
```  
  
## 请参阅  
 [欢迎回到 C\+\+](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [C\+\+ 语言参考](../cpp/cpp-language-reference.md)   
 [C\+\+ 标准库](../standard-library/cpp-standard-library-reference.md)   
 [\<iostream\>](../standard-library/iostream.md)   
 [\<limits\>](../standard-library/limits.md)   
 [\< \> iomanip](../standard-library/iomanip.md)