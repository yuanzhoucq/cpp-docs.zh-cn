---
title: /ERRORREPORT (editbin.exe)
description: Microsoft EDITBIN utility/ERRORREPORT 命令行选项的参考。
ms.date: 02/09/2020
f1_keywords:
- /ERRORREPORT_editbin
helpviewer_keywords:
- -ERRORREPORT editbin option
- ERRORREPORT editbin option
- /ERRORREPORT editbin option
ms.assetid: eca66ac3-b754-4bd7-9dd4-e04fc79a71b6
ms.openlocfilehash: 4456a49cc53b21bd24c616852159ca299181071b
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439899"
---
# <a name="errorreport-editbinexe"></a>/ERRORREPORT (editbin.exe)

> [!NOTE]
> /ERRORREPORT 选项已弃用。 从 Windows Vista 开始，错误报告由[Windows 错误报告（WER）](/windows/win32/wer/windows-error-reporting)设置控制。

## <a name="syntax"></a>语法

> **/ERRORREPORT** \[ **NONE** \| **PROMPT** \| **QUEUE** \| **SEND** ]

## <a name="remarks"></a>备注

**/ERRORREPORT**参数将被 Windows 错误报告服务设置重写。 如果 Windows 错误报告启用了报表，则 EDITBIN 会自动向 Microsoft 发送内部错误报表。 如果 Windows 错误报告禁用了报表，则不发送任何报表。

## <a name="see-also"></a>另请参阅

[EDITBIN 选项](editbin-options.md)
