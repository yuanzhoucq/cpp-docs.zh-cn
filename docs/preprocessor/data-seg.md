---
title: data_seg
ms.date: 10/22/2018
f1_keywords:
- data_seg_CPP
- vc-pragma.data_seg
helpviewer_keywords:
- data_seg pragma
- pragmas, data_seg
ms.assetid: 65c66466-4c98-494f-93af-106beb4caf78
ms.openlocfilehash: 414fc542aa3f84f985e326960d8cf73b67fd1580
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50456376"
---
# <a name="dataseg"></a>data_seg

指定 .obj 文件中用于存储初始化变量的数据段。

## <a name="syntax"></a>语法

```
#pragma data_seg( [ [ { push | pop }, ] [ identifier, ] ] [ "segment-name" [, "segment-class" ] )
```

### <a name="parameters"></a>参数

**push**<br/>
（可选）将一个记录置于内部编译器堆栈上。 一个**推送**可以*标识符*并*段名称*。

**pop**<br/>
（可选）从内部编译器堆栈的顶部移除记录。

*identifier*<br/>
（可选）与一起使用时**推送**，将名称分配给内部编译器堆栈上的记录。 与一起使用时**pop**，弹出之前内部堆栈中弹出记录*标识符*被删除; 如果*标识符*中找不到内部堆栈中，会弹出任何内容。

*标识符*使多个记录只用一个**pop**命令。

*"段名称"*<br/>
（可选）段的名称。 与一起使用时**pop**，在堆栈中弹出和*段名称*将成为活动段名称。

*"段类"*<br/>
（可选）包含有关使用 c + + 2.0 版之前的兼容性。 它将被忽略。

## <a name="remarks"></a>备注

这些术语的含义*段*并*部分*是本主题中可互换的。

可以使用查看 OBJ 文件[dumpbin](../build/reference/dumpbin-command-line.md)应用程序。 .obj 文件中用于存储初始化变量的默认段是 .data。 未初始化的变量被视为初始化为零并且存储在 .bss 中。

**data_seg**不带任何参数将段重置为.data。

## <a name="example"></a>示例

```cpp
// pragma_directive_data_seg.cpp
int h = 1;                     // stored in .data
int i = 0;                     // stored in .bss
#pragma data_seg(".my_data1")
int j = 1;                     // stored in .my_data1

#pragma data_seg(push, stack1, ".my_data2")
int l = 2;                     // stored in .my_data2

#pragma data_seg(pop, stack1)   // pop stack1 off the stack
int m = 3;                     // stored in .my_data1

int main() {
}
```

使用分配的数据**data_seg**不会保留有关其位置的任何信息。

请参阅[/section](../build/reference/section-specify-section-attributes.md)的名称创建一个部分时，不应使用的列表。

此外可以指定为常量变量的部分 ([const_seg](../preprocessor/const-seg.md))，未初始化的数据 ([bss_seg](../preprocessor/bss-seg.md))，和函数 ([code_seg](../preprocessor/code-seg.md))。

## <a name="see-also"></a>请参阅

[Pragma 指令和 __Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
