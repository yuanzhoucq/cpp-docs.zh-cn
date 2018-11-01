---
title: /INTEGRITYCHECK
ms.date: 12/28/2017
f1_keywords:
- /INTEGRITYCHECK
helpviewer_keywords:
- -INTEGRITYCHECK editbin options
- /INTEGRITYCHECK editbin options
- INTEGRITYCHECK editbin options
ms.openlocfilehash: b3f6622e3628db53c363b239c59accd94f708ab0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50617264"
---
# <a name="integritycheck"></a>/INTEGRITYCHECK

指定必须在加载时检查数字签名的二进制图像。

> **/INTEGRITYCHECK**[**： 否**]

## <a name="remarks"></a>备注

在 DLL 文件或可执行文件的标题中，此选项设置一个标志，需要由内存管理器以在 Windows 中的将图像加载数字签名检查。 在 Windows Vista 之前的 Windows 版本忽略此标志。 必须为实现内核模式代码，并且建议对所有设备驱动程序的 64 位 Dll 设置此选项。 有关详细信息，请参阅[内核模式代码签名要求](/windows-hardware/drivers/install/kernel-mode-code-signing-requirements--windows-vista-and-later-)。

## <a name="see-also"></a>请参阅

[EDITBIN 选项](../../build/reference/editbin-options.md)
