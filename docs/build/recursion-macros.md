---
title: 递归宏 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, recursion macros
- recursion macros
- macros, recursion
ms.assetid: c53e5ae7-619e-46b1-bdc2-86d8c7798b1d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f91a5f327686a522608b6eec9fd7106cbab00028
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45702035"
---
# <a name="recursion-macros"></a>递归宏

使用递归宏调用 NMAKE 以递归方式。 递归会话继承命令行和环境变量宏和 Tools.ini 信息。 它们不会继承生成文件定义的推理规则或 **。后缀**和 **。宝贵**规范。 若要传递到递归 NMAKE 会话的宏，递归调用之前使用 SET 设置环境变量、 递归调用，在命令中定义的宏或 Tools.ini 中定义的宏。

|宏|定义|
|-----------|----------------|
|**使**|最初用于调用 NMAKE 命令。<br /><br /> $ （make） 宏提供 nmake.exe 的完整路径。|
|**MAKEDIR**|NMAKE 调用时的当前目录。|
|**MAKEFLAGS**|当前正在生效的选项。 使用作为`/$(MAKEFLAGS)`。  请注意，/F 则不包含。|

## <a name="see-also"></a>请参阅

[特殊 NMAKE 宏](../build/special-nmake-macros.md)