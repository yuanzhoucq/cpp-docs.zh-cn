---
title: .DOSSEG
ms.date: 08/30/2018
f1_keywords:
- .DOSSEG
helpviewer_keywords:
- .DOSSEG directive
ms.assetid: 175ad470-0a2b-4e2b-b078-65e224fec040
ms.openlocfilehash: 28b3e351030ee83693c0fec5568aacf9b4b77c27
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62204356"
---
# <a name="dosseg"></a>.DOSSEG

根据 MS-DOS 段约定的段进行排序：代码优先，然后不在 DGROUP，段，然后 DGROUP 中的段。

## <a name="syntax"></a>语法

> .DOSSEG

## <a name="remarks"></a>备注

DGROUP 中的各段遵循此顺序： 段不在 BSS 或堆栈，然后 BSS 线段和最后的堆栈段。 主要用于确保 MASM 的独立程序中的 CodeView 支持。 与相同[DOSSEG](../../assembler/masm/dosseg.md)。

## <a name="see-also"></a>请参阅

[指令参考](../../assembler/masm/directives-reference.md)<br/>