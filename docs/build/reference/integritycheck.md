---
title: /INTEGRITYCHECK
ms.date: 12/28/2017
f1_keywords:
- /INTEGRITYCHECK
helpviewer_keywords:
- -INTEGRITYCHECK editbin options
- /INTEGRITYCHECK editbin options
- INTEGRITYCHECK editbin options
ms.openlocfilehash: 4174e22dcdadb3b3319998614285c13741fe3a88
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62269760"
---
# <a name="integritycheck"></a>/INTEGRITYCHECK

指定必须在加载时检查数字签名的二进制图像。

> **/INTEGRITYCHECK**[**:NO**]

## <a name="remarks"></a>备注

在 DLL 文件或可执行文件的标题中，此选项设置一个标志，需要由内存管理器以在 Windows 中的将图像加载数字签名检查。 在 Windows Vista 之前的 Windows 版本忽略此标志。 必须为实现内核模式代码，并且建议对所有设备驱动程序的 64 位 Dll 设置此选项。 有关详细信息，请参阅[内核模式代码签名要求](/windows-hardware/drivers/install/kernel-mode-code-signing-requirements--windows-vista-and-later-)。

## <a name="see-also"></a>请参阅

[EDITBIN 选项](editbin-options.md)
