---
title: PROTO |Microsoft Docs
ms.custom: ''
ms.date: 10/22/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- PROTO
dev_langs:
- C++
helpviewer_keywords:
- PROTO directive
ms.assetid: 0487ee16-9dc7-43d1-9445-cd1601f5a080
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4fd00263f3b4a7ffcf23ccd0501989c0d40c637d
ms.sourcegitcommit: f3a5dc788e62bb36e2d9bc3e62e0aa533422408b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/23/2018
ms.locfileid: "49644058"
---
# <a name="proto"></a>PROTO

原型的函数或过程。 您可以通过调用函数原型 PROTO 指令使用[INVOKE](invoke.md)指令。

## <a name="syntax"></a>语法

> *标签* **PROTO** \[*距离*] \[ *langtype*] \[ __，__ \[*参数*]__:__*标记*]...

### <a name="parameters"></a>参数

*标签*<br/>
原型的函数的名称。

*distance*<br/>
（可选）在 16 位内存模型中使用可重写默认值，并指示**NEAR**或**FAR**调用。

*langtype*<br/>
（可选）设置过程和公共符号的调用和命名约定。 受支持的约定如下：

- 32 位**平面**模型： **C**， **STDCALL**

- 16 位模型： **C**， **BASIC**， **FORTRAN**， **PASCAL**， **SYSCALL**， **STDCALL**

*parameter*<br/>
函数参数的可选名称。

*标记*<br/>
函数参数的类型。

*参数*并*标记*参数可能会出现多次，一次为每个传递的参数。

## <a name="example"></a>示例

此示例演示**PROTO**声明一个名为函数`addup3`，它使用**NEAR**调用重写的 16 位模型默认值为过程调用，并使用**C**调用约定的 stack 参数和返回值。 它采用两个参数， **WORD**和一个**VARARG**。

```MASM
addup3 PROTO NEAR C, argcount:WORD, arg1:VARARG
```

## <a name="see-also"></a>请参阅

[指令参考](directives-reference.md)<br/>
[.模型引用](dot-model.md)<br/>
