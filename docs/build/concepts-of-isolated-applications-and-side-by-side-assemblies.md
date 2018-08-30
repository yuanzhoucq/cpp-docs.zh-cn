---
title: 独立应用程序和通过并行程序集的概念 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- side-by-side assemblies [C++]
- isolated assemblies [C++]
ms.assetid: 945a885f-cb3e-4c8a-a0b9-2c2e3e02cc50
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 62420838cca0bcb2a922b01c6951749de7449e81
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43222456"
---
# <a name="concepts-of-isolated-applications-and-side-by-side-assemblies"></a>独立应用程序和并行程序集的概念
该应用程序视为[独立应用程序](/windows/desktop/SbsCs/isolated-applications)其所有组件是否[通过并行程序集](/windows/desktop/SbsCs/about-side-by-side-assemblies-)。 并行程序集是指应用程序在运行时可部署在一起并可使用的资源的集合，如一组 DLL、Windows 类、COM 服务器、类型库或接口。 通常，并行程序集是一个或若干个 DLL。  
  
## <a name="shared-or-private"></a>共享或私有  
 并行程序集可以是共享或私有的。 [共享的并行程序集](https://msdn.microsoft.com/library/aa375996.aspx)可能由多个应用程序在各自的清单中指定程序集的依赖。 同时运行的不同应用程序可以共享多个版本的并行程序集。 一个[私有程序集](/windows/desktop/SbsCs/about-private-assemblies-)是与该应用程序独占使用的应用程序一起部署程序集。 私有程序集安装在包含该应用程序的可执行文件的文件夹或该文件夹的一个子文件夹中。  
  
## <a name="manifests-and-search-order"></a>清单和搜索顺序  
 独立应用程序和通过并行程序集均由描述[清单](https://msdn.microsoft.com/library/aa375365)。 清单是一个 XML 文档，既可以是外部文件，也可以作为资源嵌入到应用程序或程序集内。 独立应用程序的清单文件用于管理共享的并行程序集的名称和版本，应用程序应当在运行时绑定到这些程序集。 并行程序集的清单用于指定并行程序集的名称、版本、资源和依赖程序集。 对于共享并行程序集，其清单安装在 %WINDIR%\WinSxS\Manifests\ 文件夹中。 对于私有程序集，建议将其清单作为 ID 为 1 的资源包含在 DLL 中。 还可以为私有程序集提供与 DLL 相同的名称。 有关详细信息，请参阅[有关专用程序集](/windows/desktop/SbsCs/about-private-assemblies-)。  
  
 执行时，Windows 将使用应用程序清单中的程序集信息，以搜索并加载相应的并行程序集。 如果独立应用程序指定了程序集依赖项，则操作系统会首先在 %WINDIR%\WinSxS\ 文件夹中的本机程序集缓存中的共享程序集中搜索程序集。 如果未找到所需的程序集，则操作系统会在应用程序目录结构的文件夹中搜索私有程序集。 有关详细信息，请参阅[程序集搜索顺序](/windows/desktop/SbsCs/assembly-searching-sequence)。  
  
## <a name="changing-dependencies"></a>更改依赖项  
 通过修改部署应用程序后，可以更改通过并行程序集依赖项[发行者配置文件](/windows/desktop/SbsCs/publisher-configuration-files)并[应用程序配置文件](/windows/desktop/SbsCs/application-configuration-files)。 发行者配置文件（也称为发行者策略文件）是一个 XML 文件，它对应用程序和程序集进行全局重定向，使其从使用并行程序集的一个版本变为使用该程序集的另一个版本。 例如，在为并行程序集部署 Bug 修复或安全修复并且要将所有应用程序重定向为使用已修复的版本时，可更改依赖项。 应用程序配置文件是一个 XML 文件，它对特定的应用程序进行重定向，使其从使用并行程序集的一个版本变为使用该程序集的另一个版本。 你可使用应用程序配置文件以重定向特定的应用程序，使其使用不同于在发行者配置文件中定义的并行程序集的版本。 有关详细信息，请参阅[配置](/windows/desktop/SbsCs/configuration)。  
  
## <a name="visual-c-libraries"></a>Visual C++ 库  
 在 Visual Studio 2005 和 Visual Studio 2008 中，可再发行库（如 ATL、MFC、CRT、标准 C++、OpenMP 和 MSDIA）已作为共享的并行程序集部署到本机程序集缓存中。 在当前版本中，可再发行库使用集中部署。 默认情况下，使用 Visual C++ 生成的所有应用程序在生成时都将清单嵌入到最终二进制文件中，该清单将描述此二进制文件在 Visual C++ 库中的依赖项。 若要了解 Visual C++ 应用程序的清单生成，请参阅 [Understanding Manifest Generation for C/C++ Programs](../build/understanding-manifest-generation-for-c-cpp-programs.md)。 对于静态链接到自身使用的库的应用程序，或链接到使用本地部署的库的应用程序，清单不是必需的。 有关部署的更多信息，请参阅 [Deployment in Visual C++](../ide/deployment-in-visual-cpp.md)。  
  
## <a name="see-also"></a>请参阅  
 [生成 C/C++ 独立应用程序和并行程序集](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)