---
title: "/kernel（创建内核模式二进制） | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/kernel"
  - "/kernel-"
dev_langs: 
  - "C++"
ms.assetid: 6d7fdff0-c3d1-4b78-9367-4da588ce8b05
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /kernel（创建内核模式二进制）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

创建在 Windows 内核可以执行的二进制文件。  
  
## 语法  
  
```  
/kernel[-]  
```  
  
## Arguments  
 **\/kernel**  
 在当前项目中编译代码，而链接使用一组在内核模式中运行的特定 C\+\+ 代码的语言规则。  
  
 **\/kernel\-**  
 在当前项目中编译链接代码，不使用一组在内核模式中运行的特定 C\+\+ 代码的语言规则。  
  
## 备注  
 没有与 `#pragma` 等效的方法来控制该选项。  
  
 指定 **\/kernel** 选项告知编译器和链接器仲裁哪些语言功能在内核模式是允许的，并确保具有足够的能力来避免内核模式 C\+\+ 唯一的运行时不稳定。  这通过禁止使用完成生成 Scrum 在内核模式并提供警告对 C\+\+ 语言功能是潜在破坏性的 C\+\+ 语言功能，但不能禁用。  
  
 **\/kernel** 适用于生成选项的编译器和链接器阶段和设置项目级别。  将 **\/kernel** 切换向编译器表明应将生成的二进制，在链接之后，载入到 Windows 内核。  编译器减少 C\+\+ 语言功能的范围为一个与内核兼容的子集。  
  
 如果指定 **\/kernel**，则下表列出编译器行为的更改。  
  
|行为类型|**\/kernel**行为|  
|----------|--------------------|  
|C\+\+ 异常处理|禁用。  关键字 `throw` 和 `try` 的所有实例发出编译器错误 \(除外异常规范 `throw()`\)。  **\/EH** 选项与 **\/kernel**不兼容，除了 **\/EH\-**。|  
|RTTI|禁用。  除非静态使用 `dynamic_cast`，否则 `dynamic_cast` 和关键字 `typeid` 的所有实例发出一个编译器错误。|  
|`new` 和 `delete`|您必须显式定义 `new()` 或 `delete()` 运算符；编译器和运行时不提供一个默认定义。|  
  
 在使用 **\/kernel** 选项时自定义的调用约定，[\/GS](../../build/reference/gs-buffer-security-check.md) 生成选项并允许所有优化。  内联不受 **\/kernel**的大影响，并且采用编译器相同的语义。  如果希望确保内联限定符`__forceinline` 的 采用，必须确保警告[C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md) 启用，以便您知道特定 `__forceinline` 函数时不内联。  
  
 当编译器通过 **\/kernel** 开关时，该预定义命名为 `_KERNEL_MODE` 并具有 **1**值的预处理器宏。  可以使用此基于有条件地编译的代码执行环境是否在用户模式下或内核模式。  例如，下列代码指定类应在不可分页的内存段，当为内核模式下执行时编译。  
  
```cpp  
#ifdef _KERNEL_MODE  
#define NONPAGESECTION __declspec(code_seg("$kerneltext$"))  
#else  
#define NONPAGESECTION  
#endif  
  
class NONPAGESECTION MyNonPagedClass  
{  
  
};  
  
```  
  
 在用于 **\/kernel**，则某些目标结构和 **\/arch** 选项的组合产生以下错误：  
  
-   x86不支持**\/arch:{SSE&#124;SSE2&#124;AVX}** 。  **\/arch:IA32** 仅支持在 x86 的 **\/kernel**。  
  
-   **\/arch:AVX** 不支持对 x64 的 **\/kernel**。  
  
 生成使用 **\/kernel** 还将 **\/kernel** 传递到链接器。  这显示它如何影响链接器行为：  
  
-   禁用增量链接。  如果将 **\/incremental** 添加到命令行，链接器就发出此错误：  
  
     **LINK : fatal error LNK1295: '\/INCREMENTAL' not compatible with '\/KERNEL' specification; link without '\/INCREMENTAL'**  
  
-   链接器检查每个对象文件 \(或从静态库的任何包含的存档成员\) 以查看其是否能编译使用 **\/kernel** 选项，而不是。  如果任何实例满足此标准，如下表所示，链接器仍然成功链接但可能发出警告。  
  
    ||**\/kernel**obj|obj MASM obj 或 cvtresed**\/kernel\-**，|**\/kernel** 和 **\/kernel\-** objs 的组合|  
    |-|---------------------|--------------------------------------------|--------------------------------------------|  
    |**link \/kernel**|是|是|与 LNK4257 警告|  
    |**link**|是|是|是|  
  
     **LNK4257 linking object not compiled with \/KERNEL ; image may not run**  
  
 **\/kernel** 选项和 **\/driver** 选项中独立运行和两者都不会影响其他操作。  
  
### 在 Visual Studio 中设置\/kernel编译器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参阅[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  选择 **C\/C\+\+** 文件夹。  
  
3.  选择**“命令行”**属性页。  
  
4.  在 **其他选项** 框中，添加 `/kernel` 或 `/kernel-`。  
  
## 请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)