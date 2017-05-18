---
title: "链接器工具错误 LNK1104 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK1104
dev_langs:
- C++
helpviewer_keywords:
- LNK1104
ms.assetid: 9ca6f929-0efc-4055-8354-3cf5b4e636dc
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 128bd124c2536d86c8b673b54abc4b5505526b41
ms.openlocfilehash: c6121f598bc2913b65fe781b07bcc27e6b55375b
ms.contentlocale: zh-cn
ms.lasthandoff: 05/10/2017

---
# <a name="linker-tools-error-lnk1104"></a>链接器工具错误 LNK1104
无法打开文件*filename*  
  
链接器无法打开指定的文件。  
  
## <a name="possible-causes-and-solutions"></a>可能的原因和解决方案
  
链接器尝试打开以进行读取或写入的文件时，可以出现此错误。 此问题的最常见原因是该文件不存在，无法找到目录之一中链接器搜索时，或正在使用，另一个进程锁定。 较不常见的是，你可能已用完磁盘空间、 文件可能太大、 文件的路径可能太长，或你可能没有权限访问该文件。  

请检查这些常见的问题之一︰  

-   当你尝试重新生成你的应用程序已在运行。 如果无法打开的文件是可执行文件或调试如.pdb 文件，这是一个常见原因。 若要解决此问题，请停止该程序，并将其从调试器卸载之前再次生成。  
  
-   文件*filename*生成的解决方案，但尚不存在时链接器尝试访问它。 这可能发生在一个项目依赖于另一个项目以生成此文件，但不是按正确的顺序生成项目时。 若要解决此问题，请确保你项目的引用设置中的项目中使用该文件，因此需要提供之前生成缺少的文件。 有关详细信息，请参阅[Visual c + + 项目中添加引用](../../ide/adding-references-in-visual-cpp-projects.md)和[管理项目中的引用](/visualstudio/ide/managing-references-in-a-project)。  
  
-   文件名或命令行上或 #pragma lib 指令中指定的路径不正确，或者路径具有无效的驱动器规范。 请检查拼写，并验证该文件存在在指定的位置。  
  
-   如果使用 Visual Studio IDE 生成项目从另一台计算机复制的则库的安装位置可能不同。 检查库目录属性[VC + + 目录属性页](../../ide/vcpp-directories-property-page.md)和根据需要进行更新。 若要查看和编辑在 IDE 中设置的当前库路径，选择库目录属性的下拉列表控件，然后选择**编辑**。 **计算值**部分的库目录对话框中列出当前搜索库文件的路径。  
  
-   如果你正在生成使用较旧版本的 Visual Studio 创建的项目，平台工具集和该版本的库可能不会不安装。 若要解决此问题，您具有两个选项︰ 你可以升级项目以使用你已安装的当前平台工具集，或者可以安装的较旧的工具集和生成项目保持不变。 有关详细信息，请参阅[从早期版本的 Visual c + + 升级项目](../../porting/upgrading-projects-from-earlier-versions-of-visual-cpp.md)和[使用本机多目标在 Visual Studio 中生成旧项目](../../porting/use-native-multi-targeting.md)。
  
-   未安装用于当前项目配置或平台工具集的库。 请验证中指定的平台工具集和 Windows SDK[常规属性页](../../ide/general-property-page-project.md)安装为你的项目，并验证是否在指定的库目录中提供了所需的库[VC + + 目录属性页](../../ide/vcpp-directories-property-page.md)的配置设置。 单独设置调试和发布配置，因此如果一个 build 的工作原理，但其他会导致错误，请确保设置正确无误，并为这两种配置安装所需的工具和库。  
  
-   指向 Windows SDK 的路径已过期。 如果已安装的版本比你的 Visual Studio 版本新的 Windows sdk，请确保中指定的路径[VC + + 目录属性页](../../ide/vcpp-directories-property-page.md)更新以匹配新的 SDK。 如果你使用开发人员命令提示，请确保初始化环境变量的批处理文件，将更新为新的 SDK 路径。  
  
-   另一个程序可能已打开该文件，链接器无法向其写入。 防病毒程序通常暂时阻止对新创建的文件的访问。 若要解决此问题，请尝试从防病毒扫描程序中排除项目生成目录。  
  
-   如果你使用的并行生成选项，则可能 Visual Studio 已锁定另一个线程上的文件。 要解决此问题，请验证未生成的同一个代码对象或库在多个项目中，并且你使用的生成依赖关系或项目引用来选取你的项目中生成的二进制文件。  
  
-   具有不正确的 LIB 环境变量。 在命令行版本中，验证 LIB 环境变量已设置且包含你使用的库的所有目录。 在 IDE 中 LIB 变量属性设置的库目录上[VC + + 目录属性页](../../ide/vcpp-directories-property-page.md)。 请确保所有此处列出了包含所需的库的目录。 如果你需要提供库目录可重写的标准库目录，则可以使用[/LIBPATH](../../build/reference/libpath-additional-libpath.md)) 在命令行中或你的项目的链接器属性页中的附加库目录属性上的选项。  
  
-   在项目的属性页对话框中指定单独的库，必须用空格，而不是逗号分隔库名称。  
  
-   路径*filename*超过 260 个字符。 更改名称或重新排列你的目录结构，如果需要缩短对所需文件的路径。  
  
-   该文件是太大。 库或对象的文件超过千兆字节的大小可能在 32 位链接的情况下会导致问题。 此问题的可能解决方法是使用 64 位工具集。 有关如何执行此操作在命令行的详细信息，请参阅[如何︰ 启用 64 位 Visual c + + 工具集在命令行上的](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md)。 有关如何执行此操作在 IDE 中的信息，请参阅[与 64 位编译器和工具使用 MSBuild](../../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md#using-msbuild-to-build-your-project)和此堆栈溢出文章︰[如何使 Visual Studio 中使用本机 amd64 工具链](http://stackoverflow.com/questions/19820718/how-to-make-visual-studio-use-the-native-amd64-toolchain/23793055)。  
  
-   具有访问没有足够的文件权限*filename*。 可能的原因是访问受保护的系统目录中的库文件或使用其他具有其原始的权限的用户复制文件设置。 若要解决此问题，请将文件移动到可写的项目目录中。 如果该文件可写目录中，但具有访问权限，你可以使用管理员命令提示符并运行 takeown.exe 命令，以获得的文件的所有权。  
  
-   你没有足够的磁盘空间。 链接器在多个用例中使用临时文件。 即使有足够的磁盘空间，一个非常大的链接可以消耗或片段的可用磁盘空间。 请考虑使用[/OPT （优化）](../../build/reference/opt-optimizations.md)选项; 不采取可传递的 comdat 消除读取所有对象文件多次。  
  
-   如果*filename*名为 LNK*n*、 即生成链接器为临时文件的文件名、 TMP 环境变量中指定的目录可能不存在，或为 TMP 环境变量可指定多个目录。 只能将一个目录路径应为 TMP 环境变量指定。  
  
-   如果库名称出现错误消息，并且你最近刚从之前的 Microsoft Visual C++ 开发系统中移植了 .mak 文件，库名称可能不再有效。 确保库名称正确无误，且仍存在于指定的位置，或更新为指向新位置的 LIB 路径。  

