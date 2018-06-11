---
title: 如何：组织生成的项目输出文件 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Visual C++, output files
- output files, organizing
ms.assetid: 521d95ea-2dcc-4da0-b5eb-ac3e57941446
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5058493e93a89e64c87ef52b73ff8fe3272f8f99
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2018
ms.locfileid: "34705340"
---
# <a name="how-to-organize-project-output-files-for-builds"></a>如何：组织生成的项目输出文件
本主题介绍组织项目输出文件的最佳做法。 如果没有正确设置项目输出文件，可能会出现生成错误。 本主题还概述每个替代选项在组织项目输出文件方面的优缺点。  
  
## <a name="referencing-clr-assemblies"></a>引用 CLR 程序集  
  
#### <a name="to-reference-assemblies-with-using"></a>使用 #using 引用程序集  
  
1.  使用 #using 指令（例如 `#using <System.Data.dll>`）可以直接从代码引用程序集。 有关详细信息，请参阅 [#using 指令](../preprocessor/hash-using-directive-cpp.md)。  
  
     所指定的文件可以是 dll、.exe、.netmodule 或 .obj，只要文件是以 MSIL 生成的即可。 可以引用以任何语言生成的组件。 使用此选项将能访问 IntelliSense，因为会从 MSIL 中提取元数据。 所涉及的文件必须位于项目的路径中，否则不会编译项目，并且也无法使用 IntelliSense。 若要确定文件是否在路径中，最简单的方式是右键单击 #using 行并选择“打开文档”命令。 如果未找到文件，你将收到通知。  
  
     如果不希望放置文件的完整路劲，可以使用“/AI”编译器选项来编辑 #using 引用的搜索路径。 有关详细信息，请参阅 [/AI（指定元数据目录）](../build/reference/ai-specify-metadata-directories.md)。  
  
#### <a name="to-reference-assemblies-with-fu"></a>使用 /FU 引用程序集  
  
1.  除从代码文件直接引用程序集（如上所述）以外，还可以使用“/FU”编译器选项。 此方法的优点是你不必将单独的 #using 语句添加到每个引用给定程序集的文件。  
  
     若要设置此选项，请打开项目的“属性页”。 展开“配置属性”节点，然后展开“C/C++”节点并选择“高级”。 在“强制 #using”旁边添加所需程序集。 有关详细信息，请参阅 [/FU（命名强制 #using 文件）](../build/reference/fu-name-forced-hash-using-file.md)。  
  
#### <a name="to-reference-assemblies-with-add-new-reference"></a>通过“添加新引用”来引用程序集  
  
1.  这是使用 CLR 程序集最简单的方法。 首先，请确保项目是使用“/clr”编译器选项编译的。 然后在“解决方案资源管理器”中右键单击项目，并选择“添加”、“引用”。 此时将出现“属性页”对话框。  
  
2.  从“属性页”对话框中选择“添加新引用”。 此时将出现一个对话框，其中列出了所有在当前项目中可用的 .NET、COM 和其他程序集。 选择所需程序集，然后单击“确定”。  
  
     设置项目引用后，将自动处理对应的依赖项。 此外，由于元数据是程序集的一部分，因此不需要添加头文件或者为从托管程序集使用的元素指定原型。  
  
## <a name="referencing-native-dlls-or-static-libraries"></a>引用本机 DLL 或静态库  
  
#### <a name="to-reference-native-dlls-or-static-libraries"></a>引用本机 DLL 或静态库  
  
1.  在代码中使用 #include 指令引用适当的头文件。 头文件必须位于包含路径中，或者是当前项目的一部分。 有关详细信息，请参阅 [#include 指令 (C/C++)](../preprocessor/hash-include-directive-c-cpp.md)。  
  
2.  还可以设置项目依赖项。 设置项目依赖项能保证两点。 首先能确保按正确顺序生成项目，从而让项目始终可以找到所需的依赖文件。 其次会将依赖项目的输出目录隐式添加至路径，这样能在链接时轻松找到文件。  
  
3.  若要部署应用程序，需要将 DLL 放置在适当的位置。 可以是以下位置之一：  
  
    1.  与可执行文件相同的路径。  
  
    2.  系统路径（环境变量“path”）中的任何位置。  
  
    3.  并行程序集中。 有关详细信息，请参阅[生成 C/C++ 并行程序集](../build/building-c-cpp-side-by-side-assemblies.md)。  
  
## <a name="working-with-multiple-projects"></a>使用多个项目  
 默认情况下，项目生成中的所有输出文件都创建在项目目录的子目录中。 目录的名称基于生成配置（例如调试或发布）。 为了让同级项目能互相引用，并且为了能成功地进行链接，每个项目必须显式地将其他项目输出目录添加到自己的路径中。 这将在设置项目依赖项时自动完成。 但是如果没有使用依赖项，则必须谨慎地处理此项操作，因为生成可能会很难管理。 例如，如果项目具备调试和发布配置，且包括来自同级项目的外部库，则应根据生成的配置使用不同的库文件。 所以对这些路径进行硬编码会非常困难。  
  
 所有重要的输出文件（例如可执行文件、增量链接器文件和 PDB 文件）都复制到常见的解决方案目录。 这样，在使用包含大量具备相同配置的 C++ 项目的解决方案时，会集中所有输出文件，以便简化链接和部署操作。 如果将这些文件保存在一起，可以确保它们的应用程序/库会按预期运行（因为能保证文件都在该路径中）。  
  
 部署到生成环境时，可能主要需要注意输出文件的位置。 在 IDE 中运行项目时，指向包括的库的路径无须与生成环境中的路径一致。 例如，如果你的代码中有 `#using "../../lib/debug/mylib.dll"` 但随后将 mylib.dll 部署进了不同的相对位置，则应用程序将在运行时出现故障。 若要防止此情况，应避免在代码的 #include 语句中使用相对路径。 最好确保必需的文件位于项目生成路径中，同样也请确保对应的生产文件也位于适当的位置。  
  
#### <a name="how-to-specify-where-output-files-go"></a>如何指定输出文件输出位置  
  
1.  可在项目的“属性页”中找到项目输出位置的设置。 展开“配置属性”旁边的节点，并选择“常规”。 可在“输出目录”旁指定输出位置。 有关详细信息，请参阅[“常规”属性页（项目）](../ide/general-property-page-project.md)。  
  
## <a name="see-also"></a>请参阅  
 [Visual C++ 项目类型](../ide/visual-cpp-project-types.md)