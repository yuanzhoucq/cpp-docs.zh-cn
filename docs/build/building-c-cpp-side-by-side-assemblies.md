---
title: 生成 C/C++ 并行程序集
ms.date: 11/04/2016
helpviewer_keywords:
- side-by-side applications [C++]
ms.assetid: 7fa20b16-3737-4f76-a0b5-1dacea19a1e8
ms.openlocfilehash: cf3fb532e70e047938b9a575eefdcceadceeceda
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50476305"
---
# <a name="building-cc-side-by-side-assemblies"></a>生成 C/C++ 并行程序集

一个[-并行程序集](/windows/desktop/SbsCs/about-side-by-side-assemblies-)是一系列资源-一组 Dll、 windows 类、 COM 服务器、 类型库或接口 — 可用于应用程序在运行时使用。 将 Dll 重新打包程序集的主要优点是，在同一时间的应用程序可以使用多个版本的程序集，并且可能对发生的更新版本时的当前安装的服务程序集。

Visual c + + 应用程序可能使用的应用程序的不同部分中的一个或多个 Dll。 在运行时，Dll 加载到主进程并执行所需的代码。 应用程序依赖于操作系统，可以找到所需的 Dll，请了解其他的依赖 Dll 已加载，然后连同请求 DLL 加载它们。 在 Windows 操作系统版本早于 Windows XP、 Windows Server 2003 和 Windows Vista 操作系统加载程序搜索应用程序的本地文件夹或指定的系统路径上的另一个文件夹中的依赖 Dll。 在 Windows XP、 Windows Server 2003 和 Windows Vista 上，操作系统加载程序还可以搜索使用的依赖 Dll[清单](https://msdn.microsoft.com/library/windows/desktop/aa375365)文件并搜索包含这些 Dll 的并行程序集。

默认情况下，如果 DLL 使用 Visual Studio 中，生成它具有[应用程序清单](/windows/desktop/SbsCs/application-manifests)id 等于 2 作为 RT_MANIFEST 资源嵌入。 就像一个可执行文件，此清单上的其他程序集描述此 DLL 的依赖项。 这假定 DLL 不是通过并行程序集的一部分，并依赖于此 DLL 的应用程序不会使用应用程序清单来加载它，而是依靠操作系统加载程序的系统路径上找到此 DLL。

> [!NOTE]
> 务必使用应用程序清单能够与 ID 等于 2 作为资源嵌入的清单的 DLL。 如果在运行时动态加载了 DLL (例如，使用[LoadLibrary](/windows/desktop/api/libloaderapi/nf-libloaderapi-loadlibrarya)函数)，操作系统加载程序加载 DLL 的清单中指定的依赖程序集。 Dll 的外部应用程序清单不检查期间`LoadLibrary`调用。 如果未嵌入清单，加载程序可能会尝试加载的程序集不正确版本，或无法找到依赖程序集。

一个或多个相关的 Dll 可以重新打包到具有相应的通过并行程序集[程序集清单](/windows/desktop/SbsCs/assembly-manifests)，它描述了哪些文件窗体的程序集，以及该程序集的依赖其他的并排方案程序集。

> [!NOTE]
> 如果程序集包含一个 DLL，它被建议的程序集清单嵌入到此 DLL 的资源 id 等于 1，并为私有程序集提供与 DLL 相同的名称。 例如，如果 DLL 的名称为 mylibrary.dll，则 name 属性的值中使用\<assemblyIdentity > 在清单元素也可以是 mylibrary。 在某些情况下，当库具有.dll 以外的扩展名 （例如，MFC ActiveX 控件项目创建.ocx 库） 可以创建一个外部程序集清单。 在这种情况下，该程序集和其清单的名称必须不同于 DLL （例如，MyAssembly、 MyAssembly.manifest，和 mylibrary.ocx） 的名称。 但是它仍被建议重命名此类的库来.dll，并将清单嵌入作为资源以减少此程序集的将来的维护成本。 有关操作系统如何搜索私有程序集的详细信息，请参阅[程序集搜索顺序](/windows/desktop/SbsCs/assembly-searching-sequence)。

此更改可能会允许相应的 Dll 作为部署[私有程序集](/windows/desktop/Msi/private-assemblies)应用程序本地文件夹或作为[共享程序集](/windows/desktop/Msi/shared-assemblies)WinSxS 程序集缓存中。 几个步骤需要遵循以便实现正确的运行时行为的这个新的程序集;中所述[创建的并行程序集的准则](/windows/desktop/SbsCs/guidelines-for-creating-side-by-side-assemblies)。 正确编写程序集后可以作为任一共享或私有程序集依赖于它的应用程序一起部署。 安装时的并行程序集作为共享程序集，可以的按照中介绍的指南[以在 Windows XP 上的并行共享安装 Win32 程序集](/windows/desktop/Msi/installing-win32-assemblies-for-side-by-side-sharing-on-windows-xp)或使用[合并模块](https://msdn.microsoft.com/library/windows/desktop/aa369820). 安装时的并行程序集作为专用程序集，您可能只需将复制相应 DLL、 资源和程序集清单中，作为安装过程的一部分到目标计算机上的应用程序本地文件夹确保此程序集可以在运行时加载程序找到 (请参阅[程序集搜索顺序](/windows/desktop/SbsCs/assembly-searching-sequence))。 另一种方法是使用[Windows Installer](/windows/desktop/Msi/windows-installer-portal)并按照中所述的准则[安装 Windows XP 上的应用程序专用使用的 Win32 程序集](/windows/desktop/Msi/installing-win32-assemblies-for-the-private-use-of-an-application-on-windows-xp)。

## <a name="see-also"></a>请参阅

[部署示例](../ide/deployment-examples.md)<br/>
[生成 C/C++ 独立应用程序](../build/building-c-cpp-isolated-applications.md)<br/>
[生成 C/C++ 独立应用程序和并行程序集](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)