---
title: 准备用于运行调试可执行文件的测试计算机
ms.date: 07/02/2019
helpviewer_keywords:
- debug executable, preparing a test machine to run
ms.assetid: f0400989-cc2e-4dce-9788-6bdbe91c6f5a
ms.openlocfilehash: ae751b1632473fa316c7965bc751e91b782a89ea
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513665"
---
# <a name="preparing-a-test-machine-to-run-a-debug-executable"></a>准备用于运行调试可执行文件的测试计算机

若要准备计算机以测试使用 Visual C++ 生成的应用程序的调试版本，你必须部署应用程序依赖的 Visual C++ 库 DLL 的调试版本。 要验证必须部署哪些 DLL，请遵循[了解 Visual C++ 应用程序的依赖项](understanding-the-dependencies-of-a-visual-cpp-application.md)中的步骤。 通常，Visual C++ 库 DLL 的调试版本具有以“d”结尾的名称；例如，msvcr100.dll 的调试版本名为 msvcr100d.dll。

> [!NOTE]
>  应用程序的调试版本是不可再发行的，而且 Visual C++ 库 DLL 的调试版本也是不可再发行的。 您可以只是为了在未安装 Visual Studio 的计算机上调试和测试应用程序，来仅将应用程序的调试版本和 Visual C++ DLL 部署到其他计算机上。 有关详细信息，请参阅 [Redistributing Visual C++ Files](redistributing-visual-cpp-files.md)。

可通过三种方式将 Visual C++ 库 DLL 的调试版本与应用程序的调试版本一起部署。

- 借助中央部署将特定的 Visual C++ DLL 的调试版本安装到 %windir%\system32\ 目录中，方式是使用包含正确的库版本的合并模块和应用程序的体系结构的安装程序项目。 可以在 \Common Files\Merge Modules\\ 中的 Program Files 或 Program Files (x86) 目录下找到合并模块。 合并模块的调试版本的名称包含 Debug，例如，Microsoft_VC110_DebugCRT_x86.msm。 有关此部署的示例，请参阅[演练：使用安装项目部署 Visual C++ 应用程序](walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project.md)。

- 借助本地部署将特定的 Visual C++ DLL 的调试版本安装到应用程序的安装目录，方式是使用 \Microsoft Visual Studio \<版本>\VC\redist\Debug_NonRedist\\ 中的 Program Files 或 Program Files (x86) 目录下提供的文件。

    > [!NOTE]
    >  若要在另一台计算机上使用 Visual Studio 2005 或 Visual Studio 2008 生成的应用程序的远程调试, 必须将 Visual C++ library dll 的调试版本作为共享并行程序集进行部署。 可以使用安装程序项目或 Windows Installer 来安装相应的合并模块。

- 使用 Visual Studio 中“配置管理器”对话框中的“部署”选项将项目输出和其他文件复制到远程计算机。

安装 Visual C++ DLL 之后，您可以在网络共享上运行远程调试程序。 有关远程调试的详细信息，请参阅[远程调试](/visualstudio/debugger/remote-debugging)。

## <a name="see-also"></a>请参阅

[Visual C++ 中的部署](deployment-in-visual-cpp.md)<br>
[Windows Installer 命令行选项](/windows/win32/Msi/command-line-options)<br>
[部署示例](deployment-examples.md)<br>
[远程调试](/visualstudio/debugger/remote-debugging)
