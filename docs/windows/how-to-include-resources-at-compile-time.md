---
title: 如何： 将资源包括在编译时 （c + +）
ms.date: 11/04/2016
f1_keywords:
- vs.resvw.resource.including
- vc.resvw.resource.including
helpviewer_keywords:
- comments [C++], compiled files
- resources [C++], including at compile time
- projects [C++], including resources
- '#include directive'
- include directive (#include)
ms.assetid: 357e93c2-0a29-42f9-806f-882f688b8924
ms.openlocfilehash: 8d6cfc2f18ec12354619c01ed79b740554ec4d95
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50495142"
---
# <a name="how-to-include-resources-at-compile-time"></a>如何：在编译时包含资源

通常可简单且方便地在一个资源脚本 (.rc) 文件中使用所有资源的默认安排。 但是，您可以将资源添加其他文件中向当前项目在编译时列出相关**编译时指令**框中[资源包括对话框的](../windows/resource-includes-dialog-box.md)。

将资源置于主 .rc 文件之外的文件中有以下几个原因：

- 向保存 .rc 文件时不会删除的资源语句添加注释。

   资源编辑器不直接读取.rc 或`resource.h`文件。 资源编译器将它们编译成由资源编辑器使用的 .aps 文件。 该文件是一个编译步骤，只存储符号数据。 与普通编译过程一样，非符号信息（如注释）在编译过程中将被放弃。 每当.aps 文件与.rc 文件获取同步，重新生成.rc 文件 (例如，保存时，资源编辑器将覆盖.rc 文件和`resource.h`文件)。 对资源本身所做的任何更改依然包含在 .rc 文件中，但一旦覆盖 .rc 文件就总会丢失注释。

- 包含已开发和测试并且无需进一步修改的资源。 （包含在内但没有 .rc 扩展名的任何文件都不可通过资源编辑器进行编辑。）

- 包含正由几个不同项目使用，或属于源代码版本控制系统，因而必须存在于一个修改会影响所有项目的中心位置的资源。

- 包括采用自定义格式的资源（如 RCDATA 资源）。 RCDATA 资源可能具有特殊要求。 例如，不能使用表达式作为 nameID 字段的值。 请参阅 Windows SDK 文档了解详细信息。

如果满足下列任一条件的现有.rc 文件中有一些部分，应将部分放在一个或多个单独的.rc 文件并将其包含在你的项目使用[资源包括对话框的](../windows/resource-includes-dialog-box.md)。 *Projectname*.rc2 文件创建一个新的项目的 \res 子目录中用于此目的。

### <a name="to-include-resources-in-your-project-at-compile-time"></a>编译时在项目中包含资源

1. 将资源置于具有唯一文件名的资源脚本文件中。 不要使用*projectname*.rc，因为这是用于主资源脚本文件的文件名称。

2. 右键单击.rc 文件 (在[资源视图](../windows/resource-view-window.md))，然后选择**资源包括**从快捷菜单。

3. 在中**编译时指令**框中，添加[#include](../preprocessor/hash-include-directive-c-cpp.md)编译器指令，以在开发环境中在主资源文件中包含新的资源文件。

   采用这种方式包含的文件中的资源会在编译时成为可执行文件的一部分。 它们在你处理项目的主 .rc 文件时不可直接进行编辑或修改。 需要单独打开包含的 .rc 文件。 包含在内但没有 .rc 扩展名的任何文件都不可通过资源编辑器进行编辑。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[资源文件](../windows/resource-files-visual-studio.md)<br/>
[资源编辑器](../windows/resource-editors.md)