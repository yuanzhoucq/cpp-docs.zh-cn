---
title: code_seg 杂注
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.code_seg
helpviewer_keywords:
- pragmas, code_seg
- code_seg pragma
ms.assetid: bf4faac1-a511-46a6-8d9e-456851d97d56
ms.openlocfilehash: 65d702273593dc7fba68cc040f700b01a2c5e4a7
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446468"
---
# <a name="code_seg-pragma"></a>code_seg 杂注

指定在对象（.obj）文件中存储函数的文本部分（分段）。

## <a name="syntax"></a>语法

> **#pragma code_seg （** ["*节名*" [ **，** "*节类*"]] **）** \
> **#pragma code_seg （** { **push** | **pop** } [ **，** *标识符*] [ **，** "*节名*" [ **，** "*节类*"]] **）**

### <a name="parameters"></a>参数

**推送**\
可有可无将记录放在内部编译器堆栈上。 **推送**可以具有*标识符*和*节名称*。

**pop**\
可有可无从内部编译器堆栈的顶部移除一条记录。 **Pop**可以具有*标识符*和*节名称*。 使用*标识符*只需使用一个**pop**命令即可弹出多个记录。 *节名称*成为 pop 后面的活动文本部分名称。

*标识符*\
可有可无与**push**一起使用时，将为内部编译器堆栈上的记录指定一个名称。 当与**pop**一起使用时，指令将从内部堆栈中弹出记录，直到删除*标识符*。 如果在内部堆栈上找不到*标识符*，则不会弹出任何内容。

"*节名*" \
可有可无节的名称。 当与**pop**一起使用时，将弹出堆栈，并且*节名称*将成为活动文本部分名称。

"*section 类*" \
可有可无已忽略，但包含它是为了与版本C++ 2.0 之前的版本兼容。

## <a name="remarks"></a>备注

对象文件中的*部分*是作为一个单元加载到内存中的已命名数据块。 *文本部分*是包含可执行代码的部分。 在本文中，术语 "*段*" 和 "*节*" 的含义相同。

**Code_seg**杂注指令通知编译器将来自翻译单元的所有后续对象代码放入名为 "*节名*" 的文本部分。 默认情况下，用于对象文件中的函数的文本部分名为 `.text`。 不带*节名*参数**code_seg**杂注指令重置后续对象代码的文本部分名称以 `.text`。

**Code_seg**杂注指令不控制为实例化模板生成的对象代码的位置。 它也不控制由编译器隐式生成的代码，如特殊成员函数。 若要控制该代码，建议改为使用[__declspec （code_seg （...）](../cpp/code-seg-declspec.md)特性。 它使您能够控制所有对象代码的放置，包括编译器生成的代码。

有关不应用于创建部分的名称的列表，请参阅[/SECTION](../build/reference/section-specify-section-attributes.md)。

您还可以为初始化的数据（[data_seg](../preprocessor/data-seg.md)）、未初始化的数据（[bss_seg](../preprocessor/bss-seg.md)）和常量变量（[const_seg](../preprocessor/const-seg.md)）指定节。

可以使用[DUMPBIN。EXE](../build/reference/dumpbin-command-line.md)应用程序来查看对象文件。 Visual Studio 随附每个受支持的目标体系结构的 DUMPBIN 版本。

## <a name="example"></a>示例

此示例演示如何使用**code_seg**杂注指令来控制对象代码的放置位置：

```cpp
// pragma_directive_code_seg.cpp
void func1() {                  // stored in .text
}

#pragma code_seg(".my_data1")
void func2() {                  // stored in my_data1
}

#pragma code_seg(push, r1, ".my_data2")
void func3() {                  // stored in my_data2
}

#pragma code_seg(pop, r1)      // stored in my_data1
void func4() {
}

int main() {
}
```

## <a name="see-also"></a>另请参阅

[code_seg （__declspec）](../cpp/code-seg-declspec.md)\
[Pragma 指令和 __pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
