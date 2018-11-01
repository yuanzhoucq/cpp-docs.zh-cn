---
title: 性能和诊断中心的按配置文件优化
ms.date: 03/14/2018
ms.assetid: dc3a1914-dbb6-4401-bc63-10665a8c8943
ms.openlocfilehash: 57e0c32b401f2c1c3216a120bc86efa649ee0104
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50580851"
---
# <a name="profile-guided-optimization-in-the-visual-studio-2013-performance-and-diagnostics-hub"></a>按配置优化 Visual Studio 2013 性能和诊断中心

如果使用 Visual Studio 2013，Visual c + + 中的性能和诊断中心插件按配置优化简化了开发人员的按配置优化体验。 你可以[下载插件](https://marketplace.visualstudio.com/items?itemName=ProfileGuidedOptimizationTeam.ProfileGuidedOptimizationforVisualC)从 Visual Studio 网站。 该插件不支持更高版本的 Visual Studio 中。

按配置优化 (PGO) 可帮助您创建 x86 和 x64 本机应用的生成版本，同时优化用户与它们之间的交互方式。 PGO 是多步骤过程： 创建用于分析，检测的应用版本，然后执行"培训"。 也就是说，通过常用用户交互方案运行所检测的应用。 您保存捕获的分析数据，然后使用结果引导全程序优化，从而重新生成应用。 尽管您可以在 Visual Studio 或命令行中分别执行这些步骤，但 PGO 插件可以集中并简化这一过程。 PGO 插件可以设置所有必需的选项，指导您完成每个步骤，为您显示分析，然后使用结果配置生成版本，以便优化每个函数的大小或速度。 当你更改代码时，PGO 插件可以让你轻松地重新执行应用培训，并更新生成版本优化数据。

## <a name="prerequisites"></a>系统必备

您必须[下载 PGO 插件](https://marketplace.visualstudio.com/items?itemName=ProfileGuidedOptimizationTeam.ProfileGuidedOptimizationforVisualC)并将其安装在 Visual Studio 中，才能在性能和诊断中心中使用。

## <a name="walkthrough-using-the-pgo-plug-in-to-optimize-an-app"></a>演练：使用 PGO 插件优化应用

首先，您将在 Visual Studio 创建一个基本的 Win32 桌面应用。 如果您已有一个要优化的本机应用，则可以直接使用并跳过此步骤。

### <a name="to-create-an-app"></a>创建应用

1. 在菜单栏上，依次选择“文件” 、“新建” 、“项目” 。

1. 在左窗格中**新的项目**对话框框中，展开**已安装**，**模板**， **Visual c + +**，然后选择**MFC**。

1. 在中心窗格中，选择**MFC 应用程序**。

1. 指定项目的名称 — 例如， **SamplePGOProject**— 在**名称**框。 选择“确定”  按钮。

1. 上**概述**页**MFC 应用程序向导**对话框中，选择**完成**按钮。

接下来，将应用的生成配置设置为“发布”，使之为 PGO 生成和培训步骤做好准备。

### <a name="to-set-the-build-configuration"></a>设置生成配置

1. 在菜单栏上，依次选择 **“生成”**、 **“配置管理器”**。

1. 在中**Configuration Manager**对话框框中，选择**活动解决方案配置**下拉列表按钮，然后选择**发行**。 选择**关闭**按钮。

打开性能和诊断中心，在菜单栏上依次选择**分析**，**性能和诊断**。 这将打开一个诊断会话页，其中具有您的项目类型的可用分析工具。

![性能和诊断中心中的 PGO](../../build/reference/media/pgofig0hub.png "PGOFig0Hub")

在中**可用工具**，选择**按配置优化**复选框。 选择**启动**按钮以启动 PGO 插件。

![PGO 简介页](../../build/reference/media/pgofig1start.png "PGOFig1Start")

**按配置优化**页介绍了插件用来提高您的应用程序性能的步骤。 选择**启动**按钮。

![PGO 检测页](../../build/reference/media/pgofig2instrument.png "PGOFig2Instrument")

在中**Instrumentation**部分中，使用**最初启用培训**选项选择是否在培训中包含您的应用程序的启动阶段。 如果未选中此选项，则在显式启用培训之前，不会记录正在运行的检测应用中的培训数据。

选择**检测**按钮以生成使用一组特殊的编译器选项对应用程序。 编译器会在所生成的代码中插入探测指令。 这些指令会在培训阶段记录分析数据。

![PGO 检测的生成页](../../build/reference/media/pgofig3build.PNG "PGOFig3Build")

当完成所检测的应用生成时，将自动启动此应用。

如果生成过程中发生任何错误或警告，请予以更正，然后选择**重新开始生成**重新启动检测的生成。

您的应用程序启动时，可以使用**入门培训**并**暂停培训**中的链接**培训**部分，以控制何时记录分析信息。 可以使用**停止应用程序**并**启动应用程序**停止并重新启动该应用程序的链接。

![PGO 培训页](../../build/reference/media/pgofig4training.PNG "PGOFig4Training")

在培训过程中，请完成你的用户方案，以便捕获 PGO 插件为优化代码而需要的分析信息。 完成定型后，关闭您的应用程序，或选择**停止应用程序**链接。 选择**分析**按钮以启动分析步骤。

分析完成后，**分析**部分显示了在用户方案培训阶段捕获的分析信息的报表。 您可以使用该报告检查应用调用哪些函数的次数最多、花费的时间最长。 PGO 插件可以使用这些信息确定哪些函数需要优化速度，哪些函数需要优化大小。 PGO 插件可以配置生成优化，以便为培训期间所记录的用户方案创建最小、最快的应用。

![PGO 分析页](../../build/reference/media/pgofig5analyze.png "PGOFig5Analyze")

如果培训捕获预期的分析信息，则可以选择**保存更改**将分析的分析数据保存到项目中来优化未来的生成版本。 若要丢弃分析数据并从开始处重新启动培训，选择**重做培训**。

分析数据文件保存在项目中**PGO Training Data**文件夹。 此数据用于控制应用中的编译器生成优化设置。

![在解决方案资源管理器中的 PGO 数据文件](../../build/reference/media/pgofig6data.png "PGOFig6Data")

在分析后，PGO 插件会在项目中设置生成选项，以便在编译时使用分析数据有选择地优化您的应用。 可以使用相同的分析数据继续修改并生成您的应用。 当生成应用后，生成输出将报告使用分析数据优化了多少函数和指令。

![PGO 输出诊断](../../build/reference/media/pgofig7diagnostics.png "PGOFig7Diagnostics")

在开发过程中，如果进行了大量代码更改，则可能需要重新训练你的应用，以便实现最佳优化。 当生成输出报告不到 80% 的函数或指令使用分析数据进行了优化时，建议您重新训练您的应用。