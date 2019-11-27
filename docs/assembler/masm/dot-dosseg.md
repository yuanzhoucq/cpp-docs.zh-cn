---
title: .DOSSEG
ms.date: 11/05/2019
f1_keywords:
- .DOSSEG
helpviewer_keywords:
- .DOSSEG directive
ms.assetid: 175ad470-0a2b-4e2b-b078-65e224fec040
ms.openlocfilehash: 17edea122afc03a8c3a2fdc86ee6c06c2ccf3c85
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74398491"
---
# <a name="dosseg-32-bit-masm"></a>..DOSSEG （32）

根据 MS-DOS 段约定对段进行排序：代码优先，然后是不在 DGROUP 中的段，然后是 DGROUP 中的段。 （仅限32位 MASM。）

## <a name="syntax"></a>语法

> **.DOSSEG**

## <a name="remarks"></a>备注

DGROUP 中的段遵循以下顺序：段不在 BSS 或 STACK 中，然后是 BSS 段，最后是堆栈段。 主要用于确保 MASM 独立程序中的 CodeView 支持。 与[.dosseg](../../assembler/masm/dosseg.md)相同。

## <a name="see-also"></a>另请参阅

[指令参考](../../assembler/masm/directives-reference.md)
