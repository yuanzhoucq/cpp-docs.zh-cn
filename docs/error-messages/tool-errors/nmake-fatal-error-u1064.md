---
title: NMAKE 错误 U1064 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1064
dev_langs:
- C++
helpviewer_keywords:
- U1064
ms.assetid: 7141e66e-cde6-4173-84df-a391f3ebcdd1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4240bf2c553957e73d5ead0bdd03ea129450645b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46092987"
---
# <a name="nmake-fatal-error-u1064"></a>NMAKE 错误 U1064

未找到 MAKEFILE 并且未指定目标

NMAKE 命令行未指定生成文件或目标，并在当前目录不包含名为生成文件的文件。

NMAKE 需要生成文件或命令行目标 （或两者）。 若要使生成文件可供 NMAKE，请指定 /F 选项或将放置在当前目录中名为生成文件的文件。 NMAKE 可以通过使用推理规则，如果未提供生成文件创建命令行目标。