---
title: "字符串和我-O 格式化 （现代 c + +） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 3954e8de-a59b-4175-89c9-4ee842ab89ed
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a13861fe03547e37c4de72c21a528e297a217511
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="string-and-io-formatting-modern-c"></a>字符串和 I/O 格式化（现代 C++）
C + + [iostreams](../standard-library/iostream.md)能够格式化字符串 I/O。 例如，下面的代码演示如何设置 cout 若要设置格式的整数输出以十六进制表示，第一次关闭的当前状态保存和重新之后，设置，因为后状态格式传递给 cout 时，它始终处于这种方式更改，而不仅仅是为一个行之前代码。  
  
```cpp  
#include <iostream>  
#include <iomanip>  
  
using namespace std;  
  
int main()   
{  
    ios state(nullptr);  
  
    cout << "The answer in decimal is: " << 42 << endl;  
  
    state.copyfmt(cout); // save current formatting  
    cout << "In hex: 0x" // now load up a bunch of formatting modifiers  
        << hex   
        << uppercase   
        << setw(8)   
        << setfill('0')   
        << 42            // the actual value we wanted to print out  
        << endl;  
    cout.copyfmt(state); // restore previous formatting  
}  
  
```  
  
 这可以是完全在许多情况下非常麻烦。 作为替代方法，你可以从提升 c + + 库中，使用 Boost.Format 即使使用了非标准。 你可以下载从任何 Boost 库[Boost](http://www.boost.org/)网站。  
  
 Boost.Format 的优点包括：  
  
-   安全： 类型安全的并在引发异常的错误 — 例如，太少或太多个项的规范。  
  
-   可扩展： 适用于可以进行流式处理任何类型。  
  
-   方便： 标准 Posix 和类似的格式字符串。  
  
 虽然 c + + 生成 Boost.Format [iostreams](../standard-library/iostream-programming.md)，它们是安全且可扩展，它们不性能优化。 当需要性能优化时，请考虑 C [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)和[sprintf](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)，这是快速且易于使用。 但是，它们不是扩展，也不安全漏洞。 （安全的版本存在，但它们会产生导致性能略微下降。 有关详细信息，请参阅[printf_s、 _printf_s_l、 wprintf_s、 _wprintf_s_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)和[sprintf_s、 _sprintf_s_l、 swprintf_s、 _swprintf_s_l](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md))。  
  
 下面的代码演示了一些格式设置功能的提升。  
  
```cpp  
    string s = str( format("%2% %2% %1%\n") % "world" % "hello" );  
    // s contains "hello hello world"    
  
    for( auto i = 0; i < names.size(); ++i )  
        cout << format("%1% %2% %|40t|%3%\n") % first[i] % last[i] % tel[i];  
    // Georges Benjamin Clemenceau             +33 (0) 123 456 789  
    // Jean de Lattre de Tassigny              +33 (0) 987 654 321  
  
```  
  
## <a name="see-also"></a>请参阅  
 [欢迎回到 c + +](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [C + + 语言参考](../cpp/cpp-language-reference.md)   
 [C++ 标准库](../standard-library/cpp-standard-library-reference.md)   
 [\<iostream >](../standard-library/iostream.md)   
 [\<限制 >](../standard-library/limits.md)   
 [\<iomanip>](../standard-library/iomanip.md)
