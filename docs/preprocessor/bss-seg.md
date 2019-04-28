---
title: bss_seg
ms.date: 10/22/2018
f1_keywords:
- vc-pragma.bss_seg
- bss_seg_CPP
helpviewer_keywords:
- pragmas, bss_seg
- bss_seg pragma
ms.assetid: 755f0154-de51-4778-97d3-c9b24e445079
ms.openlocfilehash: 489ced11bb6024fdf9818872c07ab7feebfeabf3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62212407"
---
# <a name="bssseg"></a>bss_seg

指定其中的未初始化变量存储在 .obj 文件中的段。

## <a name="syntax"></a>语法

```
#pragma bss_seg( [ [ { push | pop }, ] [ identifier, ] ] [ "segment-name" [, "segment-class" ] )
```

### <a name="parameters"></a>参数

**push**<br/>
（可选）将一个记录置于内部编译器堆栈上。 一个*pu*sh * 可以*标识符*并*段名称*。

**pop**<br/>
（可选）从内部编译器堆栈的顶部移除记录。

*identifier*<br/>
（可选）与一起使用时**推送**，将名称分配给内部编译器堆栈上的记录。 *标识符*使多个记录只用一个**pop**命令。 与一起使用时**pop**，弹出之前内部堆栈中弹出记录，该指令*标识符*被删除; 如果*标识符*未在执行任何操作在内部堆栈中，找到弹出。

*"segment-name"*<br/>
（可选）段的名称。 与一起使用时**pop**，在堆栈中弹出和*段名称*将成为活动段名称。

*"segment-class"*<br/>
（可选）包含与的兼容性C++之前的版本 2.0。 它将被忽略。

## <a name="remarks"></a>备注

.可以使用查看 Obj 文件[dumpbin](../build/reference/dumpbin-command-line.md)应用程序。 未初始化数据的 .obj 文件中的默认段为 .bss。 在某些情况下使用的**bss_seg**可加快通过分组为一个部分未初始化的数据加载时间。

**bss_seg**不带任何参数将段重置为.bss。

使用分配的数据**bss_seg**杂注不会保留有关其位置的任何信息。

此外可以指定部分，用于初始化的数据 ([data_seg](../preprocessor/data-seg.md))，函数 ([code_seg](../preprocessor/code-seg.md))，和常量变量 ([const_seg](../preprocessor/const-seg.md))。

请参阅[/section](../build/reference/section-specify-section-attributes.md)的名称创建一个部分时，不应使用的列表。

## <a name="example"></a>示例

```cpp
// pragma_directive_bss_seg.cpp
int i;                     // stored in .bss
#pragma bss_seg(".my_data1")
int j;                     // stored in .my_data1

#pragma bss_seg(push, stack1, ".my_data2")
int l;                     // stored in .my_data2

#pragma bss_seg(pop, stack1)   // pop stack1 from stack
int m;                     // stored in .my_data1

int main() {
}
```

## <a name="see-also"></a>请参阅

[Pragma 指令和 __Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
