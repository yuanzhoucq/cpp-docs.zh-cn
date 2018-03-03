---
title: "在 Visual c + + 项目中添加引用 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.References
dev_langs:
- C++
helpviewer_keywords:
- Add References Dialog Box (C++)
- .NET Framework (C++), Add References Dialog Box
ms.assetid: 12b8f571-0f21-40b3-9404-5318a57e9cb5
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7bacb5663d8e06ee5a10629c547de6f96219697e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="adding-references-in-visual-c-projects"></a>在 Visual C++ 项目中添加引用
程序调用到其他二进制文件（如 DLL、Windows 运行时组件、扩展 SDK、COM 组件和 .NET 程序集）中的 API 的情况非常普遍。 程序找到其他此类库的方式取决于项目的类型，以及二进制文件的类型。  
  
 在本机 C++ 项目中，如果你正在使用并非由解决方案中其他项目生成的本机 DLL 或 COM 组件，你将使用 LoadLibrary 或 CoCreateInstance 来指定指向二进制文件的路径，或者让系统通过查找定义明确的特定位置来找到它。  
  
 在其他类型的项目（如 UWP 项目或 C++/CLI 项目）中，或当二进制文件由解决方案中其他项目生成时，你可将“引用”  添加到程序集、组件或项目。   引用在本质上是一组数据，让你的程序可以找到二进制文件并与其通信。       在你添加引用时，Visual Studio 会处理低级别的详细信息。 若要将引用从 c + + 项目设置为.NET Frameworkassemblies (C + + /cli 仅)、 COM 组件，包括你的解决方案中的其他项目共享的项目，或连接的服务，右键单击**引用**中节点**解决方案资源管理器**弹出**引用管理器**。 你在引用管理器中的所见内容有所差异，具体取决于你的项目类型。  
  
 在本机 C++ 项目 (ATL) 中， *引用* 的理念只适用于解决方案中的其他项目（包括共享项目），因此你只能在“引用管理器” 中看到这些内容：  
  
 ![Visual C# 43; &#43;引用管理器 &#40;ATL 项目 &#41;] (../ide/media/visual-c---reference-manager--atl-projects-.png "Visual c + + 引用管理器 （ATL 项目）")  
  
 在 C++/CLI 或通用 Windows 平台项目中，引用的理念适用于解决方案中的其他项目，以及更多类型的二进制文件。  这些中公开的全部**引用管理器**。
  
## <a name="reference-properties"></a>引用属性  
 每类引用均有属性。 你可以采用以下两种方式来查看属性：在解决方案资源管理器中选择引用并按“Alt + Enter” ，或者右键单击并选择“属性” 。 一些属性为只读属性，而一些可进行修改。 然而，你通常无需手动修改这些属性。  
  
### <a name="activex-reference-properties"></a>ActiveX 引用属性  
 ActiveX 引用属性仅可用于对 COM 组件的引用。 只有在“引用”  窗格中选中了 COM 组件时，才会显示这些属性。 这些属性不可修改。  
  
 **控件完整路径**  
 显示所引用控件的目录路径。  
  
 **控件 GUID**  
 显示 ActiveX 控件的 GUID。  
  
 **控件版本**  
 显示所引用的 ActiveX 控件的版本。  
  
 **类型库名称**  
 显示所引用的类型库的名称。  
  
 **包装工具**  
 显示用于从所引用的 COM 库或 ActiveX 控件中生成互操作程序集的工具。  
  
### <a name="assembly-reference-properties"></a>程序集引用属性  
 程序集引用属性是仅适用于引用.NET Frameworkassemblies 在 C + + /cli 项目。 仅当.NET Frameworkassembly 中选择时，会显示这些属性**引用**窗格。 这些属性不可修改。  
  
 **相对路径**  
 显示项目目录到所引用程序集的相对路径。  
  
### <a name="build-properties"></a>生成属性  
 以下属性可用于各种类型的引用。 它们使你可以指定如何用引用进行生成。  
  
 **复制本地**  
 指定是否在生成期间自动将所引用的程序集复制到目标位置。  
  
 **复制本地附属程序集**  
 指定是否在生成期间将所引用程序集的附属程序集复制到目标位置。 仅在“复制本地”  为 `true`时使用。  
  
 **引用程序集输出**  
 指定在生成过程中使用此程序集。 若为 `true`，则在生成期间在编译器命令行上使用此程序集。  
  
### <a name="project-to-project-reference-properties"></a>项目到项目引用属性  
 以下属性定义从“引用”  窗格中选中的项目到同一解决方案中另一项目的 **项目到项目引用** 。 有关详细信息，请参阅[管理项目中的引用](/visualstudio/ide/managing-references-in-a-project)。  
  
 **链接库依赖项**  
 此属性为 **True**时，项目系统将独立项目生成的 .lib 文件链接到相关项目。 通常，你将指定 **True**。  
  
 **项目标识符**  
 唯一标识独立项目。 属性值是不可修改的内部系统 GUID。  
  
 **使用库依赖项输入**  
 当此属性为 **False**时，项目系统不会将库中由独立项目生成的 .obj 文件链接到相关项目。 因此，此值会禁用增量链接。 你通常将指定 **False** ，因为如果存在多个独立项目，则构建应用程序可能会花很长时间。  
  
### <a name="reference-properties"></a>引用属性  
 以下属性位于 COM 和 .NET 程序集引用上，且不可修改。  
  
 **程序集名称**  
 显示所引用的程序集的程序及名称。  
  
 **区域性**  
 显示所选引用的区域性。  
  
 **说明**  
 显示所选引用的描述。  
  
 **完整路径**  
 显示所引用的程序集的目录路径。  
  
 **标识**  
 对于.NET Frameworkassemblies 中，将显示的完整路径。 对于 COM 组件，显示 GUID。  
  
 **标签**  
 显示引用的标签。  
  
 **名称**  
 显示引用的名称。  
  
 **公钥标记**  
 显示用于标识所引用的程序集的公钥标记。  
  
 **强名称**  
 如果所引用程序集具有强名称，则为 `true`。 强名称程序集的版本是唯一的。  
  
 **Version**  
 显示所引用的程序集的版本。  
  
## <a name="see-also"></a>请参阅  
 [属性页](../ide/property-pages-visual-cpp.md)   
 [使用项目属性](../ide/working-with-project-properties.md)