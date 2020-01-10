---
title: .STACK
ms.date: 11/05/2019
f1_keywords:
- .STACK
helpviewer_keywords:
- .STACK directive
ms.assetid: 70019463-5d4f-41b6-8464-023a8ac2466f
ms.openlocfilehash: 4dd45a0705b729e65bb413fc02671f86e5f9105b
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2019
ms.locfileid: "75318223"
---
# <a name="stack-32-bit-masm"></a>.STACK （32位 MASM）

与一起使用时[。模型](dot-model.md)，定义堆栈段（带有分段名称**stack**）。 可选*大小*为堆栈指定字节数（默认值为1024）。 **。STACK**指令自动关闭 stack 语句。 （仅限32位 MASM。）

## <a name="syntax"></a>语法

> **.STACK** ⟦*size*⟧

## <a name="see-also"></a>另请参阅

[指令引用](directives-reference.md)\
[MASM BNF 语法](masm-bnf-grammar.md)
