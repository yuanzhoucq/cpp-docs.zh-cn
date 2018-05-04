---
title: 生成 C/c + + 端并行程序集 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- side-by-side applications [C++]
ms.assetid: 7fa20b16-3737-4f76-a0b5-1dacea19a1e8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a45062af5648c7b3565d959fd1d2dce13aeca4b3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="building-cc-side-by-side-assemblies"></a>生成 C/C++ 并行程序集
A[通过并行程序集](http://msdn.microsoft.com/library/windows/desktop/ff951640)是资源的集合-一组 Dll、 windows 类、 COM 服务器、 类型库或接口 — 可用于应用程序在运行时使用。 将 Dll 重新打包程序集的主要优点是，在同一时间应用程序可以使用多个版本的程序集，并且可能对发布更新的当前安装的服务程序集。  
  
 Visual c + + 应用程序可以使用应用程序的不同部分中的一个或多个 Dll。 在运行时，Dll 加载到主进程并执行所需的代码。 应用程序依赖于操作系统以找到所需的 Dll、 了解其他依赖 Dll 已加载，然后与请求的 DLL 中加载它们。 在 Windows 操作系统版本早于 Windows XP、 Windows Server 2003 和 Windows Vista 中，操作系统加载程序搜索的应用程序的本地文件夹或指定的系统路径上的另一个文件夹中的依赖 Dll。 在 Windows XP、 Windows Server 2003 和 Windows Vista 上，操作系统加载程序还可以搜索使用的依赖 Dll[清单](http://msdn.microsoft.com/library/windows/desktop/aa375365)文件然后搜索包含这些 Dll 的并行程序集。  
  
 默认情况下，如果 DLL 使用 Visual Studio 中，生成它具有[应用程序清单](http://msdn.microsoft.com/library/windows/desktop/aa374191)作为 RT_MANIFEST 资源嵌入 id 等于 2。 一样可执行文件，此清单说明在其他程序集上的此 DLL 的依赖项。 这假定此 DLL 不是通过并行程序集的一部分，并依赖于此 DLL 的应用程序不会使用应用程序清单来加载它，而是依靠操作系统加载程序的系统路径中查找此 DLL。  
  
> [!NOTE]
>  务必使用应用程序清单具有 id 等于 2 作为资源嵌入的清单的 DLL。 如果在运行时动态加载该 DLL (例如，使用[LoadLibrary](http://msdn.microsoft.com/library/windows/desktop/ms684175)函数)，则操作系统加载程序加载 DLL 的清单中指定的依赖程序集。 Dll 的外部应用程序清单不会检查期间`LoadLibrary`调用。 如果未嵌入清单，加载程序可能会尝试加载的程序集不正确版本，或无法找到相关程序集。  
  
 一个或多个相关 Dll 可以重新打包到与相应的并行程序集[程序集清单](http://msdn.microsoft.com/library/windows/desktop/aa374219)，其中描述哪些文件在其他并行的构成程序集，以及该程序集的依赖性程序集。  
  
> [!NOTE]
>  如果程序集包含的一个 DLL，它被建议用于程序集将清单嵌入到此 DLL 作为资源 id 等于 1，并为私有程序集提供与 DLL 相同的名称。 例如，如果 DLL 的名称为 mylibrary.dll，名称属性的值中使用\<assemblyIdentity > 清单元素也可以是 mylibrary。 在某些情况下，当库具有非.dll 的扩展名 （例如，MFC ActiveX 控件项目创建.ocx 库） 可以创建一个外部程序集清单。 在这种情况下，程序集和其清单的名称必须不同于 DLL （例如，MyAssembly、 MyAssembly.manifest，和 mylibrary.ocx） 的名称。 但是，仍然被建议重命名这种库以.dll，并将清单嵌入作为资源以减少此程序集的将来的维护成本。 有关操作系统如何搜索私有程序集的详细信息，请参阅[程序集搜索顺序](http://msdn.microsoft.com/library/windows/desktop/aa374224)。  
  
 此更改可能允许相应的 Dll 作为部署[私有程序集](http://msdn.microsoft.com/library/windows/desktop/aa370850)在应用程序本地文件夹中或作为[共享程序集](http://msdn.microsoft.com/library/windows/desktop/aa371839)WinSxS 程序集缓存中。 几个步骤需要遵循以便实现正确的运行时行为的此新的程序集;中描述了这些[对创建的并行程序集的准则](http://msdn.microsoft.com/library/windows/desktop/aa375155)。 正确编写程序集后可以部署为任一共享或私有程序集的应用程序依赖于它在一起。 安装时的并行程序集作为共享程序集，可以的按照中介绍的指南[安装 Win32 程序集以在 Windows XP 上的并排显示共享](http://msdn.microsoft.com/library/windows/desktop/aa369532)或使用[的合并模块](http://msdn.microsoft.com/library/windows/desktop/aa369820). 安装时的并行程序集作为私有程序集，你可能只复制相应 DLL、 资源和程序集清单中，作为安装过程的一部分到应用程序本地文件夹的目标计算机上，确保此程序集可以在运行时加载器找到 (请参阅[程序集搜索顺序](http://msdn.microsoft.com/library/windows/desktop/aa374224))。 另一种方法是使用[Windows Installer](http://msdn.microsoft.com/library/windows/desktop/cc185688)然后按照所述的指导[安装 Win32 程序集以在 Windows XP 上的应用程序私用](http://msdn.microsoft.com/library/windows/desktop/aa369534)。  
  
## <a name="see-also"></a>请参阅  
 [部署示例](../ide/deployment-examples.md)   
 [生成 C/c + + 独立应用程序](../build/building-c-cpp-isolated-applications.md)   
 [生成 C/C++ 独立应用程序和并行程序集](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)