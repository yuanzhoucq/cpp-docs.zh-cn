---
title: .DOSSEG | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .DOSSEG
dev_langs:
- C++
helpviewer_keywords:
- .DOSSEG directive
ms.assetid: 175ad470-0a2b-4e2b-b078-65e224fec040
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 33ee0b0b049ece65786c4d4857c2e082a067fee4
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2018
ms.locfileid: "43693227"
---
# <a name="dosseg"></a>.DOSSEG

根据 MS-DOS 段约定的段进行排序： 代码首先，然后段不在 DGROUP，并在 DGROUP 然后细分。

## <a name="syntax"></a>语法

> .DOSSEG

## <a name="remarks"></a>备注

DGROUP 中的各段遵循此顺序： 段不在 BSS 或堆栈，然后 BSS 线段和最后的堆栈段。 主要用于确保 MASM 的独立程序中的 CodeView 支持。 与相同[DOSSEG](../../assembler/masm/dosseg.md)。

## <a name="see-also"></a>请参阅

[指令参考](../../assembler/masm/directives-reference.md)<br/>