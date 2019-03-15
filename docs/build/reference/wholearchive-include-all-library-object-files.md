---
title: /WHOLEARCHIVE （包括所有库对象文件）
ms.date: 11/04/2016
ms.assetid: ee92d12f-18af-4602-9683-d6223be62ac9
ms.openlocfilehash: db99816b18110b424647603196040997044e7fbd
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57808646"
---
# <a name="wholearchive-include-all-library-object-files"></a>/WHOLEARCHIVE （包括所有库对象文件）

Force 链接器在链接的可执行文件中的静态库中包括所有对象文件。

## <a name="syntax"></a>语法

> /WHOLEARCHIVE[:*library*]

## <a name="remarks"></a>备注

/WHOLEARCHIVE 选项将强制链接器包括每个对象文件从指定的静态库，或如果未不指定任何库，从所有静态库链接到指定命令。 若要指定多个库的 /WHOLEARCHIVE 选项，可以在链接器命令行上使用多个 /WHOLEARCHIVE 切换。 默认情况下，链接器包括对象文件中链接的输出仅当它们导出符号引用的可执行文件中的其他对象文件。 /WHOLEARCHIVE 选项使链接器将在静态库中存档，如同它们在链接器命令行上单独指定的所有对象文件。

/WHOLEARCHIVE 选项可用于重新导出静态库中的所有符号。 这可以确保所有的库代码、 资源和元数据都包含一个组件创建从多个静态库时。 如果看到警告 LNK4264 创建静态库时包含导出为 Windows 运行时组件，此库链接到另一个组件或应用程序时使用 /WHOLEARCHIVE 选项。

在 Visual Studio 2015 Update 2 中引入 /WHOLEARCHIVE 选项。

### <a name="to-set-this-linker-option-in-visual-studio"></a>在 Visual Studio 中设置此链接器选项

1. 打开项目“属性页”  对话框。 有关详细信息，请参阅[Visual Studio 中的设置 c + + 编译器和生成属性](../working-with-project-properties.md)。

1. 选择**命令行**下的属性页**配置属性**，**链接器**。

1. /WHOLEARCHIVE 将选项添加到**其他选项**文本框。

## <a name="see-also"></a>请参阅

[MSVC 链接器引用](linking.md)<br/>
[MSVC 链接器选项](linker-options.md)
