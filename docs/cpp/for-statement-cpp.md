---
title: for 语句 (C++)
description: 在 Microsoft 视觉工作室C++中引用标准C++。
f1_keywords:
- for_cpp
ms.date: 04/14/2020
helpviewer_keywords:
- for keyword [C++]
ms.assetid: 6c7d01b3-c4c1-4c6a-aa58-e2d198f33d4a
ms.openlocfilehash: 92f7ae4b1f2fbaaf710cd5a8739b78cb98a0accb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375381"
---
# <a name="for-statement-c"></a>for 语句 (C++)

重复执行语句，直到条件变为 false。 有关基于范围的语句的信息，请参阅[基于范围的语句 （C++）](../cpp/range-based-for-statement-cpp.md)。

## <a name="syntax"></a>语法

> **`for (`***init 表达式***`;`***cond 表达式***`;`***循环表达式***`)`**\
> &nbsp;&nbsp;&nbsp;&nbsp;_声明_**`;`**

## <a name="remarks"></a>备注

使用**for**语句构造必须执行指定次数的循环。

**for**语句由三个可选部分组成，如下表所示。

### <a name="for-loop-elements"></a>for 循环元素

|语法名称|执行时间|说明|
|-----------------|-------------------|-----------------|
|`init-expression`|**在 for**语句的任何其他元素之前，`init-expression`仅执行一次。 控制权然后传递给 `cond-expression`。|通常用来初始化循环索引。 它可以包含表达式或声明。|
|`cond-expression`|在执行 `statement` 的每次迭代之前，包括第一次迭代。 `statement` 只在 `cond-expression` 的计算结果为 true（非零）时执行。|计算结果为整数型或明确转换为整数型的类类型的表达式。 通常用于测试循环终止条件。|
|`loop-expression`|在 `statement` 的每次迭代结束时。 执行 `loop-expression` 后，将计算 `cond-expression`。|通常用于循环索引递增。|

以下示例显示了使用**for**语句的不同方法。

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

当在`statement`for 循环中[执行中断](../cpp/break-statement-cpp.md)、[返回](../cpp/return-statement-cpp.md)或[goto（](../cpp/goto-statement-cpp.md)到**for**循环外部标记的语句）时 **，for**循环将终止。 **for**循环中的[继续](../cpp/continue-statement-cpp.md)语句仅终止当前迭代。

如果`cond-expression`省略`true`，则考虑 它，并且**for**循环不会在 中断、**返回**或**break****转到**内`statement`终止。

尽管**for**语句的三个字段通常用于初始化、终止测试和增量，但它们并不限于这些用途。 例如，下面的代码将打印数字 0 至 4。 在这种情况下，`statement` 是 null 语句：

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

C++标准表示，**在 for**循环中声明的变量应在**for**循环结束后超出范围。 例如：

```cpp
for (int i = 0 ; i < 5 ; i++) {
   // do something
}
// i is now out of scope under /Za or /Zc:forScope
```

默认情况下，在[/Ze](../build/reference/za-ze-disable-language-extensions.md)下，**在 for**循环中声明的变量将保留在作用域中，直到**for**循环的封闭作用域结束。

[/Zc：forScope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md)支持在循环中声明的变量的标准行为，而无需指定`/Za`。

也可以使用**for**循环的范围差异来重新声明变量，`/Ze`如下所示：

```cpp
// for_statement5.cpp
int main(){
   int i = 0;   // hidden by var with same name declared in for loop
   for ( int i = 0 ; i < 3; i++ ) {}

   for ( int i = 0 ; i < 3; i++ ) {}
}
```

此行为更紧密地模拟**在 for**循环中声明的变量的标准行为，该行为要求在**for**循环中声明的变量在循环完成后超出范围。 当变量在**for**循环中声明时，编译器在内部将其提升为**for**循环的封闭作用域中的局部变量。 即使已有同名的局部变量，也会升级它。

## <a name="see-also"></a>另请参阅

[迭代语句](../cpp/iteration-statements-cpp.md)<br/>
[Keywords](../cpp/keywords-cpp.md)<br/>
[while 语句 (C++)](../cpp/while-statement-cpp.md)<br/>
[做-while 语句 （C++）](../cpp/do-while-statement-cpp.md)<br/>
[基于范围的 for 语句 (C++)](../cpp/range-based-for-statement-cpp.md)
