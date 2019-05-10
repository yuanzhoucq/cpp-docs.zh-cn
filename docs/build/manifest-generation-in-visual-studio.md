---
title: Visual Studio 中的清单生成
ms.date: 11/04/2016
helpviewer_keywords:
- manifests [C++]
ms.assetid: 0af60aa9-d223-42cd-8426-b3fc543a2a81
ms.openlocfilehash: f055e3d16dfc0ea4320883210458ae10daebdc45
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273349"
---
# <a name="manifest-generation-in-visual-studio"></a>Visual Studio 中的清单生成

在项目中，可以控制清单文件的特定项目的生成**属性页**对话框。 上**配置属性**选项卡上，单击**链接器**，然后**清单文件**，然后**生成清单**。 默认情况下新的项目的项目属性设置来生成清单文件。 但是就可以禁用生成的项目使用的清单**Generate Manifest**项目的属性。 当此属性设置为**是**，生成此项目的清单。 链接器时解析依赖项的应用程序代码中，则忽略程序集信息并不会生成清单。

在 Visual Studio 中的生成系统允许要嵌入到最终二进制应用程序文件，或作为外部文件生成的清单。 这种行为受**嵌入清单**选项**项目属性**对话框。 若要设置此属性，打开**清单工具**节点，然后选择**输入和输出**。 如果未嵌入清单，它是作为外部文件生成的保存在最终二进制文件所在的同一目录中。 如果清单嵌入，Visual Studio 会嵌入最终清单使用以下过程：

1. 对对象文件编译的源代码后，链接器将收集依赖程序集的信息。 时链接到最终二进制文件，链接器生成更高版本用于生成最终清单的中间清单。

1. 清单和链接的中间完成后，将执行的清单工具合并最终清单，并将其保存为外部文件。

1. 项目生成系统，然后检测到生成的清单工具的清单是否包含不同于已在二进制文件中嵌入的清单的信息。

1. 如果将清单嵌入在二进制文件是不同于生成的清单工具的清单或二进制文件不包含嵌入的清单，Visual Studio 将调用链接器一次嵌入二进制文件中作为外部清单文件资源。

1. 如果生成的清单工具的清单相同二进制文件中嵌入的清单，生成将继续到下一步的生成步骤。

清单嵌入到最终二进制文件作为文本资源，它可以查看通过打开 Visual Studio 中的文件的最终二进制文件。 若要确保清单指向正确的库，请按照中所述的步骤[了解视觉对象的依赖项C++应用程序](../windows/understanding-the-dependencies-of-a-visual-cpp-application.md)或按照中所述的建议[故障排除](troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md)部分。

## <a name="see-also"></a>请参阅

[了解 C/C++ 程序的清单生成](understanding-manifest-generation-for-c-cpp-programs.md)
