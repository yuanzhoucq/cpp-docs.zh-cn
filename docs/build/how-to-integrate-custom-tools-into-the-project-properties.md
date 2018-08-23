---
title: 如何： 将自定义工具集成到项目属性 |Microsoft 文档
ms.custom: ''
ms.date: 04/27/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- msbuild.cpp.howto.integratecustomtools
dev_langs:
- C++
helpviewer_keywords:
- 'msbuild (c++), howto: integrate custom tools'
ms.assetid: f32d91a4-44e9-4de3-aa9a-1c7f709ad2ee
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 00482aa2b4b700d15e46d0741e76dd17afc28419
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32368897"
---
# <a name="how-to-integrate-custom-tools-into-the-project-properties"></a>如何：将自定义工具集成到项目属性中
你可以将自定义工具选项添加到 Visual Studio**属性页**窗口是通过创建基础 XML 架构文件。  
  
 **配置属性**部分**属性页**窗口将显示名为的设置组*规则*。 每个规则包含一种工具或一组功能的设置。 例如，**链接器**规则包含链接器工具的设置。 规则中的设置可以细分为*类别*。  
  
 本文档说明如何在包含自定义工具的属性，以便在 Visual Studio 启动时加载属性的集目录中创建一个文件。 有关如何修改文件的信息，请参阅[平台性扩展性第 2 部分](http://go.microsoft.com/fwlink/p/?linkid=191489)Visual Studio 项目团队博客上。  
  
### <a name="to-add-or-change-project-properties"></a>若要添加或更改项目属性  
  
1.  在 XML 编辑器中，创建一个 XML 文件。  
  
2.  将文件保存在 Visual Studio 2017`VCTargets\1033`文件夹。 必须将每个版本的安装的 Visual Studio 2017 和每种语言的不同路径。 例如，在英语中的 Visual Studio Enterprise 版的文件夹路径是`%ProgramFiles%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\VC\VCTargets\1033`。 调整你的语言和 Visual Studio 版本的路径。 中的所有规则**属性页**窗口表示通过此文件夹中的 XML 文件。 请确保该文件唯一命名的文件夹中。  
  
3.  将内容复制`%ProgramFiles%\Microsoft Visual Studio\2017\<VS Edition>\Common7\IDE\VC\VCTargets\<LCID>\cl.xml`，请关闭它而不保存更改，然后将该内容粘贴在将新的 XML 文件中。 可以使用任何 XML 架构文件-这只是其中一个，因此你开始使用模板可以使用。  
  
4.  在新的 XML 文件中，修改根据你的要求的内容。 请确保更改**规则名称**和**Rule.DisplayName**文件顶部。  
  
5.  保存所做的更改并关闭该文件。  
  
6.  XML 文件中`%ProgramFiles%\Microsoft Visual Studio\2017\<VS Edition>\Common7\IDE\VC\VCTargets\<LCID>`Visual Studio 启动时加载。 因此，若要测试新文件，重新启动 Visual Studio。  
  
7.  在**解决方案资源管理器**，右键单击某个项目，然后单击**属性**。 在**属性页**窗口中的，在左窗格中，验证是否有你的规则的名称的新节点。  
  
## <a name="see-also"></a>请参阅  
 [MSBuild (Visual C++)](../build/msbuild-visual-cpp.md)
