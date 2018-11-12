---
title: 生成自定义项疑难解答
ms.date: 11/04/2016
helpviewer_keywords:
- build events [C++], troubleshooting
- builds [C++], build events
- troubleshooting [C++], builds
- build steps [C++], troubleshooting
- events [C++], build
- builds [C++], troubleshooting
- custom build steps [C++], troubleshooting
ms.assetid: e4ceb177-fbee-4ed3-a7d7-80f0d78c1d07
ms.openlocfilehash: 52f4e37a2321cbd19fc85e7036cb8882e9399ac5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50480895"
---
# <a name="troubleshooting-build-customizations"></a>生成自定义项疑难解答

如果自定义生成步骤或事件没有按预期进行，可以执行以下几项操作，尝试了解出现问题的原因。

- 请确保自定义生成步骤生成的文件匹配声明为输出的文件。

- 如果自定义生成步骤生成的任何文件为输入或其他生成步骤（自定义或者其他）的依赖项，请确保这些文件已添加到项目中。 并确保使用这些文件的工具在自定义生成步骤后执行。

- 若要显示自定义生成步骤实际执行的操作，请将 `@echo on` 添加为第一个命令。 生成事件和生成步骤均放置在临时 .bat 文件中并在生成项目时运行。 因此，可以将错误检查添加到生成事件或生成步骤命令中。

- 在中间文件目录中检查生成日志，查看自动执行的操作。 MSBuild 宏表达式、$(IntDir)\\$(MSBuildProjectName).log 分别表示日志的路径和名称。

- 修改项目设置，以便在生成日志中收集超过默认数量的信息。 在 **“工具”** 菜单上，单击 **“选项”**。 在“选项”对话框框中，单击“项目和解决方案”节点，然后单击“生成和运行”节点。 然后，在“MSBuild 项目生成日志文件详细信息”对话框中，单击“详细信息”。

- 验证任何文件名或正在使用的目录宏的值。 可以单独回显宏，也可以将 `copy %0 command.bat` 添加到自定义生成步骤的开始处，这会将自定义生成步骤的命令复制到已展开所有宏的 command.bat。

- 分别运行自定义步骤和生成事件，检查其行为。

## <a name="see-also"></a>请参阅

[了解自定义生成步骤和生成事件](../ide/understanding-custom-build-steps-and-build-events.md)