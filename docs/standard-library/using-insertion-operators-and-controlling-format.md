---
title: "使用插入运算符并控制格式 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: insertion operators
ms.assetid: cdefe986-6548-4cd1-8a67-b431d7d36a1c
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9af3a0fe28e0b5d26f17f16a6e217dce9fd82969
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="using-insertion-operators-and-controlling-format"></a>使用插入运算符并控制格式
本主题演示如何控制格式以及如何为你自己的类创建插入运算符。 插入 (**<<**) 运算符（它已被预先编程用于所有标准 C++ 数据类型）将字节发送到输出流对象。 插入运算符使用预定义的“操控器”，操控器是更改整数自变量的默认格式的元素。  
  
 你可以使用以下选项控制格式：  
  
- [输出宽度](#vclrfoutputwidthanchor3)  
  
- [对齐方式](#vclrfalignmentanchor4)  
  
- [精度](#vclrfprecisionanchor5)  
  
- [基数](#vclrfradixanchor6)  
  
##  <a name="vclrfoutputwidthanchor3"></a>输出宽度  
 若要对齐输出，可通过将 `setw` 操控器放置在流中或通过调用 **width** 成员函数来指定每个项的输出宽度。 此示例右对齐至少为 10 个字符宽的列中的值：  
  
```  
// output_width.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
int main( )  
{  
   double values[] = { 1.23, 35.36, 653.7, 4358.24 };  
   for( int i = 0; i < 4; i++ )  
   {  
      cout.width(10);  
      cout << values[i] << '\n';  
   }  
}  
```  
  
### <a name="output"></a>输出  
  
```  
    1.23 
    35.36 
    653.7 
4358.24  
```  
  
 前导空白被添加到任何少于 10 个字符宽的值。  
  
 若要填充一个字段，请使用 **fill** 成员函数，该函数设置为具有指定宽度的字段设置填充字符的值。 默认值为空白。 若要填充带星号的数字的列，请修改以前的 **for** 循环，如下所示：  
  
```  
for(int i = 0; i <4; i++)  
{  
    cout.width(10);

 cout.fill('*');

    cout <<values[i] <<endl;  
}  
```  
  
 `endl` 操控器取代了换行字符 (`'\n'`)。 输出如下所示：  
  
```  
******1.23  
*****35.36  
*****653.7  
***4358.24  
```  
  
 若要在同一行中指定数据元素的宽度，请使用 `setw` 操控器：  
  
```  
// setw.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <iomanip>  
using namespace std;  
  
int main( )  
{  
   double values[] = { 1.23, 35.36, 653.7, 4358.24 };  
   char *names[] = { "Zoot", "Jimmy", "Al", "Stan" };  
   for( int i = 0; i < 4; i++ )  
      cout << setw( 6 )  << names[i]  
           << setw( 10 ) << values[i] << endl;  
}  
```  
  
### <a name="output"></a>输出  
 **width** 成员函数在 \<iostream> 中声明。 如果使用 `setw` 或任何其他带参数的操控器，则必须包含 \<iomanip>。 在输出中，在宽度为 6 的字段中打印字符串，在宽度为 10 的字段中打印整数：  
  
```  
    Zoot 1.23  
Jimmy     35.36  
    Al 653.7  
    Stan 4358.24  
```  
  
 `setw` 和 **width** 均不截断值。 如果格式化输出超出宽度，则整个值受流的精度设置的约束进行打印。 `setw` 和 **width** 都仅影响以下字段。 已打印一个字段之后，字段宽度将恢复为其默认行为（必要宽度）。 但是，在更改之前，其他流格式选项保持有效。  
  
##  <a name="vclrfalignmentanchor4"></a>对齐方式  
 输出流默认为右对齐的文本。 若要左对齐以前示例中的名称以及右对齐数字，请替换 **for** 循环，如下所示：  
  
```  
for (int i = 0; i <4; i++)  
    cout <<setiosflags(ios::left)  
 <<setw(6)  <<names[i]  
 <<resetiosflags(ios::left)  
 <<setw(10) <<values[i] <<endl;  
```  
  
 输出如下所示：  
  
```  
Zoot        1.23  
Jimmy      35.36  
Al         653.7  
Stan     4358.24  
```  
  
 通过使用 [setiosflags](../standard-library/iomanip-functions.md#setiosflags) 操控器和 `left` 枚举器设置左对齐标志。 此枚举器在 [ios](../standard-library/basic-ios-class.md) 类中定义，因此它的引用必须包括 **ios::** 前缀。 [resetiosflags](../standard-library/iomanip-functions.md#resetiosflags) 操控器关闭左对齐标志。 与 **width** 和 `setw` 不同，`setiosflags` 和 `resetiosflags` 的效果是永久性的。  
  
##  <a name="vclrfprecisionanchor5"></a>精度  
 浮点精度的默认值为六。 例如，数字 3466.9768 打印为 3466.98。 若要更改此值的打印方式，请使用 [setprecision](../standard-library/iomanip-functions.md#setprecision) 操控器。 操控器具有两种标志：[fixed](../standard-library/ios-functions.md#fixed) 和 [scientific](../standard-library/ios-functions.md#scientific)。 如果设定了 [fixed](../standard-library/ios-functions.md#fixed)，则数字将打印为 3466.976800。 如果设定了 **scientific**，则它将打印为 3.4669773+003。  
  
 若要显示[对齐](#vclrfalignmentanchor4)中所示的具有一个有效数字的浮点数字，请替换 **for** 循环，如下所示：  
  
```  
for (int i = 0; i <4; i++)  
    cout <<setiosflags(ios::left)  
 <<setw(6)    
 <<names[i]  
 <<resetiosflags(ios::left)  
 <<setw(10)   
 <<setprecision(1)  
 <<values[i]   
 <<endl;  
```  
  
 该程序将打印此列表：  
  
```  
Zoot          1  
Jimmy     4e+001  
Al        7e+002  
Stan      4e+003  
```  
  
 若要消除科学记数法，请在 **for** 循环之前插入此语句：  
  
```  
cout <<setiosflags(ios::fixed);
```  
  
 使用固定记数法，该程序在小数点之后使用一位数字打印。  
  
```  
Zoot         1.2  
Jimmy       35.4  
Al         653.7  
Stan      4358.2  
```  
  
 如果将 **ios::fixed** 标志更改为 **ios::scientific**，程序将打印：  
  
```  
Zoot    1.2e+000  
Jimmy   3.5e+001  
Al      6.5e+002  
Stan    4.4e+003  
```  
  
 程序会再次在小数点之后打印一位数字。 如果设定了 **ios::fixed** 或 **ios::scientific** 中的任一个，则精度值将确定小数点后的位数。 如果两个标志均未设定，则精度值将确定有效位数的总数。 `resetiosflags` 操控器清除这些标志。  
  
##  <a name="vclrfradixanchor6"></a>基数  
 **dec**、**oct** 和 **hex** 操控器设定输入和输出的默认基数。 例如，如果将 **hex** 操控器插入到输出流中，该对象会将整数的内部数据表示形式正确转换为十六进制输出格式。 如果 [uppercase](../standard-library/ios-functions.md#uppercase) 标志已清除（默认），则数字将显示为采用小写格式的 a 到 f 的数字；否则，将以大写格式显示。 默认基数是 **dec**（十进制）。  
  
## <a name="quoted-strings-c14"></a>引用字符串 (C++14)  
 当将一个字符串插入到流时，可以通过调用 stringstream::str() 成员函数轻松向后检索相同的字符串。 但是，如果你想要使用提取运算符以将流插入到一个位于后面的点的新字符串，可能会收到意外的结果，因为 >> 运算符在遇到第一个空格字符时将默认停止。  
  
```  
 
std::stringstream ss;  
std::string inserted = "This is a sentence.";  
std::string extracted;  
 
ss <<inserted;  
ss>> extracted;  
 
std::cout <<inserted;     //  This is a sentence.  
std::cout <<extracted;   //   This  
```  
  
 可以手动克服这种行为，但为了使字符串往返过程更方便，C++14 在 `<iomanip>` 中添加了 `std::quoted` 流操控器。 插入时， `quoted()` 使用一个分隔符（默认情况下为双引号 ' " '）包围字符串，且在提取时，操作流以提取所有字符直到遇到最后一个分隔符。 任何嵌入的引号都使用转义符进行转义（默认为“\\\\”）。  
  
 分隔符仅存在于流对象中；它们不存在于提取的字符串中，但存在于由 [basic_stringstream::str](../standard-library/basic-stringstream-class.md#str)() 返回的字符串中。  
  
 插入和提取操作的空格行为不依赖于字符串在代码中的表示方式，因此，无论输入的字符串是原始字符串文本还是规则的字符串，带引号的运算符都很有用。 输入字符串，无论其格式是什么，都可以有嵌入的引号、换行符、制表符等等且所有这些都将被 quoted() 操控器保留。  
  
 有关详细信息和完整代码示例，请参阅 [quoted]--brokenlink--(../Topic/%3Cios%3E%20functions.md#quoted)。  
  
## <a name="see-also"></a>请参阅  
 [输出流](../standard-library/output-streams.md)   

