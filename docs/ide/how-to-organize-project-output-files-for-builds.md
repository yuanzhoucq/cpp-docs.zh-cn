---
title: 如何： 组织生成的项目输出文件 |Microsoft 文档
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
ms.openlocfilehash: a0d1e7f8ea67db0e87199e0c12128555fa039112
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-organize-project-output-files-for-builds"></a>如何：组织生成的项目输出文件
本主题描述用于组织项目输出文件的最佳做法。 生成时未正确设置项目输出文件，可以在发生错误。 本主题还概述了每种用于组织项目输出文件的替代方案的优缺点。  
  
## <a name="referencing-clr-assemblies"></a>引用 CLR 程序集  
  
#### <a name="to-reference-assemblies-with-using"></a>引用程序集与为 #using  
  
1.  你可以在代码中直接引用程序集，通过使用 #using 指令，如`#using <System.Data.dll>`。 有关详细信息，请参阅[#using 指令](../preprocessor/hash-using-directive-cpp.md)。  
  
     指定的文件可以是.dll、.exe、.netmodule 或.obj，只要它是在 MSIL 中。 可以采用任何语言生成引用的组件。 使用此选项，因为将从 MSIL 中提取元数据将具有 intellisense 的访问。 所涉及的文件必须位于项目; 路径否则为该项目将不进行编译和 Intellisense 将不可用。 确定文件是否位于路径中的简单办法是： 右击 #using 行，选择**打开的文档**命令。 如果找不到该文件，你将收到通知。  
  
     如果您不想要放置文件的完整路径，则可以使用 **/AI**编译器选项来编辑的搜索路径 #using 引用。 有关详细信息，请参阅 [/AI（指定元数据目录）](../build/reference/ai-specify-metadata-directories.md)。  
  
#### <a name="to-reference-assemblies-with-fu"></a>引用程序集使用 /FU  
  
1.  而不是引用程序集直接从代码文件中，按上文所述，你可以使用 **/FU**编译器选项。 此方法的优点是，则不需要添加单独 #using 语句引用给定程序集的每个文件。  
  
     若要设置此选项，打开**属性页**项目。 展开**配置属性**节点，然后展开**C/c + +** 节点，然后选择**高级**。 将所需的程序集添加旁边**强制 #using**。 有关详细信息，请参阅 [/FU（命名强制 #using 文件）](../build/reference/fu-name-forced-hash-using-file.md)。  
  
#### <a name="to-reference-assemblies-with-add-new-reference"></a>若要添加新引用与引用程序集  
  
1.  这是使用 CLR 程序集的最简单方法。 首先，请确保编译项目与 **/clr**编译器选项。 然后，右键单击项目从**解决方案资源管理器**和选择**添加**，**引用**。 **属性页**对话框将出现。  
  
2.  从**属性页**对话框中，选择**添加新引用**。 将显示一个对话框，列出所有.NET、 COM 和当前项目中可用的其他程序集。 选择所需的程序集，然后单击**确定**。  
  
     设置项目引用后，自动处理相应的依赖项。 此外，由于元数据是程序集的一部分，因此不无需添加标头文件或原型托管程序集中的正在使用的元素。  
  
## <a name="referencing-native-dlls-or-static-libraries"></a>引用本机 Dll 或静态库  
  
#### <a name="to-reference-native-dlls-or-static-libraries"></a>若要引用本机 Dll 或静态库  
  
1.  引用相应的标头文件中使用 #include 指令。 标头文件必须是包含路径或当前项目的一部分。 有关详细信息，请参阅[#include 指令 （C/c + +）](../preprocessor/hash-include-directive-c-cpp.md)。  
  
2.  你还可以设置项目依赖项。 设置项目依赖项保证了以下两点。 首先，它可确保，以便项目始终可以找到所需的依赖文件，按正确的顺序生成项目。 其次，它将隐式添加依赖项目的输出目录的路径，以便在链接时，可以轻松地找到文件。  
  
3.  若要部署应用程序，你将需要将 DLL 放置在适当的位置。 这可以是以下项之一：  
  
    1.  可执行文件所在的路径。  
  
    2.  在系统路径中的任意位置 (**路径**环境变量)。  
  
    3.  中的并行程序集。 有关详细信息，请参阅[构建 C/c + + 端并行程序集](../build/building-c-cpp-side-by-side-assemblies.md)。  
  
## <a name="working-with-multiple-projects"></a>使用多个项目  
 默认情况下，以便所有输出文件都创建项目目录的子目录中生成项目。 目录的名称为基于的生成配置 （例如调试或发布）。 为了使同级项目能够相互引用，每个项目必须显式添加到其路径在顺序中用于链接若要成功执行的其他项目输出目录。 设置项目依赖项时，这会自动完成。 但是，如果不使用依赖项，你必须仔细处理上述情况由于生成可能会很难管理。 例如，如果一个项目具有调试和发布配置，它包括从同级项目外部库，它应使用一个不同的库文件，具体取决于生成配置。 因此，这些路径进行硬编码可能会很棘手。  
  
 （如可执行文件、 增量链接器文件和 PDB 文件） 的所有重要的输出文件将复制到一个常见的解决方案目录中。 因此，在使用包含大量使用等效配置的 c + + 项目的解决方案，所有输出文件是集中在都一起以简化链接和部署。 您可以确保按预期如果它们将这些文件显示在一起 （因为保证文件都是在路径中），其应用程序/库将正常工作。  
  
 部署到生产环境时，输出文件的位置可以是主要问题。 在 IDE 中运行项目，时包括的库路径并不一定与生产环境中的相同。 例如，如果你有`#using "../../lib/debug/mylib.dll"`但然后在代码中将 mylib.dll 部署到不同的相对位置、 应用程序将在运行时失败。 若要防止此情况，应避免使用中的相对路径 #include 语句位于你的代码。 最好确保所需的文件的项目生成路径中，同样，确保相应的生产文件的位置是否正确。  
  
#### <a name="how-to-specify-where-output-files-go"></a>如何指定输出文件输出位置  
  
1.  项目的位置输出设置可在项目的**属性页**。 展开的节点旁边**配置属性**和选择**常规**。 输出位置指定旁边**输出目录**。 有关详细信息，请参阅[常规属性页 （项目）](../ide/general-property-page-project.md)。  
  
## <a name="see-also"></a>请参阅  
 [Visual C++ 项目类型](../ide/visual-cpp-project-types.md)