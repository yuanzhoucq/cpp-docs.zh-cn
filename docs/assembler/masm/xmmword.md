---
title: XMMWORD
ms.date: 12/17/2019
f1_keywords:
- XMMWORD
helpviewer_keywords:
- XMMWORD directive
ms.assetid: 18026d32-5cab-403e-ad7e-382fb41aa9b8
ms.openlocfilehash: 1116729883bf9b1b9342b30332bab5de6ba59015
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2019
ms.locfileid: "75319107"
---
# <a name="xmmword"></a>XMMWORD

用于具有 MMX 和 SSE （XMM）说明的128位多媒体操作数。

## <a name="syntax"></a>语法

> **XMMWORD**

## <a name="remarks"></a>备注

**XMMWORD**用于表示与[__m128](../../cpp/m128.md)相同的类型。

## <a name="example"></a>示例

```asm
    movdqa   xmm0, xmmword ptr [ebx]
```

## <a name="see-also"></a>请参阅

[MASM BNF 语法](masm-bnf-grammar.md)
