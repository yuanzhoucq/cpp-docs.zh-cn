---
title: /INTEGRITYCHECK |Microsoft 文档
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
ms.openlocfilehash: 4b0adf9add2d191ae89aec0a5d756ade8e9f7725
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32370243"
---
# <a name="integritycheck"></a>/INTEGRITYCHECK

指定必须在加载时检查数字签名的二进制映像。

> **/INTEGRITYCHECK**[**： 否**]

## <a name="remarks"></a>备注

中的 DLL 文件或可执行文件的标头，此选项设置一个标志，需要通过要加载的映像在 Windows 中的内存管理器进行数字签名检查。 Windows Vista 之前的 Windows 版本忽略此标志。 必须为实现内核模式代码中，并且建议对所有设备驱动程序的 64 位 Dll 设置此选项。 有关详细信息，请参阅[内核模式代码签名需求](/windows-hardware/drivers/install/kernel-mode-code-signing-requirements--windows-vista-and-later-)。

## <a name="see-also"></a>请参阅

[EDITBIN 选项](../../build/reference/editbin-options.md)  
