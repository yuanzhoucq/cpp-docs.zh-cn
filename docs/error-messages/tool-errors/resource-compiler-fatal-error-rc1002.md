---
title: 资源编译器错误 RC1002 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC1002
dev_langs:
- C++
helpviewer_keywords:
- RC1002
ms.assetid: b43dfece-0dc3-4d0b-9d8f-509699b9ae80
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8d54f49b7cce988c5902a01142efe061ba03e424
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46114522"
---
# <a name="resource-compiler-fatal-error-rc1002"></a>资源编译器错误 RC1002

堆空间不足

### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用以下可能的解决方案进行修复

1. 增加 Windows 交换文件空间。 有关增加交换文件空间的详细信息，请参阅 Windows 帮助中的虚拟内存。

1. 将当前文件拆分成较小的文件并将其单独编译。

1. 删除其他程序或驱动程序在系统上运行。