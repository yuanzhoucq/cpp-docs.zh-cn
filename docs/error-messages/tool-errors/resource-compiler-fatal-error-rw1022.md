---
title: 资源编译器错误 RW1022
ms.date: 11/04/2016
f1_keywords:
- RW1022
helpviewer_keywords:
- RW1022
ms.assetid: 6747c8a9-9c9b-4422-b414-0645d22092d0
ms.openlocfilehash: 8065745c85d0552687e77f4d901adce6d1b130c7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62347215"
---
# <a name="resource-compiler-fatal-error-rw1022"></a>资源编译器错误 RW1022

**写入文件时出现 I/O 错误**

资源编译器无法写入文件。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复

1. 磁盘空间不足。 可用空间必须等于正在创建的可执行文件的大小的至少两倍。

1. 卷为只读。

1. 坏扇区。

1. 共享冲突。