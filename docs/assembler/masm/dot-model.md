---
title: .MODEL
ms.date: 11/05/2019
f1_keywords:
- .MODEL
helpviewer_keywords:
- .MODEL directive
ms.assetid: 057f00df-1515-4c55-852a-d936c8a34b53
ms.openlocfilehash: bfc114a6e71c0eb0ae70005c2657871b6c9e9692
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74398113"
---
# <a name="model-32-bit-masm"></a>.MODEL (32-bit MASM)

初始化程序内存模型。 (32-bit MASM only.)

## <a name="syntax"></a>语法

> **.MODEL** *memory-model* ⟦ __,__ *language-type*⟧ ⟦ __,__ *stack-option*⟧

### <a name="parameters"></a>参数

*memory-model*\
必需参数，确定代码和数据指针的大小。

*language-type*\
可选参数，设置过程和公共符号的调用和命名约定。

*stack-option*\
可选参数。

*stack-option* is not used if *memory-model* is **FLAT**.

Specifying **NEARSTACK** groups the stack segment into a single physical segment (**DGROUP**) along with data. The stack segment register (**SS**) is assumed to hold the same address as the data segment register (**DS**). **FARSTACK** does not group the stack with **DGROUP**; thus **SS** does not equal **DS**.

## <a name="remarks"></a>备注

**.MODEL** is not used in [MASM for x64 (ml64.exe)](../../assembler/masm/masm-for-x64-ml64-exe.md).

下表列出了在面向 16 位和 32 位平台时每个参数的可能的值：

|参数|32 位值|16 位值（支持早期的 16 位开发）|
|---------------|--------------------|----------------------------------------------------------------|
|*memory-model*|**FLAT**|**TINY**, **SMALL**, **COMPACT**, **MEDIUM**, **LARGE**, **HUGE**, **FLAT**|
|*language-type*|**C**, **STDCALL**|**C**, **BASIC**, **FORTRAN**, **PASCAL**, **SYSCALL**, **STDCALL**|
|*stack-option*|未使用|**NEARSTACK**, **FARSTACK**|

## <a name="code"></a>代码

对于 MASM 的相关示例，可从 [Visual Studio 2010 的 Visual C++ 示例和相关文档](https://go.microsoft.com/fwlink/p/?linkid=178749)下载编译器示例。

下面的示例演示 `.MODEL` 指令的用法。

## <a name="example"></a>示例

```asm
; file simple.asm
; For x86 (32-bit), assemble with debug information:
;   ml -c -Zi simple.asm
; For x64 (64-bit), assemble with debug information:
;   ml64 -c -DX64 -Zi simple.asm
;
; In this sample, the 'X64' define excludes source not used
;  when targeting the x64 architecture

ifndef X64
.686p
.XMM
.model flat, C
endif

.data
; user data

.code
; user code

fxn PROC public
  xor eax, eax ; zero function return value
  ret
fxn ENDP

end
```

## <a name="see-also"></a>请参阅

[指令参考](../../assembler/masm/directives-reference.md)
