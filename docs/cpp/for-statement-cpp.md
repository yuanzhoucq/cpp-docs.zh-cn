---
title: for 语句 （C++） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- for keyword [C++]
ms.assetid: 6c7d01b3-c4c1-4c6a-aa58-e2d198f33d4a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: feb14056e3054cdf0e802b16ce9ff20f67da43fe
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/01/2018
ms.locfileid: "39401569"
---
# <a name="for-statement-c"></a>for 语句 (C++)
重复执行语句，直到条件变为 false。 有关基于范围的 for 语句的信息，请参阅[基于范围的语句 （C++）](../cpp/range-based-for-statement-cpp.md)。  
  
## <a name="syntax"></a>语法  
  
```  
for ( init-expression ; cond-expression ; loop-expression )   
    statement;  
```  
  
## <a name="remarks"></a>备注  
 使用**为**语句可构建必须执行指定的次数的循环。  
  
 **为**语句包含三个可选部分下, 表中所示。  
  
### <a name="for-loop-elements"></a>for 循环元素  
  
|语法名称|执行时间|描述|  
|-----------------|-------------------|-----------------|  
|`init-expression`|任何其他元素的前面**有关**语句，`init-expression`执行一次。 控制权然后传递给 `cond-expression`。|通常用来初始化循环索引。 它可以包含表达式或声明。|  
|`cond-expression`|在执行 `statement` 的每次迭代之前，包括第一次迭代。 `statement` 只在 `cond-expression` 的计算结果为 true（非零）时执行。|计算结果为整数型或明确转换为整数型的类类型的表达式。 通常用于测试循环终止条件。|  
|`loop-expression`|在 `statement` 的每次迭代结束时。 执行 `loop-expression` 后，将计算 `cond-expression`。|通常用于循环索引递增。|  
  
 下面的示例演示使用不同方式**为**语句。  
  
```cpp  
#include <iostream>  
using namespace std;  
  
int main() {  
    // The counter variable can be declared in the init-expression.  
    for (int i = 0; i < 2; i++ ){   
       cout << i;  
    }  
    // Output: 01  
    // The counter variable can be declared outside the for loop.  
    int i;  
    for (i = 0; i < 2; i++){  
        cout << i;  
    }  
    // Output: 01  
    // These for loops are the equivalent of a while loop.  
    i = 0;  
    while (i < 2){  
        cout << i++;  
    }  
}  
    // Output: 012  
```  
  
 `init-expression` 和 `loop-expression` 可以包含以逗号分隔的多个语句。 例如：  
  
```cpp  
#include <iostream>  
using namespace std;  
  
int main(){  
    int i, j;  
    for ( i = 5, j = 10 ; i + j < 20; i++, j++ ) {  
        cout << "i + j = " << (i + j) << '\n';  
    }  
}  
    // Output:  
    i + j = 15  
    i + j = 17  
    i + j = 19  
```  
  
 `loop-expression` 可以递增或递减，或通过其他方式修改。  
  
```cpp  
#include <iostream>  
using namespace std;  
  
int main(){  
for (int i = 10; i > 0; i--) {  
        cout << i << ' ';  
    }  
    // Output: 10 9 8 7 6 5 4 3 2 1  
    for (int i = 10; i < 20; i = i+2) {  
        cout << i << ' ';  
    }  
    // Output: 10 12 14 16 18  
```  
  
 一个**有关**循环时终止[中断](../cpp/break-statement-cpp.md)，[返回](../cpp/return-statement-cpp.md)，或[goto](../cpp/goto-statement-cpp.md) (到外部的标记语句**为**循环) 内`statement`执行。 一个[继续](../cpp/continue-statement-cpp.md)中的语句**为**循环仅终止当前迭代。  
  
 如果`cond-expression`是省略，它被视为 true 和**有关**循环将不会终止而无需**中断**，**返回**，或**goto**在`statement`。  
  
 尽管的三个字段**为**语句通常用于初始化、 测试终止，并递增，但并不限于这些用途。 例如，下面的代码将打印数字 0 至 4。 在这种情况下，`statement` 是 null 语句：  
  
```cpp  
#include <iostream>  
using namespace std;  
  
int main()  
{  
    int i;  
    for( i = 0; i < 5; cout << i << '\n', i++){  
        ;  
    }  
}  
```  
  
## <a name="for-loops-and-the-c-standard"></a>for 循环和 C++ 标准  
 C + + 标准规定中声明的变量**有关**循环超出范围后**为**循环结束。 例如：  
  
```cpp  
for (int i = 0 ; i < 5 ; i++) {  
   // do something  
}  
// i is now out of scope under /Za or /Zc:forScope  
```  
  
 默认情况下[/Ze](../build/reference/za-ze-disable-language-extensions.md)中, 声明的变量**有关**循环保持在范围内直到**为**循环的封闭范围终止。  
  
 [/Zc: forscope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md)启用中声明的循环，而无需指定的变量的标准行为`/Za`。  
  
 还有可能要使用的范围差异**有关**循环来重新声明变量下的`/Ze`，如下所示：  
  
```cpp  
// for_statement5.cpp  
int main(){  
   int i = 0;   // hidden by var with same name declared in for loop  
   for ( int i = 0 ; i < 3; i++ ) {}  
  
   for ( int i = 0 ; i < 3; i++ ) {}  
}  
```  
  
 这更类似于中声明的变量的标准行为**有关**循环中，这要求中声明的变量**为**循环，以在循环完毕后超出范围。 当中声明的变量**有关**循环中，编译器在内部将其升级到中的本地变量**为**循环的封闭作用域，即使已存在具有相同名称的本地变量。  
  
## <a name="see-also"></a>请参阅  
 [迭代语句](../cpp/iteration-statements-cpp.md)   
 [关键字](../cpp/keywords-cpp.md)   
 [while Statement (C++)](../cpp/while-statement-cpp.md) （while 语句 (C++)）  
 [do-while 语句 (C++)](../cpp/do-while-statement-cpp.md)   
 [基于范围的 for 语句 (C++)](../cpp/range-based-for-statement-cpp.md)