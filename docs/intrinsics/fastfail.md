---
title: __fastfail |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
ms.assetid: 9cd32639-e395-4c75-9f3a-ac3ba7f49921
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b59aeb1bd2e7986e173608689b0b1c37a0ef247e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33334361"
---
# <a name="fastfail"></a>__fastfail
**Microsoft 专用**  
  
 立即终止开销最少的调用过程。  
  
## <a name="syntax"></a>语法  
  
```  
void __fastfail(unsigned int code);  
```  
  
#### <a name="parameters"></a>参数  
 [in] `code`  
 winnt.h 或 wdm.h 中的 `FAST_FAIL_<description>` 符号常量表示过程终止原因。  
  
## <a name="return-value"></a>返回值  
 `__fastfail` 内部函数不会返回。  
  
## <a name="remarks"></a>备注  
 `__fastfail`内部函数提供了一种机制*快速失败*请求-潜在破坏进程请求立即终止进程到一种方法。 无法使用常规异常处理设施处理可能已破坏程序状态和堆栈至无法恢复的的严重故障。 使用 `__fastfail` 终止开销最少的进程。  
  
 在内部，可以使用几个特定于体系结构的机制实现 `__fastfail`：  
  
|体系结构|指令|代码参数的位置|  
|------------------|-----------------|-------------------------------|  
|x86|int 0x29|ecx|  
|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|int 0x29|rcx|  
|ARM|操作码 0xDEFB|r0|  
  
 快速失败请求是独立的请求，通常只需执行两个指令。 一旦执行快速失败请求后，内核就会采取相应的行动。 在用户模式代码中，引发速快速失败事件时，除指令指针本身外不存在任何内存依赖项。 即使存在严重的内存破坏，也可最大限度地提高其可靠性。  
  
 `code` 参数（winnt.h 或 wdm.h 中的其中一个 `FAST_FAIL_<description>` 符号常量）描述故障条件的类型并采用特定于环境的方式纳入故障报告。  
  
 用户模式开始失败显示为第二个机会非持续性异常，异常代码为 0xC0000409，至少包含一个异常参数。 第一个异常参数为 `code` 值。 此异常代码对 Windows 错误报告 (WER) 和调试基础结构指示进程已损坏并且应采取最少的进程内操作以响应故障。 内核模式快速失败请求可以通过使用专用检错代码 `KERNEL_SECURITY_CHECK_FAILURE` (0x139) 实现。 在这两种情况下，都没有调用异常处理程序，因为程序预期处于损坏状态。 如果存在调试程序，就有机会在终止进程之前检查程序的状态。  
  
 Windows 8 开始支持本机快速失败机制。 不支持本机快速失败指令的 Windows 操作系统通常会将快速失败请求视为访问冲突，或视为 `UNEXPECTED_KERNEL_MODE_TRAP` 错误检查。 在这些情况下，仍然会终止程序，但并不一定会快速终止。  
  
 `__fastfail` 只能用作内部函数。  
  
## <a name="requirements"></a>要求  
  
|内部函数|体系结构|  
|---------------|------------------|  
|`__fastfail`|x86、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]、ARM|  
  
 **标头文件** \<intrin.h >  
  
**结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)