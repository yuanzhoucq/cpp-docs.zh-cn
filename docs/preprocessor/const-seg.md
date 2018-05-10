---
title: const_seg |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.const_seg
- const_seg_CPP
dev_langs:
- C++
helpviewer_keywords:
- pragmas, const_seg
- const_seg pragma
ms.assetid: 1eb58ee2-fb0e-4a39-9621-699c8f5ef957
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 984dc392b6ffa51d662d3ab56b1c0dc0dbc92233
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="constseg"></a>const_seg
指定的段其中[const](../cpp/const-cpp.md)变量形式存储在.obj 文件中。  
  
## <a name="syntax"></a>语法  
  
```  
#pragma const_seg ( [ [ { push | pop}, ] [ identifier, ] ] [ "segment-name" [, "segment-class" ] )  
```  
  
## <a name="remarks"></a>备注  
 这些术语的含义*段*和*部分*是可互换的本主题。  
  
 可以使用查看 OBJ 文件[dumpbin](../build/reference/dumpbin-command-line.md)应用程序。 .obj 文件中针对 `const` 变量的默认段是 .rdata。 某些 `const` 变量（如标量）将自动内联到代码流中。 内联代码将不会显示在 .rdata 中。  
  
 在 `const_seg` 中定义需要动态初始化的对象会导致未定义的行为。  
  
 不带参数的 `#pragma const_seg` 会将段重置为 .rdata。  
  
 `push`（可选）  
 将一个记录置于内部编译器堆栈上。 `push` 可以有一个 `identifier` 和 `segment-name`。  
  
 `pop`（可选）  
 从内部编译器堆栈的顶部移除一个记录。  
  
 `identifier`（可选）  
 当与 `push` 一起使用时，为内部编译器堆栈上的记录指定名称。 当与 `pop` 一起使用时，从内部堆栈中弹出记录，直到移除 `identifier`；如果未在内部堆栈上找到 `identifier`，则不会弹出任何内容。  
  
 使用 `identifier` 可实现只用一个 `pop` 命令弹出多个记录。  
  
 “`segment-name`”（可选）  
 段的名称。 堆栈与 `pop` 配合使用时将弹出，并且 `segment-name` 会成为活动段名称。  
  
 “`segment-class`”（可选）  
 包括与 2.0 版之前的 C++ 的兼容性。 它将被忽略。  
  
## <a name="example"></a>示例  
  
```  
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
 请参阅[/部分](../build/reference/section-specify-section-attributes.md)的创建部分时不应使用的名称列表。  
  
 你还可以指定为初始化的数据部分 ([data_seg](../preprocessor/data-seg.md))，未初始化的数据 ([bss_seg](../preprocessor/bss-seg.md))，和函数 ([code_seg](../preprocessor/code-seg.md))。  
  
## <a name="see-also"></a>请参阅  
 [Pragma 指令和 __Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)