---
title: MACRO
ms.date: 12/16/2019
f1_keywords:
- MACRO
helpviewer_keywords:
- MACRO directive
ms.assetid: 89434f7c-bc2c-4e91-8940-fe2db8785233
ms.openlocfilehash: 8eb0afdf73270c3e741f43b2e1fba02fe965846c
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076138"
---
# <a name="macro"></a>MACRO

标记名为*name*的宏块，并为调用宏时传递的参数建立*参数*占位符。

## <a name="syntax"></a>语法

> *name***宏**⟦*参数*⟦ **：** 请求 |： =*default* | *args* **： VARARG**⟧ .。。⟧\
> *语句*\
⟦**GOTO** ：*macrolabelId*⟧ \
> ⟦**EXITM**⟧ \
> **ENDM** ⟦*value*⟧

## <a name="remarks"></a>备注

宏函数将*值*返回给调用语句。

## <a name="see-also"></a>另请参阅

[指令引用](directives-reference.md)\
[GOTO （MASM）](goto-masm.md)\
[ENDM](endm.md)\
[MASM BNF 语法](masm-bnf-grammar.md)
