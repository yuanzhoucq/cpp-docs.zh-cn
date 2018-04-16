---
title: "/INTEGRITYCHECK |Microsoft 文档"
ms.custom: 
ms.date: 12/28/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
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
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 99caec18162a7506b8b7a467eb7374b6fe4a38d9
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/03/2018
---
# <a name="integritycheck"></a>/INTEGRITYCHECK

指定必须在加载时检查数字签名的二进制映像。

> **/INTEGRITYCHECK**[**： 否**]

## <a name="remarks"></a>备注

中的 DLL 文件或可执行文件的标头，此选项设置一个标志，需要通过要加载的映像在 Windows 中的内存管理器进行数字签名检查。 Windows Vista 之前的 Windows 版本忽略此标志。 必须为实现内核模式代码中，并且建议对所有设备驱动程序的 64 位 Dll 设置此选项。 有关详细信息，请参阅[内核模式代码签名需求](/windows-hardware/drivers/install/kernel-mode-code-signing-requirements--windows-vista-and-later-)。

## <a name="see-also"></a>请参阅

[EDITBIN 选项](../../build/reference/editbin-options.md)  
