---
title: "-内核 (创建内核模式二进制) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /kernel
- /kernel-
dev_langs:
- C++
ms.assetid: 6d7fdff0-c3d1-4b78-9367-4da588ce8b05
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b0e20df59788577acb680cbd18b737f7ec2d7822
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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
 没有任何`#pragma`等效以控制此选项。  
  
 指定**/kernel**选项，可以告诉编译器和链接器将裁定哪些语言功能是允许在内核模式中，并确保您具有足够的表达力来避免运行时不稳定，即内核模式 c + + 所独有。 此目标通过以下方法实现：禁止使用在内核模式中有破坏性的 C++ 语言功能，并针对可能有破坏性但无法禁用的 C++ 语言功能提供警告。  
  
 **/Kernel**选项适用于生成的编译器和链接器阶段，并在项目级别设置。 传递**/kernel**交换机以指示编译器生成的二进制文件，在链接后应会加载到 Windows 内核。 编译器会将 C++ 语言功能的范围缩小为与内核兼容的子集。  
  
 下表列出了编译器行为发生变化时**/kernel**指定。  
  
|行为类型|**/kernel**行为|  
|-------------------|---------------------------|  
|C++ 异常处理|禁用。 `throw` 和 `try` 关键字的所有实例都发出了编译器错误（异常规范 `throw()` 除外）。 不**/EH**选项是与兼容**/kernel**，除**/EH-**。|  
|RTTI|禁用。 除非以静态方式使用 `dynamic_cast`，否则 `typeid` 和 `dynamic_cast` 关键字的所有实例都会发出编译器错误。|  
|`new` 和 `delete`|您必须显式定义 `new()` 或 `delete()` 运算符；编译器和运行时都不会提供默认定义。|  
  
 自定义调用约定， [/GS](../../build/reference/gs-buffer-security-check.md)生成选项和所有优化都允许使用时**/kernel**选项。 内联基本上没有受**/kernel**，与编译器遵循相同的语义。 如果你想要确保`__forceinline`内联限定符，则必须确保该警告[C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md)以便了解何时特定启用`__forceinline`函数未内联。  
  
 当向编译器传递**/kernel**开关，它会预定义名为预处理器宏`_KERNEL_MODE`且具有值**1**。 你可以使用此宏，根据执行环境是处于用户模式还是内核模式下按条件编译代码。 例如，以下代码指定在针对内核模式执行对类进行编译时，类应该位于不可分页的内存段中。  
  
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
  
 某些目标体系结构的以下组合和**/arch**选项一起使用时生成错误**/kernel**:  
  
-   **/arch: {SSE &#124;SSE2 &#124;AVX}**不支持在 x86 上。 仅**/arch:IA32**支持**/kernel** x86 上。  
  
-   **/arch: avx**不支持**/kernel** x64 上。  
  
 生成与**/kernel**传递**/kernel**到链接器。 下面显示了这对链接器行为的影响：  
  
-   禁用了增量链接。 如果你添加**/ 增量**到命令行中，链接器会发出此错误：  
  
     **链接： 错误 LNK1295: '/ 增量' 与不兼容 / 内核规范;链接而无需 '/ 增量'**  
  
-   链接器检查每个对象文件 （或静态库中任何包含的存档成员） 以查看是否它无法具有已编译使用**/kernel**选项，但却不。 如果任何实例都满足此标准，链接器仍然会成功链接，但可能发出警告，如下表所示。  
  
    ||**/kernel** obj|**/kernel-** obj、 MASM obj 或 cvtresed|混合的**/kernel**和**/kernel-** objs|  
    |-|----------------------|-----------------------------------------------|-------------------------------------------------|  
    |**链接/内核**|是|是|是，但出现警告 LNK4257|  
    |**链接**|是|是|是|  
  
     **LNK4257 链接对象不是用 /KERNEL; 编译图像可能无法运行**  
  
 **/Kernel**选项和**/driver**选项独立运行且都不会互相影响。  
  
### <a name="to-set-the-kernel-compiler-option-in-visual-studio"></a>在 Visual Studio 中设置 /kernel 编译器选项  
  
1.  打开**属性页**项目对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  选择**C/c + +**文件夹。  
  
3.  选择**命令行**属性页。  
  
4.  在**其他选项**框中，添加`/kernel`或`/kernel-`。  
  
## <a name="see-also"></a>请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)