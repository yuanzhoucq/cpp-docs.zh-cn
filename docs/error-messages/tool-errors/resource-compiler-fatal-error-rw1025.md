---
title: 资源编译器错误 RW1025
ms.date: 11/04/2016
f1_keywords:
- RW1025
helpviewer_keywords:
- RW1025
ms.assetid: 561a02af-e7e0-442a-8ad3-a00b2ca1b62e
ms.openlocfilehash: 9b6697dff0a445cc342f30d08bd79822b02df7b8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172719"
---
# <a name="resource-compiler-fatal-error-rw1025"></a>资源编译器错误 RW1025

超出最大堆内存

检查可能占用过多空间的内存驻留软件。 使用 CHKDSK 程序来找出有多少内存。

如果要创建大资源文件，请将资源脚本拆分为两个文件。 创建两个 .res 文件后，使用 MS-DOS 命令行将它们联接在一起：

```
copy first.res /b + second.res /b full.res
```
