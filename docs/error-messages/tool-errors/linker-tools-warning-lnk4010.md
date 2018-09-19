---
title: 链接器工具警告 LNK4010 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4010
dev_langs:
- C++
helpviewer_keywords:
- LNK4010
ms.assetid: 2824cf99-4174-4b60-a6e2-c01e9f1ee52d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e214f603c31c72533d81a140023363880532191c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46068060"
---
# <a name="linker-tools-warning-lnk4010"></a>链接器工具警告 LNK4010

无效的子系统版本编号;假定为默认子系统版本

可以指定图像的子系统的版本 ([/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md))。 每个子系统具有最低版本要求。 如果指定的版本低于最小值，将出现此警告和链接器将仅使用默认子系统。