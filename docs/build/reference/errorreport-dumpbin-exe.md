---
title: /ERRORREPORT (dumpbin.exe)
description: Microsoft DUMPBIN utility/ERRORREPORT 命令行选项的参考。
ms.date: 02/09/2020
f1_keywords:
- /ERRORREPORT_dumpbin
helpviewer_keywords:
- -ERRORREPORT dumpbin option
- ERRORREPORT dumpbin option
- /ERRORREPORT dumpbin option
ms.assetid: 51178c43-4f95-4fda-8f97-50a257d1c948
ms.openlocfilehash: f701c2e28dcf82194589877709bf6959de4bcbfc
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439937"
---
# <a name="errorreport-dumpbinexe"></a>/ERRORREPORT (dumpbin.exe)

> [!NOTE]
> /ERRORREPORT 选项已弃用。 从 Windows Vista 开始，错误报告由[Windows 错误报告（WER）](/windows/win32/wer/windows-error-reporting)设置控制。

## <a name="syntax"></a>语法

> **/ERRORREPORT**\[**NONE** \| **PROMPT** \| **QUEUE** \| **SEND** ]

## <a name="remarks"></a>备注

**/ERRORREPORT**参数将被 Windows 错误报告服务设置重写。 如果 Windows 错误报告启用了报表，则 DUMPBIN 会自动向 Microsoft 发送内部错误报表。 如果 Windows 错误报告禁用了报表，则不发送任何报表。

## <a name="see-also"></a>另请参阅

[DUMPBIN 选项](dumpbin-options.md)
