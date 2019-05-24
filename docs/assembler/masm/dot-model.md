---
title: .MODEL
ms.date: 08/30/2018
f1_keywords:
- .MODEL
helpviewer_keywords:
- .MODEL directive
ms.assetid: 057f00df-1515-4c55-852a-d936c8a34b53
ms.openlocfilehash: c409bf10a2f863c380cda6b4822583ffb3787da6
ms.sourcegitcommit: 61121faf879cc581a4d39e4baccabf7cf1f673a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/20/2019
ms.locfileid: "65934100"
---
# <a name="model"></a>.MODEL

初始化程序内存模型。

## <a name="syntax"></a>语法

> .MODEL memorymodel [[, langtype]] [[, stackoption]]

### <a name="parameters"></a>参数

memorymodel<br/>
必需参数，确定代码和数据指针的大小。

langtype<br/>
可选参数，设置过程和公共符号的调用和命名约定。

stackoption<br/>
可选参数。

如果 memorymodel 为 `FLAT`，则不使用 stackoption。

指定 `NEARSTACK` 将堆栈段以及数据组合至单个物理段 (`DGROUP`)。 假定堆栈段寄存器 (`SS`) 与数据段寄存器 (`DS`) 保留相同的地址。 `FARSTACK` 不会将堆栈与 `DGROUP` 组合；因此，`SS` 不等于 `DS`。

## <a name="remarks"></a>备注

.`MODEL` 不在 [x64 的 MASM (ml64.exe)](../../assembler/masm/masm-for-x64-ml64-exe.md) 中使用。

下表列出了在面向 16 位和 32 位平台时每个参数的可能的值：

|参数|32 位值|16 位值（支持早期的 16 位开发）|
|---------------|--------------------|----------------------------------------------------------------|
|memorymodel|`FLAT`|`TINY`, `SMALL`, `COMPACT`, `MEDIUM`, `LARGE`, `HUGE`, `FLAT`|
|langtype|`C`， `STDCALL`|`C`, `BASIC`, `FORTRAN`, `PASCAL`, `SYSCALL`, `STDCALL`|
|stackoption|未使用|`NEARSTACK`， `FARSTACK`|

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

[指令参考](../../assembler/masm/directives-reference.md)<br/>
