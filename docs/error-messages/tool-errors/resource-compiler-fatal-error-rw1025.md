---
title: 资源编译器错误 RW1025
ms.date: 11/04/2016
f1_keywords:
- RW1025
helpviewer_keywords:
- RW1025
ms.assetid: 561a02af-e7e0-442a-8ad3-a00b2ca1b62e
ms.openlocfilehash: 8ecfc11f5cc991294d966a4b6c75d8da6669d5b1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50575677"
---
# <a name="resource-compiler-fatal-error-rw1025"></a>资源编译器错误 RW1025

远端的堆内存不足

检查可能会占用太多的空间驻留在内存中的软件。 使用 CHKDSK 程序若要了解有多少内存。

如果要创建一个大型资源文件，将资源脚本拆分为两个文件中。 在创建后两个.res 文件，使用 MS-DOS 命令行来将其联接起来：

```
copy first.res /b + second.res /b full.res
```