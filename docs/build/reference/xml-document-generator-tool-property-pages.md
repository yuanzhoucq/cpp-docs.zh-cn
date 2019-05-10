---
title: “XML 文档生成器工具”属性页
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCXDCMakeTool.ValidateIntelliSense
- VC.Project.VCXDCMakeTool.SuppressStartupBanner
- VC.Project.VCXDCMakeTool.DocumentLibraryDependencies
- VC.Project.VCXDCMakeTool.OutputDocumentFile
- VC.Project.VCXDCMakeTool.AdditionalDocumentFiles
ms.assetid: 645912b5-197a-4c36-ba58-64df09444ca0
ms.openlocfilehash: c99677d7fc53ae3343e15e54997fe0101322fbcf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62316153"
---
# <a name="xml-document-generator-tool-property-pages"></a>“XML 文档生成器工具”属性页

“XML 文档生成器工具”属性页公开 xdcmake.exe 的功能。 如果源代码包含文档注释，并且指定了 [/doc（处理文档注释）(C/C++)](doc-process-documentation-comments-c-cpp.md)，则 xdcmake.exe 将 .xdc 文件合并到 .xml 文件中。 有关如何将文档注释添加到源代码的详细信息，请参阅[建议的文档注释标记](recommended-tags-for-documentation-comments-visual-cpp.md)。

> [!NOTE]
>  开发环境（属性页）中的 xdcmake.exe 选项与在命令行使用 xdcmake.exe 时的选项有所不同。 有关如何在命令行使用 xdcmake.exe 的详细信息，请参阅 [XDCMake 参考](xdcmake-reference.md)。

## <a name="uielement-list"></a>UIElement 列表

- **取消显示启动版权标志**

   取消显示版权消息。

- **附加文档文件**

   想让项目系统从中查找 xdc 文件的附加目录。 xdcmake 将始终查找由项目生成的 .xdc 文件。 可以指定多个目录。

- **输出文档文件**

   .xml 输出文件的名称和目录位置。 请参阅[用于常见宏生成命令和属性](common-macros-for-build-commands-and-properties.md)使用宏来指定的目录位置的信息。

- **文档库依赖项**

   如果项目与解决方案中的 .lib 项目有依赖关系，则可以将 .lib 项目中的 .xdc 文件处理至当前项目的 .xml 文件中。

## <a name="see-also"></a>请参阅

[C++项目属性页引用](property-pages-visual-cpp.md)