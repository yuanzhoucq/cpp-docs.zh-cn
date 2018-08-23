---
title: .MODEL | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .MODEL
dev_langs:
- C++
helpviewer_keywords:
- .MODEL directive
ms.assetid: 057f00df-1515-4c55-852a-d936c8a34b53
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2814b1b6cc4483807f77989ff4fbb70929400d6e
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2018
ms.locfileid: "32057742"
---
# <a name="model"></a>.MODEL
初始化程序内存模型。  
  
## <a name="syntax"></a>语法  
  
```  
.MODEL memorymodel [[, langtype]] [[, stackoption]]  
```  
  
#### <a name="parameters"></a>参数  
 `memorymodel`  
 确定代码和数据的指针的大小的必选的参数。  
  
 `langtype`  
 设置过程和公共符号的调用和命名约定的可选参数。  
  
 `stackoption`  
 可选参数。  
  
 `stackoption` 如果不使用`memorymodel`是`FLAT`。  
  
 指定`NEARSTACK`分组到单个物理网段的堆栈段 (`DGROUP`) 以及数据。 堆栈段寄存器 (`SS`) 假定来保存的数据段寄存器与相同的地址 (`DS`)。 `FARSTACK` 非组与堆栈`DGROUP`; 因此`SS`不等于`DS`。  
  
## <a name="remarks"></a>备注  
 .`MODEL` 中不使用[x64 (ml64.exe) 的 MASM](../../assembler/masm/masm-for-x64-ml64-exe.md)。  
  
 当目标为 16 位和 32 位平台时下, 表列出每个参数的可能值：  
  
|参数|32 位值|16 位值 （用于更早版本的 16 位开发的支持）|  
|---------------|--------------------|----------------------------------------------------------------|  
|`memorymodel`|`FLAT`|`TINY`, `SMALL`, `COMPACT`, `MEDIUM`, `LARGE`, `HUGE`, `FLAT`|  
|`langtype`|`C`, `STDCALL`|`C`, `BASIC`, `FORTRAN`, `PASCAL`, `SYSCALL`, `STDCALL`|  
|`stackoption`|未使用|`NEARSTACK`, `FARSTACK`|  
  
## <a name="code"></a>代码  
 有关 MASM 相关示例，下载从编译器示例[Visual c + + 示例和相关文档 Visual Studio 2010](http://go.microsoft.com/fwlink/p/?linkid=178749)。  
  
 下面的示例演示了利用`.MODEL`指令。  
  
## <a name="example"></a>示例  
  
```  
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
 [指令引用](../../assembler/masm/directives-reference.md)   
 [Visual c + + 示例和 Visual Studio 2010 的相关的文档](http://go.microsoft.com/fwlink/p/?linkid=178749)