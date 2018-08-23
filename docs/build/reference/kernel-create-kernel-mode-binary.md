---
title: -内核 (创建内核模式二进制) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /kernel
- /kernel-
dev_langs:
- C++
ms.assetid: 6d7fdff0-c3d1-4b78-9367-4da588ce8b05
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 20ea3423acd19a70c5b7b759b9923b0132e04af0
ms.sourcegitcommit: e9ce38decc9f986edab5543de3464b11ebccb123
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/13/2018
ms.locfileid: "42572529"
---
# <a name="kernel-create-kernel-mode-binary"></a>/kernel（创建内核模式二进制）
创建可在 Windows 内核中执行的二进制文件。  
  
## <a name="syntax"></a>语法  
  
```  
/kernel[-]  
```  
  
## <a name="arguments"></a>自变量  
 **/kernel**  
 当前项目中的代码在编译和链接时使用了一组 C++ 规则（特定于将在内核模式中运行的代码）。  
  
 **/kernel-**  
 当前项目中的代码在编译和链接时未使用 C++ 规则（特定于将在内核模式中运行的代码）。  
  
## <a name="remarks"></a>备注  
 没有任何`#pragma`相当于控制此选项。  
  
 指定 **/kernel**选项告知编译器和链接器应将裁定哪些语言功能是允许在内核模式下，还要确保有足够的表达力来避免运行时不稳定，这是唯一的内核模式 c + +。 此目标通过以下方法实现：禁止使用在内核模式中有破坏性的 C++ 语言功能，并针对可能有破坏性但无法禁用的 C++ 语言功能提供警告。  
  
 **/Kernel**选项适用于生成的编译器和链接器阶段，并在项目级别设置。 传递 **/kernel**开关来指示编译器生成的二进制文件，在链接后应加载的 Windows 内核。 编译器会将 C++ 语言功能的范围缩小为与内核兼容的子集。  
  
 下表列出了编译器行为发生变化时 **/kernel**指定。  
  
|行为类型|**/kernel**行为|  
|-------------------|---------------------------|  
|C++ 异常处理|禁用。 `throw` 和 `try` 关键字的所有实例都发出了编译器错误（异常规范 `throw()` 除外）。 否 **/EH**选项将与兼容 **/kernel**，除 **/EH-**。|  
|RTTI|禁用。 除非以静态方式使用 `dynamic_cast`，否则 `typeid` 和 `dynamic_cast` 关键字的所有实例都会发出编译器错误。|  
|`new` 和 `delete`|您必须显式定义 `new()` 或 `delete()` 运算符；编译器和运行时都不会提供默认定义。|  
  
 自定义调用约定， [/GS](../../build/reference/gs-buffer-security-check.md)生成选项和所有优化都允许使用时 **/kernel**选项。 内联基本上没有受 **/kernel**，与编译器遵循相同的语义。 如果你想要确保`__forceinline`遵循内联限定符，则必须确保该警告[C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md)启用，以便您了解特定`__forceinline`函数何时没有内联。  
  
 当向编译器传递 **/kernel**开关，它会预定义名为预处理器宏`_KERNEL_MODE`且其值**1**。 你可以使用此宏，根据执行环境是处于用户模式还是内核模式下按条件编译代码。 例如，以下代码指定在针对内核模式执行对类进行编译时，类应该位于不可分页的内存段中。  
  
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
  
 一些目标体系结构的以下组合并 **/arch**选项一起使用时生成错误 **/kernel**:  
  
-   **/arch: {SSE&#124;SSE2&#124;AVX}** 不支持在 x86 上。 仅 **/arch:ia32**支持与 **/kernel** x86 上。  
  
-   **/arch: avx**不支持 **/kernel**在 x64 上。  
  
 使用生成 **/kernel**还将传递 **/kernel**到链接器。 下面显示了这对链接器行为的影响：  
  
-   禁用了增量链接。 如果您将添加 **/incremental**到命令行中，链接器会发出此错误：  
  
     **LINK： 错误 LNK1295: / 增量与不兼容 / 内核规范;链接而无需 / 增量**  
  
-   链接器检查每个对象文件 （或静态库中任何包含的存档成员） 以查看是否它无法编译过的已通过使用 **/kernel**选项，但却没有。 如果任何实例都满足此标准，链接器仍然会成功链接，但可能发出警告，如下表所示。  
  
    ||**/kernel** obj|**/kernel-** obj、 MASM obj 或 cvtresed|混合 **/kernel**并 **/kernel-** obj|  
    |-|----------------------|-----------------------------------------------|-------------------------------------------------|  
    |**链接/内核**|是|是|是，但出现警告 LNK4257|  
    |**链接**|是|是|是|  
  
     **不使用 /KERNEL; 编译 LNK4257 正在链接对象映像可能无法运行**  
  
 **/Kernel**选项和 **/driver**独立运行且不会互相影响。  
  
### <a name="to-set-the-kernel-compiler-option-in-visual-studio"></a>在 Visual Studio 中设置 /kernel 编译器选项  
  
1.  打开**属性页**项目对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  选择**C/c + +** 文件夹。  
  
3.  选择**命令行**属性页。  
  
4.  在中**其他选项**框中，添加`/kernel`或`/kernel-`。  
  
## <a name="see-also"></a>请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)