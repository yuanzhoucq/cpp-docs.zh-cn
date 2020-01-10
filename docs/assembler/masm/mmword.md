---
title: MMWORD
ms.date: 12/17/2019
f1_keywords:
- MMWORD
helpviewer_keywords:
- MMWORD directive
ms.assetid: b4c5a104-9078-4fb4-afc3-d1e63abe562a
ms.openlocfilehash: fd3b9f40b7ff9fa4dae570e0ed906c13a9456424
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2019
ms.locfileid: "75311918"
---
# <a name="mmword"></a>MMWORD

用于具有 MMX 和 SSE （XMM）说明的64位多媒体操作数。

## <a name="syntax"></a>语法

> **MMWORD**

## <a name="remarks"></a>备注

**MMWORD**是一种类型。  在将**MMWORD**添加到 MASM 之前，可通过以下方式实现等效功能：

```asm
    mov mm0, qword ptr [ebx]
```

尽管两个指令都适用于64位操作数，但**QWORD**是64位无符号整数的类型， **MMWORD**是64位多媒体值的类型。

**MMWORD**用于表示与[__m64](../../cpp/m64.md)相同的类型。

## <a name="example"></a>示例

```asm
    movq     mm0, mmword ptr [ebx]
```

## <a name="see-also"></a>请参阅

[MASM BNF 语法](masm-bnf-grammar.md)
