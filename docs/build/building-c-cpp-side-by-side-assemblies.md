---
title: 生成 C/C++ 并行程序集
ms.date: 11/04/2016
helpviewer_keywords:
- side-by-side applications [C++]
ms.assetid: 7fa20b16-3737-4f76-a0b5-1dacea19a1e8
ms.openlocfilehash: 6e49ba72a397efb97437a2f7e6d721c782875c48
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493329"
---
# <a name="building-cc-side-by-side-assemblies"></a>生成 C/C++ 并行程序集

[并行程序集](/windows/win32/SbsCs/about-side-by-side-assemblies-)是指应用程序在运行时可使用的资源的集合，如一组 DLL、Windows 类、COM 服务器、类型库或接口。 在程序集中重新打包 DLL 的主要优点是，应用程序可以同时使用多个版本的程序集，并且对于更新版本，可以处理当前已安装的程序集。

C++ 应用程序可以在应用程序的不同部分中使用一个或多个 DLL。 在运行时，会将 DLL 加载到主进程中，并执行所需代码。 应用程序依赖于操作系统来查找所请求的 DLL，了解必须加载的其他依赖 DLL，然后将它们与请求的 DLL 一起加载。 在 Windows XP、Windows Server 2003 和 Windows Vista 之前的 Windows 操作系统版本上，操作系统加载程序会在应用程序的本地文件夹或系统路径上指定的其他文件夹中搜索依赖 DLL。 在 Windows XP、Windows Server 2003 和 Windows Vista 上，操作系统加载程序还可以使用[清单](/windows/win32/sbscs/manifests)文件搜索依赖 DLL，并搜索包含这些 DLL 的并行程序集。

默认情况下，使用 Visual Studio 生成 DLL 时，会将[应用程序清单](/windows/win32/SbsCs/application-manifests)作为 ID 等于 2 的 RT_MANIFEST 资源嵌入。 正如对可执行文件一样，此清单描述此 DLL 对其他程序集的依赖关系。 这假设 DLL 不是并行程序集的一部分，并且依赖于此 DLL 的应用程序不会使用应用程序清单加载它，而是依赖于操作系统加载程序在系统路径上查找此 DLL。

> [!NOTE]
> 使用应用程序清单的 DLL 将清单作为 ID 等于 2 的资源嵌入，这一点非常重要。 如果在运行时动态加载 DLL（例如，使用 [LoadLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryw) 函数），则操作系统加载程序会加载 DLL 清单中指定的依赖程序集。 在 `LoadLibrary` 调用期间，不会检查 DLL 的外部应用程序清单。 如果未嵌入清单，则加载程序可能会尝试加载不正确的程序集版本，或找不到依赖程序集。

一个或多个相关 DLL 可以通过对应[程序集清单](/windows/win32/SbsCs/assembly-manifests)重新打包到并行程序集中，该清单描述组成该程序集的文件以及该程序集对其他并行程序集的依赖关系。

> [!NOTE]
> 如果程序集包含一个 DLL，则建议将程序集清单作为 ID 等于 1 的资源嵌入此 DLL 中，并为私有程序集提供与 DLL 相同的名称。 例如，如果该 DLL 的名称为 mylibrary.dll，则清单的 \<assemblyIdentity> 元素中使用的名称特性的值也可以是 mylibrary。 在某些情况下，当库的扩展名不是 .dll 时（例如，MFC ActiveX 控件项目会创建 .ocx 库），可以创建外部程序集清单。 在这种情况下，程序集及其清单的名称必须与于 DLL 的名称不同（例如，MyAssembly、MyAssembly.manifest 和 mylibrary.ocx）。 但仍建议将此类库重命名为具有扩展名 .dll，并将清单作为资源嵌入，以减少此程序集的将来维护成本。 有关操作系统如何搜索私有程序集的详细信息，请参阅[程序集搜索顺序](/windows/win32/SbsCs/assembly-searching-sequence)。

此更改可能会允许将对应 DLL 作为[私有程序集](/windows/win32/Msi/private-assemblies)部署在应用程序本地文件夹中，或作为[共享程序集](/windows/win32/Msi/shared-assemblies)部署在 WinSxS 程序集缓存中。 若要实现此新程序集的正确运行时行为，必须遵循几个步骤；[有关创建并行程序集的准则](/windows/win32/SbsCs/guidelines-for-creating-side-by-side-assemblies)中介绍了这些步骤。 正确创作程序集之后，可以将它部署为共享程序集，或是作为私有程序集与依赖于它的应用程序一起部署。 将并行程序集作为共享程序集进行安装时，可以按照[在 Windows XP 上安装 Win32 程序集以便并行共享](/windows/win32/Msi/installing-win32-assemblies-for-side-by-side-sharing-on-windows-xp)中所述的准则或使用[合并模块](/windows/win32/msi/merge-modules)。 将并行程序集作为私有程序集进行安装时，只能将对应 DLL、资源和程序集清单作为安装过程的一部分复制到目标计算机上的应用程序本地文件夹，从而确保加载程序在运行时可以找到此程序集（请参阅[程序集搜索顺序](/windows/win32/SbsCs/assembly-searching-sequence)）。 另一种方法是使用 [Windows Installer](/windows/win32/Msi/windows-installer-portal)，并遵循[在 Windows XP 上安装 Win32 程序集以实现应用程序的专用](/windows/win32/Msi/installing-win32-assemblies-for-the-private-use-of-an-application-on-windows-xp)中所述的准则。

## <a name="see-also"></a>请参阅

[生成 C/C++ 独立应用程序](building-c-cpp-isolated-applications.md)<br/>
[生成 C/C++ 独立应用程序和并行程序集](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)
