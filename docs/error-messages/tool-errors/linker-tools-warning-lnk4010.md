---
title: 链接器工具警告 LNK4010
ms.date: 11/04/2016
f1_keywords:
- LNK4010
helpviewer_keywords:
- LNK4010
ms.assetid: 2824cf99-4174-4b60-a6e2-c01e9f1ee52d
ms.openlocfilehash: 3f25c9194f48df4064282fb8601928b3ff00f40e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410313"
---
# <a name="linker-tools-warning-lnk4010"></a>链接器工具警告 LNK4010

无效的子系统版本编号;假定为默认子系统版本

可以指定图像的子系统的版本 ([/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md))。 每个子系统具有最低版本要求。 如果指定的版本低于最小值，将出现此警告和链接器将仅使用默认子系统。