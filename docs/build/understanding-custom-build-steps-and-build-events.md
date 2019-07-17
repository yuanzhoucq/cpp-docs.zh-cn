---
title: 了解自定义生成步骤和生成事件
ms.date: 11/04/2016
helpviewer_keywords:
- builds [C++], events
- custom build steps [C++], customizing builds
- events [C++], build
- custom build steps [C++]
- build steps [C++]
- build events [C++], order of events and build steps
- build steps [C++], build events
- builds [C++], custom build steps
ms.assetid: beb2f017-3e9f-4b2c-9b57-2572fd2628e4
ms.openlocfilehash: 93a1c787a863c2c52986a00fdeabbc4d44b0fcce
ms.sourcegitcommit: 8bb2bea1384b290b7570b01608a86c7488ae7a02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2019
ms.locfileid: "67400447"
---
# <a name="understanding-custom-build-steps-and-build-events"></a>了解自定义生成步骤和生成事件

可通过三种基本方法从 Visual C++ 开发环境内自定义生成过程：

- **自定义生成步骤**

   自定义生成步骤是与项目关联的生成规则。 自定义生成步骤可指定要执行的命令行、任何其他输入或输出文件，以及要显示的消息。 有关详细信息，请参阅[如何：向 MSBuild 项目添加自定义生成步骤](how-to-add-a-custom-build-step-to-msbuild-projects.md)。

- **自定义生成工具**

   自定义生成工具是与一个或多个文件关联的生成规则。 自定义生成步骤可将输入文件传递给自定义生成工具，从而产生一个或多个输出文件。 例如，MFC 应用程序中的帮助文件都是借助自定义生成工具生成的。 有关详细信息，请参阅[如何：向 MSBuild 项目添加自定义生成工具](how-to-add-custom-build-tools-to-msbuild-projects.md)以及[指定自定义生成工具](specifying-custom-build-tools.md)。

- **生成事件**

   生成事件可用于自定义项目的生成。 有三种生成事件：预先生成、预链接和后期生成    。 通过生成事件，可以指定在生成过程中的特定时间发生的操作。 例如，可以使用生成事件在项目完成生成后通过 regsvr32.exe 注册文件  。 有关详细信息，请参阅[指定生成事件](specifying-build-events.md)。

[生成自定义项疑难解答](troubleshooting-build-customizations.md)可帮助确保自定义生成步骤和生成事件按预期运行。

自定义生成步骤或生成事件的输出格式也可以增强工具的可用性。 有关详细信息，请参阅[设置自定义生成步骤或生成事件输出的格式](formatting-the-output-of-a-custom-build-step-or-build-event.md)。

生成事件和自定义生成步骤与其他生成步骤一起按以下顺序运行：

1. 预先生成事件

2. 单个文件上的自定义生成工具

3. MIDL

4. 资源编译器

5. C/C++ 编译器

6. Pre-Link 事件

7. 链接器或库管理器（视情况而定）

8. 清单工具

9. BSCMake

10. 项目上的自定义生成步骤

11. 后期生成事件

在完成所有其他生成过程后，`custom build step on the project` 和 `post-build event` 按顺序运行。

## <a name="in-this-section"></a>本节内容

[指定自定义生成工具](specifying-custom-build-tools.md)<br/>
[指定生成事件](specifying-build-events.md)<br/>
[排除生成自定义项故障](troubleshooting-build-customizations.md)<br/>
[设置自定义生成步骤或生成事件的输出格式](formatting-the-output-of-a-custom-build-step-or-build-event.md)

## <a name="see-also"></a>请参阅

[Visual Studio 项目 - C++](creating-and-managing-visual-cpp-projects.md)<br>
[用于生成命令和属性的常用宏](reference/common-macros-for-build-commands-and-properties.md)
