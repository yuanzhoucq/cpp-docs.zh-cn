---
title: "内部 | Microsoft Docs"
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
  - "intrinsic_CPP"
  - "vc-pragma.intrinsic"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "内部杂注"
  - "杂注, 内部"
ms.assetid: 25c86ac7-ef40-47b7-a2c0-fada9c5dc3c5
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 内部
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定对杂注参数列表中指定的函数的调用是内部的。  
  
## 语法  
  
```  
  
#pragma intrinsic( function1 [, function2, ...] )  
```  
  
## 备注  
 **内部**杂注告知编译器某个函数已了解行为。编译器可以调用函数，并且不将函数调用替换为内联说明（如果将实现更好的性能）。  
  
 下面列出了带内部形式的库函数。  一旦看到**内部**杂注，它在包含指定的内部函数的第一个函数定义处生效。  该效果持续到源文件的末端或指定相同内部函数的**函数**杂注外观。  **内部**杂注仅能在函数定义之外使用 \- 在全局级。  
  
 以下函数具有内部形式，在指定 [\/Oi](../build/reference/oi-generate-intrinsic-functions.md) 时可使用这些内部形式。  
  
|||||  
|-|-|-|-|  
|[\_disable](../intrinsics/disable.md)|[\_outp](../c-runtime-library/outp-outpw-outpd.md)|[fabs](../c-runtime-library/reference/fabs-fabsf-fabsl.md)|[strcmp](../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)|  
|[\_enable](../intrinsics/enable.md)|[\_outpw](../c-runtime-library/outp-outpw-outpd.md)|[labs](../misc/labs-llabs.md)|[strcpy](../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)|  
|[\_inp](../c-runtime-library/inp-inpw-inpd.md)|[\_rotl](../c-runtime-library/reference/rotl-rotl64-rotr-rotr64.md)|[memcmp](../c-runtime-library/reference/memcmp-wmemcmp.md)|[strlen](../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)|  
|[\_inpw](../c-runtime-library/inp-inpw-inpd.md)|[\_rotr](../c-runtime-library/reference/rotl-rotl64-rotr-rotr64.md)|[memcpy](../c-runtime-library/reference/memcpy-wmemcpy.md)||  
|[\_lrotl](../c-runtime-library/reference/lrotl-lrotr.md)|[\_strset](../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)|[memset](../c-runtime-library/reference/memset-wmemset.md)||  
|[\_lrotr](../c-runtime-library/reference/lrotl-lrotr.md)|[abs](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|[strcat](../c-runtime-library/reference/strcat-wcscat-mbscat.md)||  
  
 使用内部函数的程序的运行速度比较快，因为它们没有函数调用的开销，但是，由于生成了附加代码，它们可能比较大。  
  
 **x86 专用**  
  
 \_disable 和 \_enable 内部生成内核模式说明以禁用\/启用中断，并且在内核模式驱动程序中很有用。  
  
## 示例  
 利用“cl \-c \-FAs sample.c”从命令行中编译以下代码，并查看 sample.asm 以了解它们是否转换为 x86 说明 CLI 和 STI：  
  
```  
// pragma_directive_intrinsic.cpp  
// processor: x86  
#include <dos.h>   // definitions for _disable, _enable  
#pragma intrinsic(_disable)  
#pragma intrinsic(_enable)  
void f1(void) {  
   _disable();  
   // do some work here that should not be interrupted  
   _enable();  
}  
int main() {  
}  
```  
  
 **结束 x86 专用**  
  
 下面列出的浮点函数不具有真正的内部形式。  相反，它们具有直接将参数传递到浮点芯片而不是将其推送到程序堆栈上的版本：  
  
|||||  
|-|-|-|-|  
|[acos](../c-runtime-library/reference/acos-acosf-acosl.md)|[cosh](../c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl.md)|[pow](../c-runtime-library/reference/pow-powf-powl.md)|[tanh](../c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl.md)|  
|[asin](../c-runtime-library/reference/asin-asinf-asinl.md)|[fmod](../c-runtime-library/reference/fmod-fmodf.md)|[sinh](../c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl.md)||  
  
 当您指定 [\/Oi](../build/reference/oi-generate-intrinsic-functions.md)、[\/Og](../build/reference/og-global-optimizations.md) 和 [\/fp:fast](../build/reference/fp-specify-floating-point-behavior.md)（或任何包含 \/Og 的选项：[\/Ox](../build/reference/ox-full-optimization.md)、[\/O1](../build/reference/o1-o2-minimize-size-maximize-speed.md) 和 \/O2）时，下面列出的浮点函数将具有真正的内部形式：  
  
|||||  
|-|-|-|-|  
|[atan](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)|[exp](../c-runtime-library/reference/exp-expf.md)|[log10](../c-runtime-library/reference/log-logf-log10-log10f.md)|[sqrt](../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md)|  
|[atan2](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)|[log](../c-runtime-library/reference/log-logf-log10-log10f.md)|[sin](../c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl.md)|[tan](../c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl.md)|  
|[cos](../c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl.md)||||  
  
 您可以使用 [\/fp:strict](../build/reference/fp-specify-floating-point-behavior.md) 或 [\/Za](../build/reference/za-ze-disable-language-extensions.md) 重写真正的内部浮点选项的生成。  在此情况下，函数将生成为库例程，后者将参数直接传递到浮点芯片，而不是将参数推送到程序堆栈。  
  
 有关如何启用\/禁用内部源文本块的信息和示例，请参阅 [\# pragma 函数](../preprocessor/function-c-cpp.md)。  
  
## 请参阅  
 [Pragma 指令和 \_\_Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)   
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)