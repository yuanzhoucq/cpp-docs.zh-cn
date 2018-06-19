---
title: 左的移和右移运算符 (&gt; &gt;和&lt; &lt;) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- <<
- '>>'
dev_langs:
- C++
helpviewer_keywords:
- << operator [C++], with specific objects
- left shift operators [C++]
- right shift operators [C++]
- bitwise-shift operators [C++]
- '>> operator'
- shift operators [C++]
- operators [C++], shift
ms.assetid: 25fa0cbb-5fdd-4657-8745-b35f7d8f1606
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0d8835d096575f3f7a9d50c7be26fa435e5d6bcd
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32422392"
---
# <a name="left-shift-and-right-shift-operators-gtgt-and-ltlt"></a>左的移和右移运算符 (&gt; &gt;和&lt; &lt;)
按位移位运算符是右移位运算符 (>>)，移动的位*shift 表达式*到右侧，并使用左移运算符 (<<)，移动的位*shift 表达式*左侧。 <sup>1</sup>  
  
## <a name="syntax"></a>语法  
  
> *shift 表达式* `<<` *加法表达式*  
> *shift 表达式* `>>` *加法表达式*  
  
## <a name="remarks"></a>备注  
  
> [!IMPORTANT]
> 以下说明和示例在 x86 和 x64 体系结构的 Windows 上有效。 左移和右移运算符的实现在 ARM 版 Windows RT 设备上有很大不同。 有关详细信息，请参阅的"移位运算符"部分[你好 ARM](http://blogs.msdn.com/b/vcblog/archive/2012/10/25/hello-arm-exploring-undefined-unspecified-and-implementation-defined-behavior-in-c.aspx)博客文章。  
  
## <a name="left-shifts"></a>左移  
 左移运算符使中的位*shift 表达式*要数指定的位数向左移动*加法表达式*。 因移位运算而空出的位上将用零填充。 左移是逻辑移动（从末端移掉的位将被舍弃，包括符号位）。 有关类型的按位右移的详细信息，请参阅[按位右移](http://en.wikipedia.org/wiki/Bitwise_shift)。  
  
 以下示例将显示使用无符号数字的左移运算。 该示例通过将值表示为 bitset 来显示对位的操作。 有关详细信息，请参阅[bitset 类](../standard-library/bitset-class.md)。  
  
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
  
 如果你左移有符号的数字，以至于符号位受影响，则结果是不确定的。 以下示例将显示 Visual C++ 中 1 位左移到符号位时所发生的情况。  
  
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
  
## <a name="right-shifts"></a>右移  
 右移位运算符将导致位模式中的*shift 表达式*要数指定的位数向右移动*加法表达式*。 对于无符号数字，因移位运算而空出的位上将用零填充。 对于有符号数字，符号位用于填充空出的位。 也就是说，如果数字为正，则使用 0；如果数字为负，则使用 1。  
  
> [!IMPORTANT]
> 符号为负的数字右移的结果依实现而定。 虽然 Visual C++ 使用符号位填充空出的位，但是无法保证其他实现也会这样执行。  
  
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
  
## <a name="shifts-and-promotions"></a>移位和提升  
 移位运算符两侧的表达式必须是整数类型。 整型提升执行根据所述的规则[标准转换](standard-conversions.md)。 结果的类型是与提升后的类型相同*shift 表达式*。  
  
 在下面的示例中，`char` 类型的变量将提升为 `int`。  
  
```cpp  
#include <iostream>  
#include <typeinfo>  
  
using namespace std;  
  
int main() {  
    char char1 = 'a';  
  
    auto promoted1 = char1 << 1;   // 194  
    cout << typeid(promoted1).name() << endl;  // int  
  
    auto promoted2 = char1 << 10;  // 99328  
    cout << typeid(promoted2).name() << endl;  // int  
}  
```  
  
## <a name="additional-details"></a>其他详细信息  
 移位运算的结果是不确定的如果*加法表达式*为负或如果*加法表达式*大于或等于 （提升） 中的位数*shift 表达式*。 如果执行移位运算不*加法表达式*为 0。  
  
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
  
## <a name="footnotes"></a>脚注  
 1 以下是中 C++ 11 ISO 规范 （INCITS/ISO/IEC 14882-2011[2012])，部分 5.8.2 和 5.8.3 对移位运算符描述。  
  
 值**E1 << E2**是**E1**向左移动**E2**位的结果，空出 bits 将用零填充。 如果**E1**具有无符号的类型，则结果的值是**E1 × 2**<sup>**E2**</sup>，约减的模一大于中可表示的最大值结果类型中。 否则为如果**E1**有符号的类型且非负值，和**E1 × 2**<sup>**E2** </sup>是用相应的无符号类型表示结果类型，该值转换为结果类型，则生成的值;否则，该行为不确定。  
  
 值**E1 >> E2**是**E1**向右移动**E2**位的结果。 如果**E1**属于无符号的类型或如果**E1**有符号的类型且为非负值，则结果的值为的商的整数部分**E1/2** <sup>**E2**</sup>。 如果**E1**具有带符号的类型且为负值，生成的值是实现定义。  
  
## <a name="see-also"></a>请参阅  
 [使用二元运算符的表达式](../cpp/expressions-with-binary-operators.md)   
 [C++ 内置运算符、优先级和关联性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)