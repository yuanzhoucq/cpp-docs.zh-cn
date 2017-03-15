---
title: "生成 C/C++ 并行程序集 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "并行应用程序 [C++]"
ms.assetid: 7fa20b16-3737-4f76-a0b5-1dacea19a1e8
caps.latest.revision: 18
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 生成 C/C++ 并行程序集
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[并行程序集](_win32_side_by_side_assemblies)是指应用程序在运行时可使用的资源的集合，如一组 DLL、Windows 类、COM 服务器、类型库或接口。  将 DLL 重新打包到程序集中的主要优点是，应用程序可以同时使用程序集的多个版本，且发布更新时可以为当前已安装的程序集提供服务。  
  
 Visual C\+\+ 应用程序可以在它的不同部分使用一个或若干个 DLL。  运行时，会将这些 DLL 加载到主进程并执行所需的代码。  应用程序依赖操作系统来定位所需的 DLL，了解必须加载的其他依赖 DLL，然后将它们与所需的 DLL 一起加载。  在早于 Windows XP、Windows Server 2003 和 Windows Vista 的 Windows 操作系统版本上，操作系统加载程序会在应用程序的本地文件夹或系统路径指定的另一个文件夹中搜索依赖 DLL。  在 Windows XP、Windows Server 2003 和 Windows Vista 上，操作系统加载程序还可以使用[清单](http://msdn.microsoft.com/library/aa375365)文件搜索依赖 DLL，并搜索包含这些 DLL 的并行程序集。  
  
 默认情况下，在使用 Visual Studio 生成 DLL 时，该 DLL 会有一个作为 RT\_MANIFEST 资源（ID 等于 2）嵌入的[应用程序清单](http://msdn.microsoft.com/library/aa374191)。  正如可执行文件一样，此清单描述该 DLL 在其他程序集中的依赖项。  此处假定此 DLL 不是并行程序集的一部分，且依赖于此 DLL 的应用程序将不会使用应用程序清单加载此 DLL，而是依靠操作系统加载程序在系统路径中查找此 DLL。  
  
> [!NOTE]
>  对于使用应用程序清单的 DLL 来说，将此清单作为资源（ID 等于 2）嵌入其中是十分重要的。  如果在运行时动态加载此 DLL（例如，使用 [LoadLibrary](http://msdn.microsoft.com/library/windows/desktop/ms684175) 函数），操作系统加载程序将加载 DLL 的清单中指定的依赖程序集。  在调用 `LoadLibrary` 期间，不会检查 DLL 的外部应用程序清单。  如果未嵌入此清单，则加载程序可能会尝试加载程序集的错误版本，或无法找到依赖程序集。  
  
 通过相应的[程序集清单](http://msdn.microsoft.com/library/aa374219)，可以将一个或若干个相关 DLL 重新打包到并行程序集中，该清单用于描述构成此程序集的文件、以及此程序集对于其他并行程序集的依赖性。  
  
> [!NOTE]
>  如果程序集包含一个 DLL，建议将程序集清单作为 ID 等于 1 的资源嵌入到该 DLL 中，并且让私有程序集与该 DLL 同名。  例如，如果该 DLL 的名称为 mylibrary.dll，则清单的 \<assemblyIdentity\>元素中使用的名称特性的值也可以是 mylibrary。  在某些情况下，如果库的扩展名不是 .dll（例如，MFC ActiveX 控件项目会创建 .ocx 库），则可以创建外部程序集清单。  在此情况下，程序集及其清单的名称必须不同于 DLL 的名称（例如，MyAssembly、MyAssembly.manifest 和 mylibrary.ocx）。  但是，仍然建议对这种库重命名，使其扩展名为 .dll，并将清单作为资源嵌入，以减少今后对此程序集的维护成本。  有关操作系统如何搜索私有程序集的更多信息，请参见[程序集搜索顺序](http://msdn.microsoft.com/library/aa374224)。  
  
 此更改允许将相应的 DLL 作为[私有程序集](_win32_private_assemblies)部署到应用程序本地文件夹中，或作为[共享程序集](https://msdn.microsoft.com/en-us/library/aa375996.aspx)部署到 WinSxS 程序集缓存中。  若要使此新程序集在运行时的行为准确无误，必须执行若干步骤；[创建并行程序集指南](http://msdn.microsoft.com/library/aa375155)中描述了这些步骤。  正确编写程序集后，可将此程序集作为共享程序集或私有程序集与依赖于它的应用程序一起进行部署。  将并行程序集作为共享程序集安装时，可以按照[在 Windows XP 上安装 Win32 程序集以实现并行共享](http://msdn.microsoft.com/library/aa369532)中介绍的指南进行操作，也可以使用[合并模块](http://msdn.microsoft.com/library/aa369820)。  将并行程序集作为私有程序集安装时，仅需将相应的 DLL、资源和程序集清单作为安装过程的一部分复制到目标计算机上的应用程序本地文件夹中，这样可确保加载程序在运行时可以找到此程序集（请参见[程序集搜索顺序](http://msdn.microsoft.com/library/aa374224)）。  另一种方法是使用 [Windows Installer](http://msdn.microsoft.com/library/cc185688)，并按照[在 Windows XP 上安装 Win32 程序集以供应用程序专用](http://msdn.microsoft.com/library/aa369534)中介绍的指南进行操作。  
  
## 请参阅  
 [部署示例](../ide/deployment-examples.md)   
 [生成 C\/C\+\+ 独立应用程序](../build/building-c-cpp-isolated-applications.md)   
 [生成 C\/C\+\+ 独立应用程序和并行程序集](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)