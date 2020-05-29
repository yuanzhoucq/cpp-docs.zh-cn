---
title: INVOKE
ms.date: 11/05/2019
f1_keywords:
- Invoke
helpviewer_keywords:
- INVOKE directive
ms.assetid: 12d9bb40-33b9-411e-b801-45a1d675967e
ms.openlocfilehash: ba1377359ba9bc960e5d7d2a55df15adfe0d5d33
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076225"
---
# <a name="invoke"></a>INVOKE

（仅限32位 MASM。）调用由*expression*给定的地址处的过程，并根据语言类型的标准调用约定在堆栈上或在寄存器中传递参数。

## <a name="syntax"></a>语法

> **调用** *expression* ⟦ __，__ *argument* .。。⟧

## <a name="remarks"></a>备注

传递给过程的每个参数可以是表达式、寄存器对或地址表达式（前面**是地址的表达式）。**

## <a name="see-also"></a>另请参阅

[指令引用](directives-reference.md)\
[MASM BNF 语法](masm-bnf-grammar.md)
