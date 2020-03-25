---
title: 错误 C1010
ms.date: 09/03/2019
f1_keywords:
- C1010
helpviewer_keywords:
- C1010
ms.assetid: dfd035f1-a7a2-40bc-bc92-dc4d7f456767
ms.openlocfilehash: 40a2828ce6b21384ec49c371f23e506d816f1284
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80204784"
---
# <a name="fatal-error-c1010"></a>错误 C1010

> 查找预编译头时意外的文件尾。 是否忘记将 "#include*名称*" 添加到源？

## <a name="remarks"></a>备注

[/Yu](../../build/reference/yu-use-precompiled-header-file.md)指定的包含文件未列在源文件中。 在许多 Visual Studio C++项目类型中，默认情况下启用此选项。 此选项指定的默认包含文件为*pch*或 Visual Studio 2017 及更早版本中的*stdafx.h* 。

在 Visual Studio 环境中，使用以下方法之一来解决此错误：

- 确保你没有无意中删除、重命名或删除了当前项目中的*pch*文件或*pch*文件。 （在较早的项目中，这些文件可以命名为*stdafx.h*和*stdafx.h*。）

- 请确保在源文件中的任何其他代码或预处理器指令之前包含*pch*或*stdafx.h*头文件。 （在 Visual Studio 中，此标头文件由**预编译头文件**项目属性指定。）

- 可以关闭预编译标头使用。 如果关闭预编译头，则可能会严重影响生成性能。

### <a name="to-turn-off-precompiled-headers"></a>关闭预编译头

若要在项目中关闭预编译标头使用，请执行以下步骤：

1. 在 "**解决方案资源管理器**" 窗口中，右键单击项目名称，然后选择 "**属性**" 以打开 "项目**属性页**" 对话框。

1. 在 "**配置**" 下拉 "配置" 中，选择 "**所有配置**"。

1. 选择 "**配置属性**" > " **C/C++**  > **预编译标头**" 属性页。

1. 在 "属性" 列表中，选择 "**预编译标头**" 属性的下拉列表，然后选择 "**不使用预编译标头**"。 选择“确定”以保存更改。

1. 在 "**解决方案资源管理器**" 窗口中，右键单击项目中的 " *pch* " 源文件。 （在较早的项目中，该文件可以命名为*stdafx.h*。）选择 "**从项目中排除**" 可将其从生成中删除。

1. 对于生成的每个配置，请使用 "**生成** > **清理解决方案**" 菜单命令删除中间生成目录中的任何*project_name .pch*文件。

## <a name="see-also"></a>另请参阅

[预编译的头文件](../../build/creating-precompiled-header-files.md)\
[/Yc （创建预编译标头文件）](../../build/reference/yc-create-precompiled-header-file.md)\
[/Yu （使用预编译标头文件）](../../build/reference/yu-use-precompiled-header-file.md)
