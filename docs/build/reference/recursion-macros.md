---
title: 递归宏
description: 描述在递归会话中用于调用 NMAKE 的宏。
ms.date: 11/20/2019
helpviewer_keywords:
- NMAKE program, recursion macros
- recursion macros
- macros, recursion
ms.assetid: c53e5ae7-619e-46b1-bdc2-86d8c7798b1d
no-loc:
- MAKE
- MAKEDIR
- MAKEFLAGS
ms.openlocfilehash: f2bda23cb079e4fd7d12cea3598d33b3625c088d
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303143"
---
# <a name="recursion-macros"></a>递归宏

使用递归宏递归调用 NMAKE。 递归会话继承命令行和环境变量宏以及工具 .ini 信息。 它们不会继承生成文件定义的推理规则或 `.SUFFIXES` 和 `.PRECIOUS` 规范。 有三种方法可将宏传递到递归 NMAKE 会话：在递归调用之前使用 :::no-loc text="SET"::: 命令设置环境变量。 在用于递归调用的命令中定义宏。 或者，在 "setup.ini" 中定义宏。

|宏|定义|
|-----------|----------------|
|**MAKE**|最初用于调用 NMAKE 的命令。<br /><br /> `$(MAKE)` 宏提供了 eseutil.exe 的完整路径。|
|**MAKEDIR**|调用 NMAKE 时的当前目录。|
|**MAKEFLAGS**|当前有效的选项。 用作 `/$(MAKEFLAGS)`。 不包括 **/f**选项。|

## <a name="see-also"></a>另请参阅

[特殊 NMAKE 宏](special-nmake-macros.md)
