---
title: LOCAL (MASM)
ms.date: 12/16/2019
f1_keywords:
- Local
helpviewer_keywords:
- LOCAL directive
ms.assetid: 76147e2d-23ca-4f1e-8817-81428becd113
ms.openlocfilehash: 2bef6b26f1b922be6512bd6ebe8e0b2627e86f45
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317144"
---
# <a name="local"></a>LOCAL

在第一个指令中，在宏内，**本地**定义宏的每个实例特有的标签。

## <a name="syntax"></a>语法

> **LOCAL** *LocalId* ⟦， *localId* .。。⟧
>
> **LOCAL** *面部*⟦ __\[__ *count* __]__ ⟧⟦ __：__ *qualifiedType*⟧⟦ __，__ *面部*⟦ __\[__ *count* __]__ *⟧⟦ qualifiedType ⟧ ...* ⟧

## <a name="remarks"></a>备注

在第二个指令中，在过程定义（**PROC**）内，**本地**创建在过程中存在的基于堆栈的变量。 *面部*可以是一个简单变量或包含*count*元素的数组，其中*count*是一个常量表达式。

## <a name="see-also"></a>另请参阅

[指令引用](directives-reference.md)\
[MASM BNF 语法](masm-bnf-grammar.md)
