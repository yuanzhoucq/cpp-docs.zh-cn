---
title: 运行 NMAKE |Microsoft Docs
ms.custom: ''
ms.date: 09/05/2018
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- targets, building
- response files, NMAKE
- targets
- command files
- NMAKE program, targets
- NMAKE program, running
- command files, NMAKE
ms.assetid: 0421104d-8b7b-4bf3-86c1-928d9b7c1a8c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bdc9d89dbc0e77a8002cc34e5d010ee49d761da4
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45706688"
---
# <a name="running-nmake"></a>运行 NMAKE

## <a name="syntax"></a>语法

> **NMAKE** [*选项*...][*宏*...][*目标*...][**\@**<em>commandfile</em> ...]

## <a name="remarks"></a>备注

仅在指定的 NMAKE 生成*目标*或如果未指定，第一个目标中生成文件。 第一个生成文件目标可以是[伪目标](../build/pseudotargets.md)生成其他目标。 NMAKE 使用 /F; 使用指定的生成文件如果未指定 /F，它使用当前目录中的生成文件文件。 如果指定了不到生成文件，它使用推理规则来生成命令行*目标*。

*Commandfile*文本文件 （或响应文件） 包含命令行输入。 其他输入可以前面或后面\@ *commandfile*。 允许的路径。 在中*commandfile*，换行被视为空格。 宏定义用引号引起来，如果它们包含空格。

## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

[NMAKE 选项](../build/nmake-options.md)

[Tools.ini 和 NMake](../build/tools-ini-and-nmake.md)

[从 NMAKE 退出代码](../build/exit-codes-from-nmake.md)

## <a name="see-also"></a>请参阅

[NMAKE 参考](../build/nmake-reference.md)