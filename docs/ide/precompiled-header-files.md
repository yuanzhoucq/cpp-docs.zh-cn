---
title: 预编译的头文件
ms.date: 11/04/2016
f1_keywords:
- stdafx.h
helpviewer_keywords:
- stdafx.h
- PCH files, file descriptions
- .pch files, file descriptions
- precompiled header files, file descriptions
- stdafx.cpp
ms.assetid: 8228d87a-5609-41f3-9697-b16094c000e5
ms.openlocfilehash: fed583464aa172887b80a8551adf86e02a76d210
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50643204"
---
# <a name="precompiled-header-files"></a>预编译的头文件

这些文件用于对头文件 *Projname*.pch 和预编译的类型文件 Stdafx.obj 进行生成和预编译。

这些文件位于 *Projname* 目录中。 在解决方案资源管理器中，Stdafx.h 位于标头文件文件夹中，而 Stdafx.cpp 位于源文件文件夹中。

|文件名|描述|
|---------------|-----------------|
|stdafx.h|标准系统的包含文件和项目特定的包含文件的包含文件，经常使用但不常更改。<br /><br /> 不应定义或取消任何 stdafx.h 中的任何 _AFX_NO_XXX 宏。|
|stdafx.cpp|包含预处理器指令 `#include "stdafx.h"` 并添加预编译类型的包含文件。 任何类型的预编译文件（包括头文件）都可通过将编译仅限于有需要的文件，从而支持更快的编译时间。 首次生成项目后，你将注意到由于预编译头文件的存在，随后生成的生成时间将大大加快。|

## <a name="see-also"></a>请参阅

[为 Visual C++ 项目创建的文件类型](../ide/file-types-created-for-visual-cpp-projects.md)<br>
[使用项目属性](../ide/working-with-project-properties.md)