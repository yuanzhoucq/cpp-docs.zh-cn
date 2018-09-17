---
title: /INTEGRITYCHECK |Microsoft Docs
ms.custom: ''
ms.date: 12/28/2017
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /INTEGRITYCHECK
dev_langs:
- C++
helpviewer_keywords:
- -INTEGRITYCHECK editbin options
- /INTEGRITYCHECK editbin options
- INTEGRITYCHECK editbin options
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 062ce019fe1b622661be880d8a06eac9c5971103
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45709198"
---
# <a name="integritycheck"></a>/INTEGRITYCHECK

指定必须在加载时检查数字签名的二进制图像。

> **/INTEGRITYCHECK**[**： 否**]

## <a name="remarks"></a>备注

在 DLL 文件或可执行文件的标题中，此选项设置一个标志，需要由内存管理器以在 Windows 中的将图像加载数字签名检查。 在 Windows Vista 之前的 Windows 版本忽略此标志。 必须为实现内核模式代码，并且建议对所有设备驱动程序的 64 位 Dll 设置此选项。 有关详细信息，请参阅[内核模式代码签名要求](/windows-hardware/drivers/install/kernel-mode-code-signing-requirements--windows-vista-and-later-)。

## <a name="see-also"></a>请参阅

[EDITBIN 选项](../../build/reference/editbin-options.md)
