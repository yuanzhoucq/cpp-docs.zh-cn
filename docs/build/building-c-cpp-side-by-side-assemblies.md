---
title: 生成 C/C++ 并行程序集
ms.date: 11/04/2016
helpviewer_keywords:
- side-by-side applications [C++]
ms.assetid: 7fa20b16-3737-4f76-a0b5-1dacea19a1e8
ms.openlocfilehash: 6e49ba72a397efb97437a2f7e6d721c782875c48
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493329"
---
# <a name="building-cc-side-by-side-assemblies"></a>生成 C/C++ 并行程序集

并行[程序集](/windows/win32/SbsCs/about-side-by-side-assemblies-)是可用于在运行时使用的应用程序的资源 (一组 dll、windows 类、COM 服务器、类型库或接口) 的集合。 在程序集中重新打包 Dll 的主要优点是, 应用程序可以同时使用多个版本的程序集, 并且在更新版本的情况下, 可以为当前已安装的程序集服务。

C++应用程序可以在应用程序的不同部分中使用一个或多个 dll。 在运行时, 会将 Dll 加载到主进程中, 并执行所需的代码。 应用程序依赖于操作系统来查找所请求的 Dll, 了解必须加载其他依赖 Dll, 然后将它们与请求的 DLL 一起加载。 在 windows XP、Windows Server 2003 和 Windows Vista 之前的 Windows 操作系统版本上, 操作系统加载程序将在应用程序的本地文件夹或系统路径上指定的其他文件夹中搜索依赖的 Dll。 在 Windows XP、Windows Server 2003 和 Windows Vista 上, 操作系统加载程序还可以使用[清单](/windows/win32/sbscs/manifests)文件搜索依赖 dll, 并搜索包含这些 dll 的并行程序集。

默认情况下, 使用 Visual Studio 生成 DLL 时, 它会将[应用程序清单](/windows/win32/SbsCs/application-manifests)嵌入为 ID 等于2的 RT_MANIFEST 资源。 与可执行文件一样, 此清单描述此 DLL 在其他程序集上的依赖关系。 这假定 DLL 不是并行程序集的一部分, 依赖于此 DLL 的应用程序不会使用应用程序清单来加载它, 而是依赖于操作系统加载程序在系统路径上找到此 DLL。

> [!NOTE]
> 使用应用程序清单将清单嵌入为 ID 等于2的资源, 这一点非常重要。 如果在运行时动态加载 DLL (例如, 使用[LoadLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryw)函数), 操作系统加载程序将加载 dll 清单中指定的依赖程序集。 `LoadLibrary`调用期间, 不会检查 dll 的外部应用程序清单。 如果未嵌入清单, 则加载程序可能会尝试加载不正确的程序集版本, 或找不到查找依赖程序集的情况。

可以使用相应的[程序集清单](/windows/win32/SbsCs/assembly-manifests)将一个或多个相关的 dll 重新打包到并行程序集中, 该清单描述了程序集和其他并行程序集上的程序集的依赖关系。

> [!NOTE]
> 如果程序集包含一个 DLL, 则建议将程序集清单作为 ID 等于1的资源嵌入此 DLL, 并为私有程序集提供与 DLL 相同的名称。 例如, 如果 DLL 的名称为 mylibrary.dll, 则清单的\<assemblyIdentity > 元素中使用的 name 属性的值也可能为 mylibrary.dll。 在某些情况下, 当库的扩展名不是 .dll 时 (例如, MFC ActiveX 控件项目创建 .ocx 库), 可以创建外部程序集清单。 在这种情况下, 程序集及其清单的名称必须不同于 DLL 的名称 (例如, MyAssembly、MyAssembly 和 mylibrary.dll)。 但仍建议将此类库重命名为具有扩展名 .dll, 并将清单嵌入为资源, 以减少此程序集的将来维护成本。 有关操作系统如何搜索私有程序集的详细信息, 请参阅[程序集搜索顺序](/windows/win32/SbsCs/assembly-searching-sequence)。

此更改可能会允许将相应的 Dll 作为[私有程序集](/windows/win32/Msi/private-assemblies)部署在应用程序本地文件夹中或作为 WinSxS 程序集缓存中的[共享程序集](/windows/win32/Msi/shared-assemblies)。 为了实现此新程序集的正确运行时行为, 必须遵循几个步骤:它们在[创建并行程序集的准则](/windows/win32/SbsCs/guidelines-for-creating-side-by-side-assemblies)中进行了介绍。 编写程序集后, 可以将其部署为共享程序集或私有程序集, 并将其部署为依赖于它的应用程序。 将并行程序集作为共享程序集安装时, 你可以遵循在[WINDOWS XP 上安装 Win32 程序集以进行并行共享](/windows/win32/Msi/installing-win32-assemblies-for-side-by-side-sharing-on-windows-xp)或使用[合并模块](/windows/win32/msi/merge-modules)中所述的指导原则。 将并行程序集作为专用程序集安装时, 您可以将相应的 DLL、资源和程序集清单作为安装过程的一部分复制到目标计算机上的应用程序本地文件夹中, 从而确保可以将此程序集由加载程序在运行时找到 (请参阅[程序集搜索顺序](/windows/win32/SbsCs/assembly-searching-sequence))。 另一种方法是使用[Windows Installer](/windows/win32/Msi/windows-installer-portal) , 并遵循在[Windows XP 上安装应用程序的 Win32 程序集](/windows/win32/Msi/installing-win32-assemblies-for-the-private-use-of-an-application-on-windows-xp)中所述的指导原则。

## <a name="see-also"></a>请参阅

[生成 C/C++ 独立应用程序](building-c-cpp-isolated-applications.md)<br/>
[生成 C/C++ 独立应用程序和并行程序集](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)
