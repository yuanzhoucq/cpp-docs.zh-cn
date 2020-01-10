---
title: MACRO
ms.date: 12/16/2019
f1_keywords:
- MACRO
helpviewer_keywords:
- MACRO directive
ms.assetid: 89434f7c-bc2c-4e91-8940-fe2db8785233
ms.openlocfilehash: 23c6b0aefae856da449da574669e8475122c7556
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2019
ms.locfileid: "75312945"
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

