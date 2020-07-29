---
title: /kernel（创建内核模式二进制）
ms.date: 11/04/2016
f1_keywords:
- /kernel
- /kernel-
ms.assetid: 6d7fdff0-c3d1-4b78-9367-4da588ce8b05
ms.openlocfilehash: bcef52144e4da932e9e1b6acbcd5f2170c4c7f86
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211939"
---
# <a name="kernel-create-kernel-mode-binary"></a>/kernel（创建内核模式二进制）

创建可在 Windows 内核中执行的二进制文件。

## <a name="syntax"></a>语法

```
/kernel[-]
```

## <a name="arguments"></a>参数

**/kernel**<br/>
当前项目中的代码在编译和链接时使用了一组 C++ 规则（特定于将在内核模式中运行的代码）。

**/kernel**<br/>
当前项目中的代码在编译和链接时未使用 C++ 规则（特定于将在内核模式中运行的代码）。

## <a name="remarks"></a>备注

没有 `#pragma` 等效于控制此选项。

指定 **/kernel**选项将告知编译器和链接器仲裁在内核模式下允许哪些语言功能，并确保您有足够的可表达能力，以避免对内核模式 c + + 唯一的运行时不稳定。 此目标通过以下方法实现：禁止使用在内核模式中有破坏性的 C++ 语言功能，并针对可能有破坏性但无法禁用的 C++ 语言功能提供警告。

**/Kernel**选项适用于生成的编译器和链接器阶段，并在项目级别设置。 传递 **/kernel**开关，以指示编译器在链接后应将生成的二进制文件加载到 Windows 内核中。 编译器会将 C++ 语言功能的范围缩小为与内核兼容的子集。

下表列出了在指定 **/kernel**时编译器行为的更改。

|行为类型|**/kernel**操作|
|-------------------|---------------------------|
|C++ 异常处理|已禁用。 和关键字的所有实例都会 **`throw`** **`try`** 发出编译器错误（异常规范除外 `throw()` ）。 除 **/EH-** 外，没有 **/EH**选项与 **/kernel**兼容。|
|RTTI|已禁用。 **`dynamic_cast`** **`typeid`** 除非静态使用，否则和关键字的所有实例都会发出编译器错误 **`dynamic_cast`** 。|
|`new` 和 `delete`|您必须显式定义 `new()` 或 `delete()` 运算符；编译器和运行时都不会提供默认定义。|

使用 **/kernel**选项时，可以使用自定义调用约定、 [/gs](gs-buffer-security-check.md)生成选项以及所有优化。 内联在很大程度上不受 **/kernel**的影响，其语义与编译器相同。 如果要确保 **`__forceinline`** 内联限定符是有效的，则必须确保启用了警告[C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md) ，以便知道特定 **`__forceinline`** 函数何时不内联。

当编译器传递到 **/kernel**开关时，它将预定义名为的预处理器宏，其 `_KERNEL_MODE` 值为**1**。 你可以使用此宏，根据执行环境是处于用户模式还是内核模式下按条件编译代码。 例如，以下代码指定在针对内核模式执行对类进行编译时，类应该位于不可分页的内存段中。

```cpp
#ifdef _KERNEL_MODE
#define NONPAGESECTION __declspec(code_seg("$kerneltext$"))
#else
#define NONPAGESECTION
#endif

class NONPAGESECTION MyNonPagedClass
{
   // ...
};
```

某些目标体系结构和 **/arch**选项在与 **/kernel**一起使用时会产生错误：

- **/arch：不支持 x86&#124;SSE2&#124;AVX}** 。 X86 上的 **/kernel**只支持 **/arch： IA32** 。

- **/arch：** x64 上的 **/KERNEL**不支持 AVX。

用 **/kernel**生成还会将 **/kernel**传递到链接器。 下面显示了这对链接器行为的影响：

- 禁用了增量链接。 如果将 **/incremental**添加到命令行，链接器会发出此错误：

   **链接：严重错误 LNK1295： "/INCREMENTAL" 与 "/KERNEL" 规范不兼容;不带 "/INCREMENTAL" 的链接**

- 链接器将检查每个对象文件（或静态库中包含的任何存档成员），以查看它是否可以使用 **/kernel**选项进行编译，但不能使用。 如果任何实例都满足此标准，链接器仍然会成功链接，但可能发出警告，如下表所示。

   ||**/kernel** obj|**/kernel-** OBJ、MASM obj 或 cvtresed|**/Kernel**和 **/kernel-** obj 混合|
   |-|----------------------|-----------------------------------------------|-------------------------------------------------|
   |**链接/内核**|是|是|是，但出现警告 LNK4257|
   |**连接**|是|是|是|

   **未用/KERNEL 编译的 LNK4257 链接对象;映像可能无法运行**

**/Kernel**选项和 **/driver**选项独立操作，并且不会影响另一个选项。

### <a name="to-set-the-kernel-compiler-option-in-visual-studio"></a>在 Visual Studio 中设置 /kernel 编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择 " **c/c + +** " 文件夹。

1. 选择 "**命令行**" 属性页。

1. 在 "**附加选项**" 框中，添加 `/kernel` 或 `/kernel-` 。

## <a name="see-also"></a>另请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
