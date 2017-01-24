---
title: "左移和右移运算符（&gt;&gt; 和 &lt;&lt;） | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "<<"
  - ">>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<< 运算符, 具有特定对象"
  - ">> 运算符"
  - "按位移位运算符"
  - "左移位运算符"
  - "运算符 [C++], 移位"
  - "右移位运算符"
  - "移位运算符"
ms.assetid: 25fa0cbb-5fdd-4657-8745-b35f7d8f1606
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 左移和右移运算符（&gt;&gt; 和 &lt;&lt;）
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

按位移位运算符包括向右移动 `>>` 的位的右移运算符 \(`shift_expression`\) 和向左移动 `<<` 的位的左移运算符 \(`shift_expression`\)。  <sup>1</sup>  
  
## 语法  
  
```  
  
        shift-expression << additive-expression  
shift-expression >> additive-expression  
```  
  
## 备注  
  
> [!IMPORTANT]
>  以下说明和示例在 x86 和 x64 体系结构的 Windows 上有效。  左移和右移运算符的实现在 ARM 版 Windows RT 设备上有很大不同。  有关详细信息，请参阅[你好 ARM](http://blogs.msdn.com/b/vcblog/archive/2012/10/25/hello-arm-exploring-undefined-unspecified-and-implementation-defined-behavior-in-c.aspx) 博客文章的“移位运算符”部分。  
  
## 左移  
 左移运算符将导致 `shift-expression` 中的位向左移动 `additive-expression` 所指定的位数。  因移位运算而空出的位上将用零填充。  左移是逻辑移动（从末端移掉的位将被舍弃，包括符号位）。  有关按位移位的类型的详细信息，请参阅[按位移位](http://en.wikipedia.org/wiki/Bitwise_shift)。  
  
 以下示例将显示使用无符号数字的左移运算。  该示例通过将值表示为 bitset 来显示对位的操作。  有关详细信息，请参阅[bitset 类](../standard-library/bitset-class.md)。  
  
```cpp  
#include <iostream>  
#include <bitset>  
using namespace std;  
  
int main() {  
    unsigned short short1 = 4;      
    bitset<16> bitset1{short1};   // the bitset representation of 4  
    cout << bitset1 << endl;  // 0000000000000100  
  
    unsigned short short2 = short1 << 1;     // 4 left-shifted by 1 = 8  
    bitset<16> bitset2{short2};  
    cout << bitset2 << endl;  // 0000000000001000  
  
    unsigned short short3 = short1 << 2;     // 4 left-shifted by 2 = 16  
    bitset<16> bitset3{short3};  
    cout << bitset3 << endl;  // 0000000000010000  
}  
  
```  
  
 如果你左移有符号的数字，以至于符号位受影响，则结果是不确定的。  以下示例将显示 Visual C\+\+ 中 1 位左移到符号位时所发生的情况。  
  
```cpp  
#include <iostream>  
#include <bitset>  
using namespace std;  
  
int main() {  
    short short1 = 16384;      
    bitset<16> bitset1{short2};  
    cout << bitset1 << endl;  // 0100000000000000   
  
    short short3 = short1 << 1;  
    bitset<16> bitset3{short3};  // 16384 left-shifted by 1 = -32768  
    cout << bitset3 << endl;  // 100000000000000  
  
    short short4 = short1 << 14;  
    bitset<16> bitset4{short4};  // 4 left-shifted by 14 = 0  
    cout << bitset4 << endl;  // 000000000000000    
}  
```  
  
## 右移  
 右移运算符将导致 `shift-expression` 中的位模式向右移动 `additive-expression` 所指定的位数。  对于无符号数字，因移位运算而空出的位上将用零填充。  对于有符号数字，符号位用于填充空出的位。  也就是说，如果数字为正，则使用 0；如果数字为负，则使用 1。  
  
> [!IMPORTANT]
>  符号为负的数字右移的结果依实现而定。  虽然 Visual C\+\+ 使用符号位填充空出的位，但是无法保证其他实现也会这样执行。  
  
 以下示例显示使用无符号数字的右移运算：  
  
```cpp  
#include <iostream>  
#include <bitset>  
using namespace std;  
  
int main() {  
    unsigned short short11 = 1024;  
    bitset<16> bitset11{short11};  
    cout << bitset11 << endl;     // 0000010000000000  
  
    unsigned short short12 = short11 >> 1;  // 512  
    bitset<16> bitset12{short12};  
    cout << bitset12 << endl;     // 0000001000000000  
  
    unsigned short short13 = short11 >> 10;  // 1  
    bitset<16> bitset13{short13};  
    cout << bitset13 << endl;     // 0000000000000001  
  
    unsigned short short14 = short11 >> 11;  // 0  
    bitset<16> bitset14{short14};  
    cout << bitset14 << endl;     // 0000000000000000}  
}  
```  
  
 下一示例显示使用符号为正的数字的右移运算。  
  
```cpp  
#include <iostream>  
#include <bitset>  
using namespace std;  
  
int main() {  
    short short1 = 1024;  
    bitset<16> bitset1{short1};  
    cout << bitset1 << endl;     // 0000010000000000  
  
    short short2 = short1 >> 1;  // 512  
    bitset<16> bitset2{short2};  
    cout << bitset2 << endl;     // 0000001000000000  
  
    short short3 = short1 >> 11;  // 0  
    bitset<16> bitset3{short3};     
    cout << bitset3 << endl;     // 0000000000000000  
}  
```  
  
 下一示例显示使用符号为负的整数的右移运算。  
  
```cpp  
#include <iostream>  
#include <bitset>  
using namespace std;  
  
int main() {  
    short neg1 = -16;  
    bitset<16> bn1{neg1};  
    cout << bn1 << endl;  // 1111111111110000  
  
    short neg2 = neg1 >> 1; // -8  
    bitset<16> bn2{neg2};  
    cout << bn2 << endl;  // 1111111111111000  
  
    short neg3 = neg1 >> 2; // -4  
    bitset<16> bn3{neg3};  
    cout << bn3 << endl;  // 1111111111111100  
  
    short neg4 = neg1 >> 4; // -1  
    bitset<16> bn4{neg4};      
    cout << bn4 << endl;  // 1111111111111111  
  
    short neg5 = neg1 >> 5; // -1   
    bitset<16> bn5{neg5};      
    cout << bn5 << endl;  // 1111111111111111  
}  
```  
  
## 移位和提升  
 移位运算符两侧的表达式必须是整数类型。  整型提升将根据[整数提升](../misc/integral-promotions.md)中描述的规则执行。  结果的类型与提升后的 `shift-expression` 类型相同。  
  
 在下面的示例中，`char` 类型的变量将提升为 `int`。  
  
```cpp  
#include <iostream>  
#include <typeinfo>  
  
using namespace std;  
  
int main() {  
    char char1 = 'a';  
  
    auto promoted1 = char1 << 1;  // 194  
    cout << typeid(promoted1).name() << endl;  // int  
  
    auto promoted2 = char1 << 10;  // 99328  
    cout << typeid(promoted2).name() << endl;   // int  
}  
```  
  
## 其他详细信息  
 如果 `additive-expression` 为负或 `additive-expression` 大于或等于 `shift-expression`（提升后）中的位数，则移位运算的结果是不确定的。  如果 `additive-expression` 为 0，移位运算不会执行。  
  
```cpp  
#include <iostream>  
#include <bitset>  
using namespace std;  
  
int main() {  
    unsigned int int1 = 4;  
    bitset<32> b1{int1};  
    cout << b1 << endl;    // 00000000000000000000000000000100  
  
    unsigned int int2 = int1 << -3;  // C4293: '<<' : shift count negative or too big, undefined behavior  
    unsigned int int3 = int1 >> -3;  // C4293: '>>' : shift count negative or too big, undefined behavior  
  
    unsigned int int4 = int1 << 32;  // C4293: '<<' : shift count negative or too big, undefined behavior  
  
    unsigned int int5 = int1 >> 32;  // C4293: '>>' : shift count negative or too big, undefined behavior  
  
    unsigned int int6 = int1 << 0;  
    bitset<32> b6{int6};  
    cout << b6 << endl;    // 00000000000000000000000000000100 (no change)}  
}  
```  
  
## 脚注  
 1 以下是 C\+\+ ISO 规范 \(INCITS\/ISO\/IEC 14882\-2011\[2012\]\) 5.8.2 和 5.8.3 两节中对移位运算符的说明。  
  
 `E1 << E2` 的值是 `E1` 向左移动 `E2` 位的结果，空出的位用零填充。  如果 `E1` 属于无符号类型，则结果的值为 `E1 × 2`<sup>E2</sup>，约减的模一大于结果类型可表示的最大值。  否则，如果 `E1` 属于有符号类型且为非负值，`E1 × 2`<sup>E2</sup> 可由结果类型的相应无符号类型表示，则该值转换为结果类型后即为得到的值；否则，该行为是不确定的。  
  
 `E1 >> E2` 的值是 `E1` 向右移动 `E2` 位的结果。  如果 `E1` 属于无符号类型或 `E1` 属于有符号类型且为非负值，则结果值为 `E1/2`<sup>E2</sup> 之商的整数部分。  如果 `E1` 属于有符号类型且为负值，则结果值由实现决定。  
  
## 请参阅  
 [使用二元运算符的表达式](../cpp/expressions-with-binary-operators.md)   
 [C\+\+ 运算符优先级和关联性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)