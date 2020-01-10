---
title: INVOKE
ms.date: 11/05/2019
f1_keywords:
- Invoke
helpviewer_keywords:
- INVOKE directive
ms.assetid: 12d9bb40-33b9-411e-b801-45a1d675967e
ms.openlocfilehash: 7a005e5e70a2696ca89fb0ad1a3ff02aab8ffe5a
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317183"
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
