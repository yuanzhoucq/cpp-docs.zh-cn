---
title: .DOSSEG
ms.date: 11/05/2019
f1_keywords:
- .DOSSEG
helpviewer_keywords:
- .DOSSEG directive
ms.assetid: 175ad470-0a2b-4e2b-b078-65e224fec040
ms.openlocfilehash: 8f0388c3df9804c0cdb105162a962a44fe207345
ms.sourcegitcommit: 45f1d889df633f0f7e4a8e813b46fa73c9858b81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/06/2019
ms.locfileid: "73703308"
---
# <a name="dosseg-32-bit-masm"></a>..DOSSEG （32）

根据 MS-DOS 段约定对段进行排序：代码优先，然后是不在 DGROUP 中的段，然后是 DGROUP 中的段。 （仅限32位 MASM。）

## <a name="syntax"></a>语法

> .DOSSEG

## <a name="remarks"></a>备注

DGROUP 中的段遵循以下顺序：段不在 BSS 或 STACK 中，然后是 BSS 段，最后是堆栈段。 主要用于确保 MASM 独立程序中的 CodeView 支持。 与[.dosseg](../../assembler/masm/dosseg.md)相同。

## <a name="see-also"></a>请参阅

[指令参考](../../assembler/masm/directives-reference.md)<br/>