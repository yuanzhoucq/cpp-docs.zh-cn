---
title: Pragma 指令和 __Pragma 关键字
ms.date: 11/04/2016
f1_keywords:
- '#pragma'
helpviewer_keywords:
- '#pragma directives, C/C++'
- __pragma keyword
- pragma directives, C/C++
- pragmas, C/C++
- preprocessor
- pragmas
- preprocessor, pragmas
- pragma directives (#pragma)
ms.assetid: 9867b438-ac64-4e10-973f-c3955209873f
ms.openlocfilehash: 9e79ba7378e28fdea863af010decb7064df415cd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50660091"
---
# <a name="pragma-directives-and-the-pragma-keyword"></a>Pragma 指令和 __Pragma 关键字

杂注指令指定计算机或操作系统特定的编译器功能。 **__Pragma**关键字，这是特定于 Microsoft 编译器，可以在宏定义中编码杂注指令。

## <a name="syntax"></a>语法

```
#pragma token-string
__pragma(token-string)
```

## <a name="remarks"></a>备注

C 和 C++ 的每个实现均支持某些对其主机或操作系统唯一的功能。 例如，某些程序必须对将数据放入的内存区域进行准确的控制或控制某些函数接收参数的方式。 **#Pragma**指令提供的每个编译器均能够保留与 C 和 c + + 语言的整体兼容性的同时提供计算机和操作系统特定的功能的方法。

根据定义，杂注是计算机或操作系统特定的，并且通常对于每个编译器而言都有所不同。 杂注可用于条件语句以提供新的预处理器功能，或为编译器提供实现所定义的信息。

`token-string` 是一系列字符，这些字符提供了特定的编译器指令和自变量（如果有）。 数字符号 (**#**) 必须是第一个非空白字符包含在行杂注; 空白字符可以分隔数字的符号和词"pragma"。 遵循 **#pragma**，编写转换器可分析为预处理标记的任何文本。 参数 **#pragma**受到宏扩展。

如果编译器发现它无法识别的杂注，则它会发出警告并继续编译。

Microsoft C 和 C++ 编译器识别以下杂注：

||||
|-|-|-|
|[alloc_text](../preprocessor/alloc-text.md)|[auto_inline](../preprocessor/auto-inline.md)|[bss_seg](../preprocessor/bss-seg.md)|
|[check_stack](../preprocessor/check-stack.md)|[code_seg](../preprocessor/code-seg.md)|[comment](../preprocessor/comment-c-cpp.md)|
|[component](../preprocessor/component.md)|[符合](../preprocessor/conform.md) <sup>1</sup>|[const_seg](../preprocessor/const-seg.md)|
|[data_seg](../preprocessor/data-seg.md)|[deprecated](../preprocessor/deprecated-c-cpp.md)|[detect_mismatch](../preprocessor/detect-mismatch.md)|
|[fenv_access](../preprocessor/fenv-access.md)|[float_control](../preprocessor/float-control.md)|[fp_contract](../preprocessor/fp-contract.md)|
|[函数](../preprocessor/function-c-cpp.md)|[hdrstop](../preprocessor/hdrstop.md)|[include_alias](../preprocessor/include-alias.md)|
|[init_seg](../preprocessor/init-seg.md) <sup>1</sup>|[inline_depth](../preprocessor/inline-depth.md)|[inline_recursion](../preprocessor/inline-recursion.md)|
|[intrinsic](../preprocessor/intrinsic.md)|[循环](../preprocessor/loop.md) <sup>1</sup>|[make_public](../preprocessor/make-public.md)|
|[托管](../preprocessor/managed-unmanaged.md)|[message](../preprocessor/message.md)||
|[omp](../preprocessor/omp.md)|[once](../preprocessor/once.md)||
|[optimize](../preprocessor/optimize.md)|[pack](../preprocessor/pack.md)|[pointers_to_members](../preprocessor/pointers-to-members.md) <sup>1</sup>|
|[pop_macro](../preprocessor/pop-macro.md)|[push_macro](../preprocessor/push-macro.md)|[region, endregion](../preprocessor/region-endregion.md)|
|[runtime_checks](../preprocessor/runtime-checks.md)|[section](../preprocessor/section.md)|[setlocale](../preprocessor/setlocale.md)|
|[strict_gs_check](../preprocessor/strict-gs-check.md)|[非托管](../preprocessor/managed-unmanaged.md)|[vtordisp](../preprocessor/vtordisp.md) <sup>1</sup>|
|[warning](../preprocessor/warning.md)|||

<sup>1</sup>仅受 c + + 编译器。

## <a name="pragmas-and-compiler-options"></a>杂注和编译器选项

某些杂注提供与编译器选项相同的功能。 在源代码中遇到杂注时，将重写编译器选项所指定的行为。 例如，如果您指定[/zp8](../build/reference/zp-struct-member-alignment.md)，可以重写此编译器设置与代码的特定部分[pack](../preprocessor/pack.md):

```
cl /Zp8 ...

<file> - packing is 8
// ...
#pragma pack(push, 1) - packing is now 1
// ...
#pragma pack(pop) - packing is 8
</file>
```

## <a name="the-pragma-keyword"></a>__pragma() 关键字

**Microsoft 专用**

编译器还支持 **__pragma**关键字，它具有相同的功能作为 **#pragma**指令，但可以使用的宏定义中的内联。 **#Pragma**指令不能用于宏定义中，因为编译器会将数字符号字符 （' #'） 解释为在指令中[字符串化运算符 （#）](../preprocessor/stringizing-operator-hash.md)。

下面的代码示例演示了如何 **__pragma**关键字可在宏中。 此代码摘自“编译器 COM 支持示例”中的 ACDUAL 示例中的 mfcdual.h 头：

```cpp
#define CATCH_ALL_DUAL \
CATCH(COleException, e) \
{ \
_hr = e->m_sc; \
} \
AND_CATCH_ALL(e) \
{ \
__pragma(warning(push)) \
__pragma(warning(disable:6246)) /*disable _ctlState prefast warning*/ \
AFX_MANAGE_STATE(pThis->m_pModuleState); \
__pragma(warning(pop)) \
_hr = DualHandleException(_riidSource, e); \
} \
END_CATCH_ALL \
return _hr; \
```

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[C/C++ 预处理器参考](../preprocessor/c-cpp-preprocessor-reference.md)<br/>
[C 杂注](../c-language/c-pragmas.md)<br/>
[关键字](../cpp/keywords-cpp.md)