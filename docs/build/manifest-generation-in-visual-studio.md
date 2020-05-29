---
title: Visual Studio 中的清单生成
ms.date: 11/04/2016
helpviewer_keywords:
- manifests [C++]
ms.assetid: 0af60aa9-d223-42cd-8426-b3fc543a2a81
ms.openlocfilehash: f055e3d16dfc0ea4320883210458ae10daebdc45
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273349"
---
# <a name="manifest-generation-in-visual-studio"></a>Visual Studio 中的清单生成

可以在项目“属性页”对话框中控制特定项目的清单文件的生成  。 在“配置属性”选项卡上，单击“链接器”，然后单击“清单文件”，再单击“生成清单”     。 默认情况下，新项目的项目属性设置为生成清单文件。 不过，可使用项目的“生成清单”属性禁用项目的清单生成  。 如果此属性设置为“是”，则将生成此项目的清单  。 否则，链接器在解决应用程序代码的依赖项时会忽略程序集信息，并且不生成清单。

Visual Studio 中的生成系统允许将清单嵌入到最终的二进制应用程序文件中，或作为外部文件生成。 此行为由“项目属性”对话框中的“嵌入清单”选项控制   。 要设置此属性，请打开“清单工具”节点，然后选择“输入和输出”   。 如果不嵌入清单，则它将被生成为外部文件，并保存在与最终二进制文件相同的目录中。 如果清单嵌入，Visual Studio 将使用以下过程嵌入最终清单：

1. 将源代码编译为对象文件后，链接器将收集依赖程序集信息。 在链接最终二进制文件时，链接器会生成一个中间清单，稍后该清单将用于生成最终清单。

1. 生成中间清单并完成链接后，将执行清单工具以合并成一个最终清单，并将它另存为外部文件。

1. 然后，项目生成系统将进行检测，确定在由清单工具生成的清单中，其信息是否有别于已嵌入二进制文件中的清单所包含的信息。

1. 如果二进制文件中嵌入的清单不同于清单工具生成的清单，或二进制文件中不包含嵌入的清单，则 Visual Studio 将再次调用链接器，将外部清单文件作为资源嵌入到二进制文件中。

1. 如果二进制文件中嵌入的清单与清单工具生成的清单相同，则生成系统将继续下面的生成步骤。

清单会作为文本资源嵌入到最终二进制文件中，你可通过在 Visual Studio 中将最终二进制文件作为文件打开来查看该清单。 若要确保清单指向正确的库，请按照[了解 Visual C++ 应用程序的依赖关系](../windows/understanding-the-dependencies-of-a-visual-cpp-application.md)中的所述步骤或按照[故障排除](troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md)部分中的建议步骤进行操作。

## <a name="see-also"></a>请参阅

[了解 C/C++ 程序的清单生成](understanding-manifest-generation-for-c-cpp-programs.md)
