---
title: NMAKE 错误 U1064
ms.date: 11/04/2016
f1_keywords:
- U1064
helpviewer_keywords:
- U1064
ms.assetid: 7141e66e-cde6-4173-84df-a391f3ebcdd1
ms.openlocfilehash: 71213391032989e5faf8889761b29194928125a0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62367403"
---
# <a name="nmake-fatal-error-u1064"></a>NMAKE 错误 U1064

未找到 MAKEFILE 并且未指定目标

NMAKE 命令行未指定生成文件或目标，并在当前目录不包含名为生成文件的文件。

NMAKE 需要生成文件或命令行目标 （或两者）。 若要使生成文件可供 NMAKE，请指定 /F 选项或将放置在当前目录中名为生成文件的文件。 NMAKE 可以通过使用推理规则，如果未提供生成文件创建命令行目标。