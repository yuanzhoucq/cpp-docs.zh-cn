---
title: 资源编译器错误 RW1022
ms.date: 11/04/2016
f1_keywords:
- RW1022
helpviewer_keywords:
- RW1022
ms.assetid: 6747c8a9-9c9b-4422-b414-0645d22092d0
ms.openlocfilehash: 896eac8bcc59ef84dc1437fba00c42c6c9304bed
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172745"
---
# <a name="resource-compiler-fatal-error-rw1022"></a>资源编译器错误 RW1022

**写入文件时出现 i/o 错误**

资源编译器无法写入文件。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复

1. 磁盘空间不足。 可用空间必须至少等于正在创建的可执行文件大小的两倍。

1. 卷只读。

1. 坏扇区。

1. 共享冲突。
