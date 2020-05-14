---
title: 如何：针对 64 位 x64 平台配置 Visual Studio C++ 项目
ms.date: 11/04/2016
helpviewer_keywords:
- platforms [C++], 64-bit
- 64-bit programming [C++], configuring projects
- project configurations [C++]
ms.assetid: 2b9ae001-df36-4750-83b2-982145d632ad
ms.openlocfilehash: 762fd5d6ddbb55713cf2fc5e34cb33fb91b08eb9
ms.sourcegitcommit: ce3393846c86e7905ff0c86e4cd6610476809585
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/25/2019
ms.locfileid: "68492242"
---
# <a name="how-to-configure-visual-studio-c-projects-to-target-64-bit-x64-platforms"></a>如何：针对 64 位 x64 平台配置 Visual Studio C++ 项目

可以使用 Visual Studio IDE 中的项目配置来设置面向 64 位 x64 平台的 C++ 应用程序。 还可以将 Win32 项目设置迁移到 64 位项目配置。

### <a name="to-set-up-c-applications-to-target-64-bit-platforms"></a>设置项目以面向 64 位平台

1. 打开要配置的 C++ 项目。

1. 打开该项目的属性页面。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](working-with-project-properties.md)。

   > [!NOTE]
   > 对于.NET 项目，请确保在“\<项目名称>属性页面”对话框中选择“配置属性”节点或一个子节点；否则“配置管理器”按钮仍然不可用    。

1. 选择“配置管理器”  按钮以打开“配置管理器”  对话框。

1. 在“活动解决方案平台”下拉列表中，选择“\<新建...>”选项来打开“新建解决方案平台”对话框    。

1. 在“键入或选择新平台”  下拉列表中，选择 64 位目标平台。

   > [!NOTE]
   > 在“新建解决方案平台”  对话框中，可以使用“从此处复制设置”  选项将现有项目设置复制到新的 64 位项目配置中。

1. 选择“确定”  按钮。 前一步中选择的平台出现在“配置管理器”对话框的“活动解决方案平台”下   。

1. 请在“配置管理器”对话框中选择“关闭”按钮，然后在“\<项目名称>属性页面”对话框中选择“确定”按钮     。

### <a name="to-copy-win32-project-settings-into-a-64-bit-project-configuration"></a>将 Win32 项目设置复制到 64 位项目配置中

- 当设置面向 64 位平台的项目时，如果“新建解决方案平台”  对话框处于打开状态，请在“从此处复制设置”  下拉列表中选择“Win32”  。 在项目级别会自动更新这些项目设置：

  - [/MACHINE](reference/machine-specify-target-platform.md) 链接器选项设置为 **/MACHINE:X64**。

  - 关闭“注册输出”  。 有关详细信息，请参阅 [Linker Property Pages](reference/linker-property-pages.md)。

  - “目标环境”  设置为 **/env x64**。 有关详细信息，请参阅 [MIDL 属性页](reference/midl-property-pages.md)。

  - “验证参数”  被清除并且重置为默认值。 有关详细信息，请参阅 [MIDL 属性页](reference/midl-property-pages.md)。

  - 如果在 Win32 项目配置中已将“调试信息格式”  设置为 **/ZI** ，则在 64 位项目配置中将设置为 **/Zi** 。 有关详细信息，请参阅 [/Z7、/Zi、/ZI（调试信息格式）](reference/z7-zi-zi-debug-information-format.md)。

  > [!NOTE]
  > 如果在文件级重写，则不会更改这些项目属性。

## <a name="see-also"></a>请参阅

[针对 64 位 x64 目标配置 C++ 项目](configuring-programs-for-64-bit-visual-cpp.md)<br/>
[调试 64 位应用程序](/visualstudio/debugger/debug-64-bit-applications)
