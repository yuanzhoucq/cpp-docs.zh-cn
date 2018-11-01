---
title: 递归宏
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, recursion macros
- recursion macros
- macros, recursion
ms.assetid: c53e5ae7-619e-46b1-bdc2-86d8c7798b1d
ms.openlocfilehash: 0005a4be0422ed83816eabc7b55932a81441ae25
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50451254"
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