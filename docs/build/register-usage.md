---
title: 注册用量 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: ce58e2cf-afd3-4068-980e-28a209298265
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4c77469a8cef03827101f4bf367c00a3bb440820
ms.sourcegitcommit: 4fc6869067d533b175207befd2dc60346afee285
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
---
# <a name="register-usage"></a>寄存器用法

X64 体系结构提供了 16 个通用寄存器 （以后称为整数寄存器），以及 16 XMM/YMM 寄存器可供浮点使用。 易失寄存器是由调用方假想的临时寄存器，并要在调用过程中销毁。 非易失寄存器需要在整个函数调用过程中保留其值，并且一旦使用，则必须由被调用方保存。

## <a name="register-volatility-and-preservation"></a>注册更新率和保留

下表说明了每种寄存器在整个函数调用过程中的使用方法：

||||
|-|-|-|
|寄存器|状态|使用|
|RAX|易失的|返回值寄存器|
|RCX|易失的|第一个整型参数|
|RDX|易失的|第二个整型参数|
|R8|易失的|第三个整型参数|
|R9|易失的|第四个整型参数|
|R10:R11|易失的|必须根据需要由调用方保留；在 syscall/sysret 指令中使用|
|R12:R15|非易失的|必须由被调用方保留|
|RDI|非易失的|必须由被调用方保留|
|RSI|非易失的|必须由被调用方保留|
|RBX|非易失的|必须由被调用方保留|
|RBP|非易失的|可用作帧指针；必须由被调用方保留|
|RSP|非易失的|堆栈指针|
|XMM0、YMM0|易失的|第一个 FP 参数；使用 `__vectorcall` 时的第一个矢量类型参数|
|XMM1、YMM1|易失的|第二个 FP 参数；使用 `__vectorcall` 时的第二个矢量类型参数|
|XMM2、YMM2|易失的|第三个 FP 参数；使用 `__vectorcall` 时的第三个矢量类型参数|
|XMM3、YMM3|易失的|第四个 FP 参数；使用 `__vectorcall` 时的第四个矢量类型参数|
|XMM4、YMM4|易失的|必须根据需要由调用方保留；使用 `__vectorcall` 时的第五个矢量类型参数|
|XMM5、YMM5|易失的|必须根据需要由调用方保留；使用 `__vectorcall` 时的第六个矢量类型参数|
|XMM6:XMM15、YMM6:YMM15|非易失的 (XMM)，易失的（YMM 的上半部分）|必须由被调用方保留。 YMM 寄存器必须根据需要由调用方保留。|

在函数退出和函数进入的 C 运行库调用和 Windows 系统调用中 CPU, 的方向标志标志注册需要清除。

## <a name="see-also"></a>请参阅

- [x64 软件约定](../build/x64-software-conventions.md)
- [__vectorcall](../cpp/vectorcall.md)
- [方向标志](../c-runtime-library/direction-flag.md)
