---
title: "Pragma 指令和 __Pragma 关键字 | Microsoft Docs"
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
  - "#pragma"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "#pragma 指令, C/C++"
  - "__pragma 关键字"
  - "#pragma 指令 (#pragma)"
  - "pragma 指令, C/C++"
  - "杂注"
  - "杂注, C/C++"
  - "预处理器"
  - "预处理器, 杂注"
ms.assetid: 9867b438-ac64-4e10-973f-c3955209873f
caps.latest.revision: 20
caps.handback.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Pragma 指令和 __Pragma 关键字
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

杂注指令指定计算机或操作系统特定的编译器功能。  `__pragma` 关键字是特定于 Microsoft 编译器的，可利用它在宏定义中编码杂注指令。  
  
## 语法  
  
```  
  
      #pragma token-string  
__pragma(token-string)  
```  
  
## 备注  
 C 和 C\+\+ 的每个实现均支持某些对其主机或操作系统唯一的功能。  例如，某些程序必须对将数据放入的内存区域进行准确的控制或控制某些函数接收参数的方式。  在保留与 C 和 C\+\+ 语言的总体兼容性的同时，`#pragma` 指令使每个编译器均能够提供特定于计算机和操作系统的功能。  
  
 根据定义，杂注是计算机或操作系统特定的，并且通常对于每个编译器而言都有所不同。  杂注可用于条件语句以提供新的预处理器功能，或为编译器提供实现所定义的信息。  
  
 `token-string` 是一系列字符，这些字符提供了特定的编译器指令和参数（如果有）。  数字符号 \(**\#**\) 必须是位于包含杂注的行上的第一个非空白字符；空白字符可以分隔数字符号和词“pragma”。  在 `#pragma` 之后，编写转换器可分析为预处理标记的所有文本。  `#pragma` 的参数受宏展开的约束。  
  
 如果编译器发现它无法识别的杂注，则它会发出警告并继续编译。  
  
 Microsoft C 和 C\+\+ 编译器识别以下杂注：  
  
||||  
|-|-|-|  
|[alloc\_text](../preprocessor/alloc-text.md)|[auto\_inline](../preprocessor/auto-inline.md)|[bss\_seg](../preprocessor/bss-seg.md)|  
|[check\_stack](../preprocessor/check-stack.md)|[code\_seg](../preprocessor/code-seg.md)|[comment](../preprocessor/comment-c-cpp.md)|  
|[component](../preprocessor/component.md)|[conform](../preprocessor/conform.md) <sup>1</sup>|[const\_seg](../preprocessor/const-seg.md)|  
|[data\_seg](../preprocessor/data-seg.md)|[deprecated](../preprocessor/deprecated-c-cpp.md)|[detect\_mismatch](../preprocessor/detect-mismatch.md)|  
|[fenv\_access](../preprocessor/fenv-access.md)|[float\_control](../preprocessor/float-control.md)|[fp\_contract](../preprocessor/fp-contract.md)|  
|[function](../preprocessor/function-c-cpp.md)|[hdrstop](../preprocessor/hdrstop.md)|[include\_alias](../preprocessor/include-alias.md)|  
|[init\_seg](../preprocessor/init-seg.md) <sup>1</sup>|[inline\_depth](../preprocessor/inline-depth.md)|[inline\_recursion](../preprocessor/inline-recursion.md)|  
|[intrinsic](../preprocessor/intrinsic.md)|[loop](../preprocessor/loop.md) <sup>1</sup>|[make\_public](../preprocessor/make-public.md)|  
|[managed](../preprocessor/managed-unmanaged.md)|[message](../preprocessor/message.md)||  
|[omp](../preprocessor/omp.md)|[once](../preprocessor/once.md)||  
|[optimize](../preprocessor/optimize.md)|[pack](../preprocessor/pack.md)|[pointers\_to\_members](../preprocessor/pointers-to-members.md) <sup>1</sup>|  
|[pop\_macro](../preprocessor/pop-macro.md)|[push\_macro](../preprocessor/push-macro.md)|[region、endregion](../preprocessor/region-endregion.md)|  
|[runtime\_checks](../preprocessor/runtime-checks.md)|[section](../preprocessor/section.md)|[setlocale](../preprocessor/setlocale.md)|  
|[strict\_gs\_check](../preprocessor/strict-gs-check.md)|[unmanaged](../preprocessor/managed-unmanaged.md)|[vtordisp](../preprocessor/vtordisp.md) <sup>1</sup>|  
|[warning](../preprocessor/warning.md)|||  
  
 1.  仅受 C\+\+ 编译器支持。  
  
## 杂注和编译器选项  
 某些杂注提供与编译器选项相同的功能。  在源代码中遇到杂注时，将重写编译器选项所指定的行为。  例如，如果您指定了 [\/Zp8](../build/reference/zp-struct-member-alignment.md)，则可以使用 [pack](../preprocessor/pack.md) 为代码的特定部分重写此编译器设置。  
  
```  
cl /Zp8 ...  
  
<file> - packing is 8  
// ...  
#pragma pack(push, 1) - packing is now 1  
// ...  
#pragma pack(pop) - packing is 8  
</file>  
```  
  
## \_\_pragma\(\) 关键字  
 **Microsoft 专用**  
  
 编译器还支持 `__pragma` 关键字，该关键字具有与 `#pragma` 指令相同的功能，但可用于宏定义中的内联。  `#pragma` 指令不能用于宏定义中，因为编译器会将指令中的数字符号（“\#”）解释为[字符串化运算符 \(\#\)](../preprocessor/stringizing-operator-hash.md)。  
  
 下面的代码示例说明如何在宏中使用 `__pragma` 关键字。  此代码摘自“编译器 COM 支持示例”中的 ACDUAL 示例中的 mfcdual.h 头：  
  
```  
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
  
## 请参阅  
 [C\/C\+\+ 预处理器参考](../preprocessor/c-cpp-preprocessor-reference.md)   
 [C 杂注](../c-language/c-pragmas.md)   
 [C\+\+ 关键字](../cpp/keywords-cpp.md)