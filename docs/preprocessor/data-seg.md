---
title: data_seg 杂注
ms.date: 08/29/2019
f1_keywords:
- data_seg_CPP
- vc-pragma.data_seg
helpviewer_keywords:
- data_seg pragma
- pragmas, data_seg
ms.assetid: 65c66466-4c98-494f-93af-106beb4caf78
ms.openlocfilehash: f67a9f39695adf5067c61288cf09ea7eb481c7dd
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220383"
---
# <a name="data_seg-pragma"></a>data_seg 杂注

指定将初始化的变量存储在对象 (.obj) 文件中的数据节 (段)。

## <a name="syntax"></a>语法

> **#pragma data_seg (** ["*节名*" [ **,** "*节类*"]] **)** \
> **#pragma data_seg (** { **push** | **pop** } [ **,** *标识符*] [ , "*节名*" [ **,** "*节类*"]] **)**

### <a name="parameters"></a>参数

**请求**\
可有可无将记录放在内部编译器堆栈上。 **推送**可以具有*标识符*和*节名称*。

**弹出**\
可有可无从内部编译器堆栈的顶部移除一条记录。 **Pop**可以具有*标识符*和*节名称*。 使用*标识符*只需使用一个**pop**命令即可弹出多个记录。 *节名称*成为 pop 后面的活动数据部分名称。

*标志*\
可有可无与**push**一起使用时, 将为内部编译器堆栈上的记录指定一个名称。 当与**pop**一起使用时, 将在内部堆栈中弹出记录, 直到删除*标识符*。 如果在内部堆栈上找不到*标识符*, 则不会弹出任何内容。

*标识符*允许使用单个**pop**命令弹出多个记录。

*"节名"* \
可有可无节的名称。 当与**pop**一起使用时, 将弹出堆栈, 并且*节名称*将成为活动数据部分名称。

*"section 类"* \
可有可无已忽略, 但包含它是为了与版本C++ 2.0 之前的版本兼容。

## <a name="remarks"></a>备注

对象文件中的*部分*是作为一个单元加载到内存中的已命名数据块。 *数据部分*是包含初始化的数据的部分。 在本文中, 术语 "*段*" 和 "*节*" 的含义相同。

已初始化的变量的 .obj 文件中的默认部分是`.data`。 未初始化的变量被视为初始化为零, 并存储在中`.bss`。

**Data_seg**杂注指令通知编译器将翻译单元中的所有已初始化数据项放入名为*节名*的数据节。 默认情况下, 用于对象文件中初始化数据的数据部分命名`.data`为。 未初始化的变量被视为初始化为零, 并存储在中`.bss`。 不带*节名称*参数的`.data` **data_seg**杂注指令将后续初始化数据项的数据节名称重置为。

使用**data_seg**分配的数据不会保留有关其位置的任何信息。

有关不应用于创建部分的名称的列表, 请参阅[/SECTION](../build/reference/section-specify-section-attributes.md)。

还可以为常量变量 ([const_seg](../preprocessor/const-seg.md))、未初始化的数据 ([bss_seg](../preprocessor/bss-seg.md)) 和函数 ([code_seg](../preprocessor/code-seg.md)) 指定部分。

可以使用[DUMPBIN。EXE](../build/reference/dumpbin-command-line.md)应用程序来查看对象文件。 Visual Studio 随附每个受支持的目标体系结构的 DUMPBIN 版本。

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

## <a name="see-also"></a>请参阅

[Pragma 指令和 __pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
