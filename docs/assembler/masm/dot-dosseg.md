---
title: .DOSSEG
ms.date: 11/05/2019
f1_keywords:
- .DOSSEG
helpviewer_keywords:
- .DOSSEG directive
ms.assetid: 175ad470-0a2b-4e2b-b078-65e224fec040
ms.openlocfilehash: e27b0ae185542c11ee29119575d5c8225501f71e
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2019
ms.locfileid: "75313842"
---
# <a name="dosseg-32-bit-masm"></a>..DOSSEG （32）

根据 MS-DOS 段约定对段进行排序：代码优先，然后是不在 DGROUP 中的段，然后是 DGROUP 中的段。 （仅限32位 MASM。）

## <a name="syntax"></a>语法

> **.DOSSEG**

## <a name="remarks"></a>备注

DGROUP 中的段遵循以下顺序：段不在 BSS 或 STACK 中，然后是 BSS 段，最后是堆栈段。 主要用于确保 MASM 独立程序中的 CodeView 支持。 与[.dosseg](dosseg.md)相同。

## <a name="see-also"></a>另请参阅

[指令引用](directives-reference.md)\
[MASM BNF 语法](masm-bnf-grammar.md)
