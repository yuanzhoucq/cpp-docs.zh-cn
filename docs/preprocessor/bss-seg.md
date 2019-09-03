---
title: bss_seg 杂注
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.bss_seg
- bss_seg_CPP
helpviewer_keywords:
- pragmas, bss_seg
- bss_seg pragma
ms.assetid: 755f0154-de51-4778-97d3-c9b24e445079
ms.openlocfilehash: a343fb45b4bbe4789f38b7a1102572cf4241ec53
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218546"
---
# <a name="bss_seg-pragma"></a>bss_seg 杂注

指定未初始化的变量存储在对象 (.obj) 文件中的节 (段)。

## <a name="syntax"></a>语法

> **#pragma bss_seg (** ["*节名*" [ **,** "*节类*"]] **)** \
> **#pragma bss_seg (** { **push** | **pop** } [ **,** *标识符*] [ , "*节名*" [ **,** "*节类*"]] **)**

### <a name="parameters"></a>参数

**请求**\
可有可无将记录放在内部编译器堆栈上。 **推送**可以具有*标识符*和*节名称*。

**弹出**\
可有可无从内部编译器堆栈的顶部移除一条记录。 **Pop**可以具有*标识符*和*节名称*。 使用*标识符*只需使用一个**pop**命令即可弹出多个记录。 *节名称*成为 pop 后的活动 BSS 部分名称。

*标志*\
可有可无与**push**一起使用时, 将为内部编译器堆栈上的记录指定一个名称。 当与**pop**一起使用时, 指令将从内部堆栈中弹出记录, 直到删除*标识符*。 如果在内部堆栈上找不到*标识符*, 则不会弹出任何内容。

*"节名"* \
可有可无节的名称。 当与**pop**一起使用时, 将弹出堆栈, 并且*节名称*成为活动的 BSS 部分名称。

*"section 类"* \
可有可无已忽略, 但包含它是为了与版本C++ 2.0 之前的版本兼容。

## <a name="remarks"></a>备注

对象文件中的*部分*是作为一个单元加载到内存中的已命名数据块。 *BSS 部分*是包含未初始化的数据的部分。 在本文中, 术语 "*段*" 和 "*节*" 的含义相同。

**Bss_seg**杂注指令通知编译器将未初始化的所有数据项从翻译单元放入名为*节名*的 bss 部分。 在某些情况下, 使用**bss_seg**可以通过将未初始化的数据组合到一个部分来缩短加载时间。 默认情况下, 用于对象文件中未初始化数据的 BSS 部分的名称`.bss`为。 不带*节名称*参数的**bss_seg**杂注指令将未初始化的后续数据项的 bss 部分名称重置`.bss`为。

使用**bss_seg**杂注分配的数据不会保留有关其位置的任何信息。

有关不应用于创建部分的名称的列表, 请参阅[/SECTION](../build/reference/section-specify-section-attributes.md)。

还可以为初始化的数据 ([data_seg](../preprocessor/data-seg.md))、函数 ([code_seg](../preprocessor/code-seg.md)) 和常量变量 ([const_seg](../preprocessor/const-seg.md)) 指定节。

可以使用[DUMPBIN。EXE](../build/reference/dumpbin-command-line.md)应用程序来查看对象文件。 Visual Studio 随附每个受支持的目标体系结构的 DUMPBIN 版本。

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

[Pragma 指令和 __pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
