---
title: 如何：将自定义工具集成到项目属性中
ms.date: 05/16/2019
helpviewer_keywords:
- 'msbuild (c++), howto: integrate custom tools'
ms.assetid: f32d91a4-44e9-4de3-aa9a-1c7f709ad2ee
ms.openlocfilehash: 0c0233ad6715a3adb7d47f021a87207f288d5139
ms.sourcegitcommit: a10c9390413978d36b8096b684d5ed4cf1553bc8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2019
ms.locfileid: "65837035"
---
# <a name="how-to-integrate-custom-tools-into-the-project-properties"></a>如何：将自定义工具集成到项目属性中

可通过创建基础 XML 架构文件，将自定义工具选项添加到 Visual Studio“属性页”。

“属性页”窗口的“配置属性”部分显示名为“规则”的设置组。 每个规则都包含一个工具或一组功能的设置。 例如，“链接器”规则包含链接器工具的设置。 规则中的设置可以细分为各种类别。

本文档说明如何在包含自定义工具属性的设置目录中创建文件，以便在 Visual Studio 启动时加载这些属性。 有关如何修改该文件的信息，请参阅 Visual Studio 项目团队博客上的[平台可扩展性第 2 部分](https://blogs.msdn.microsoft.com/vsproject/2009/06/18/platform-extensibility-part-2/)。

### <a name="to-add-or-change-project-properties"></a>添加或更改项目属性

1. 在 XML 编辑器中，创建 XML 文件。

1. 将文件保存在 Visual Studio `VCTargets\1033` 文件夹中。 安装的每个 Visual Studio 版本和每种语言都有不同的路径。 例如，Visual Studio 2019 Community 英文版的默认文件夹路径是 `C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\IDE\VC\VCTargets`。 调整语言和 Visual Studio 版本的路径。 “属性页”窗口中的每个规则都由此文件夹中的 XML 文件表示。 请确保该文件在文件夹中具有唯一的名称。

1. 复制 `%ProgramFiles%\Microsoft Visual Studio\2019\<VS Edition>\Common7\IDE\VC\VCTargets\<LCID>\cl.xml`（或任何路径）的内容、不保存更改直接关闭，然后将内容粘贴在新的 XML 文件中。 可以使用任何可用的 XML 架构文件，以便开始使用模板。

1. 在新的 XML 文件中，根据要求修改内容。 请确保更改文件顶部的“规则名称”和“Rule.DisplayName”。

1. 保存更改并关闭文件。

1. 启动 Visual Studio 时，会加载 `%ProgramFiles%\Microsoft Visual Studio\2019\<VS Edition>\Common7\IDE\VC\VCTargets\<LCID>`（或任何保存位置）中的 XML 文件。 因此，若要测试新文件，请重启 Visual Studio。

1. 在“解决方案资源管理器”中，右键单击项目，然后单击“属性”。 在“属性页”窗口的左侧窗格中，验证是否存在名称为“规则”的新节点。

## <a name="see-also"></a>请参阅

[命令行上的 MSBuild - C++](msbuild-visual-cpp.md)
