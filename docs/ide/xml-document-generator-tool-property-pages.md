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
ms.openlocfilehash: 411bc96f00215ff9f90d8601387ab6bec5a7dc78
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/11/2019
ms.locfileid: "57740894"
---
# <a name="xml-document-generator-tool-property-pages"></a>“XML 文档生成器工具”属性页

“XML 文档生成器工具”属性页公开 xdcmake.exe 的功能。 如果源代码包含文档注释，并且指定了 [/doc（处理文档注释）(C/C++)](../build/reference/doc-process-documentation-comments-c-cpp.md)，则 xdcmake.exe 将 .xdc 文件合并到 .xml 文件中。 有关如何将文档注释添加到源代码的详细信息，请参阅[建议的文档注释标记](../ide/recommended-tags-for-documentation-comments-visual-cpp.md)。

> [!NOTE]
>  开发环境（属性页）中的 xdcmake.exe 选项与在命令行使用 xdcmake.exe 时的选项有所不同。 有关如何在命令行使用 xdcmake.exe 的详细信息，请参阅 [XDCMake 参考](../ide/xdcmake-reference.md)。

## <a name="uielement-list"></a>UIElement 列表

- **取消显示启动版权标志**

   取消显示版权消息。

- **附加文档文件**

   想让项目系统从中查找 xdc 文件的附加目录。 xdcmake 将始终查找由项目生成的 .xdc 文件。 可以指定多个目录。

- **输出文档文件**

   .xml 输出文件的名称和目录位置。 有关如何使用宏来指定目录位置的详细信息，请参阅[用于生成命令和属性的常用宏](../ide/common-macros-for-build-commands-and-properties.md)。

- **文档库依赖项**

   如果项目与解决方案中的 .lib 项目有依赖关系，则可以将 .lib 项目中的 .xdc 文件处理至当前项目的 .xml 文件中。

## <a name="see-also"></a>请参阅

[属性页](../ide/property-pages-visual-cpp.md)<br>
[属性页](../ide/property-pages-visual-cpp.md)
