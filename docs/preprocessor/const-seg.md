---
title: const_seg
ms.date: 09/17/2018
f1_keywords:
- vc-pragma.const_seg
- const_seg_CPP
helpviewer_keywords:
- pragmas, const_seg
- const_seg pragma
ms.assetid: 1eb58ee2-fb0e-4a39-9621-699c8f5ef957
ms.openlocfilehash: c58f154f5e1ab6906b45d59f454a7dc2b5c0bfbe
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59029617"
---
# <a name="constseg"></a>const_seg
指定的段位置[const](../cpp/const-cpp.md)变量存储在.obj 文件中。

## <a name="syntax"></a>语法

```
#pragma const_seg ( [ [ { push | pop}, ] [ identifier, ] ] [ "segment-name" [, "segment-class" ] )
```

### <a name="parameters"></a>参数

**push**<br/>
（可选）将一个记录置于内部编译器堆栈上。 一个**推送**可以*标识符*并*段名称*。

**pop**<br/>
（可选）从内部编译器堆栈的顶部移除记录。

*identifier*<br/>
（可选）与一起使用时**推送**，将名称分配给内部编译器堆栈上的记录。 与一起使用时**pop**，弹出之前内部堆栈中弹出记录*标识符*被删除; 如果*标识符*中找不到内部堆栈中，会弹出任何内容。

使用*标识符*使多个记录只用一个**pop**命令。

"*segment-name*"<br/>
（可选）段的名称。 与一起使用时**pop**，在堆栈中弹出和*段名称*将成为活动段名称。

"*segment-class*"<br/>
（可选）包含有关使用 c + + 2.0 版之前的兼容性。 它将被忽略。

## <a name="remarks"></a>备注

这些术语的含义*段*并*部分*是本主题中可互换的。

可以使用查看 OBJ 文件[dumpbin](../build/reference/dumpbin-command-line.md)应用程序。 .obj 文件中针对 `const` 变量的默认段是 .rdata。 某些 `const` 变量（如标量）将自动内联到代码流中。 内联代码将不会显示在 .rdata 中。

在 `const_seg` 中定义需要动态初始化的对象会导致未定义的行为。

`#pragma const_seg` 不带任何参数将段重置为.rdata。

## <a name="example"></a>示例

```cpp
// pragma_directive_const_seg.cpp
// compile with: /EHsc
#include <iostream>

const int i = 7;               // inlined, not stored in .rdata
const char sz1[]= "test1";     // stored in .rdata

#pragma const_seg(".my_data1")
const char sz2[]= "test2";     // stored in .my_data1

#pragma const_seg(push, stack1, ".my_data2")
const char sz3[]= "test3";     // stored in .my_data2

#pragma const_seg(pop, stack1) // pop stack1 from stack
const char sz4[]= "test4";     // stored in .my_data1

int main() {
    using namespace std;
   // const data must be referenced to be put in .obj
   cout << sz1 << endl;
   cout << sz2 << endl;
   cout << sz3 << endl;
   cout << sz4 << endl;
}
```

```Output
test1
test2
test3
test4
```

## <a name="comments"></a>注释

请参阅[/section](../build/reference/section-specify-section-attributes.md)的名称创建一个部分时，不应使用的列表。

此外可以指定部分，用于初始化的数据 ([data_seg](../preprocessor/data-seg.md))，未初始化的数据 ([bss_seg](../preprocessor/bss-seg.md))，和函数 ([code_seg](../preprocessor/code-seg.md))。

## <a name="see-also"></a>请参阅

[Pragma 指令和 __Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)