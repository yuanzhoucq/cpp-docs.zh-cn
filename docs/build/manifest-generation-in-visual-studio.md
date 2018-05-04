---
title: Visual Studio 中的清单生成 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- manifests [C++]
ms.assetid: 0af60aa9-d223-42cd-8426-b3fc543a2a81
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 73b5cbe631d078dd6ee27b4f7e0a97503c36638b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="manifest-generation-in-visual-studio"></a>Visual Studio 中的清单生成
可以在项目中控制生成清单文件的特定项目**属性页**对话框。 上**配置属性**选项卡上，单击**链接器**，然后**清单文件**，然后**生成清单**。 默认情况下，新项目的项目属性将设置为生成清单文件。 但是很可能禁用生成的清单项目使用**生成清单**项目属性。 当此属性设置为**是**，生成此项目的清单。 则链接器忽略程序集信息时解决应用程序代码的依赖关系，并且不生成清单。  
  
 Visual Studio 中的生成系统允许要嵌入到最终二进制的应用程序文件，或作为外部文件生成的清单。 此行为由控制**嵌入清单**选项**项目属性**对话框。 若要设置此属性，打开**清单工具**节点，然后选择**输入和输出**。 如果未嵌入清单，它作为外部文件生成并保存在最终二进制文件所在的目录。 如果清单嵌入时，Visual Studio 会嵌入最终的清单使用以下过程：  
  
1.  源代码编译到对象文件后，链接器将收集从属程序集的信息。 时将链接到最终二进制文件，链接器生成的中间清单的更高版本用于生成最终的清单。  
  
2.  生成中间清单并链接已完成后，将执行清单工具合并最终清单并将其保存为外部文件。  
  
3.  项目生成系统，然后检测到该清单工具生成的清单是否包含不同于已在二进制文件中嵌入的清单的信息。  
  
4.  如果将清单嵌入在二进制文件是不同于生成的清单工具的清单或二进制文件不包含嵌入的清单，Visual Studio 将调用链接器一次嵌入二进制文件中作为外部的清单文件资源。  
  
5.  如果将清单嵌入在二进制文件是由清单工具生成的清单相同，生成将继续到下一步的生成步骤。  
  
 清单嵌入到最终二进制文件作为文本资源，可通过为 Visual Studio 中的文件打开到最终二进制文件。 若要确保清单指向正确的库，请按照中所述的步骤[了解 Visual c + + 应用程序的依赖关系](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md)或按照中所述的建议[故障排除](../build/troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md)部分。  
  
## <a name="see-also"></a>请参阅  
 [如何： 将 C/c + + 应用程序清单嵌入](../build/how-to-embed-a-manifest-inside-a-c-cpp-application.md)   
 [有关私有程序集](http://msdn.microsoft.com/library/ff951638)   
 [清单工具](http://msdn.microsoft.com/library/aa375649)   
 [了解 C/C++ 程序的清单生成](../build/understanding-manifest-generation-for-c-cpp-programs.md)