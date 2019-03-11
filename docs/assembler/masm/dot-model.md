---
title: .MODEL
ms.date: 08/30/2018
f1_keywords:
- .MODEL
helpviewer_keywords:
- .MODEL directive
ms.assetid: 057f00df-1515-4c55-852a-d936c8a34b53
ms.openlocfilehash: c3917fea0f13e54d5f8f73599a2d28482bb6d259
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/11/2019
ms.locfileid: "57743933"
---
# <a name="model"></a>.MODEL

初始化程序内存模型。

## <a name="syntax"></a>语法

> .模型 memorymodel [[，langtype]] [[，stackoption]]

### <a name="parameters"></a>参数

*memorymodel*<br/>
必需的参数，它确定的代码和数据的指针的大小。

*langtype*<br/>
设置过程和公共符号的调用和命名约定的可选参数。

*stackoption*<br/>
可选参数。

*stackoption*如果不使用*memorymodel*是`FLAT`。

指定`NEARSTACK`组合到单个物理网段堆栈段 (`DGROUP`) 以及数据。 堆栈段寄存器 (`SS`) 假定用于保存数据段注册相同的地址 (`DS`)。 `FARSTACK` 非组与堆栈`DGROUP`; 因此`SS`不等于`DS`。

## <a name="remarks"></a>备注

.`MODEL` 中不使用[MASM 的 x64 (ml64.exe)](../../assembler/masm/masm-for-x64-ml64-exe.md)。

面向 16 位和 32 位平台时下, 表列出了每个参数的可能值：

|参数|32 位值|16 位值 （支持早期的 16 位开发）|
|---------------|--------------------|----------------------------------------------------------------|
|*memorymodel*|`FLAT`|`TINY`, `SMALL`, `COMPACT`, `MEDIUM`, `LARGE`, `HUGE`, `FLAT`|
|*langtype*|`C`， `STDCALL`|`C`, `BASIC`, `FORTRAN`, `PASCAL`, `SYSCALL`, `STDCALL`|
|*stackoption*|未使用|`NEARSTACK`， `FARSTACK`|

## <a name="code"></a>代码

MASM 相关的示例，用于下载从编译器示例[Visual c + + 示例和相关文档的 Visual Studio 2010](http://go.microsoft.com/fwlink/p/?linkid=178749)。

下面的示例演示如何将`.MODEL`指令。

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

[指令参考](../../assembler/masm/directives-reference.md)<br/>
