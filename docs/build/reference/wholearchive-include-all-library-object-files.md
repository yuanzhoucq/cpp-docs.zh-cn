---
title: /WHOLEARCHIVE （包括所有库对象文件）
ms.date: 02/12/2020
ms.assetid: ee92d12f-18af-4602-9683-d6223be62ac9
ms.openlocfilehash: 95685c9c0dfde45c42449bbcad67228a0e21b36a
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2020
ms.locfileid: "77257528"
---
# <a name="wholearchive-include-all-library-object-files"></a>/WHOLEARCHIVE （包括所有库对象文件）

强制链接器在链接的可执行文件中包含静态库中的所有对象文件。

## <a name="syntax"></a>语法

> **/WHOLEARCHIVE**\
> **/WHOLEARCHIVE：** _库_

### <a name="arguments"></a>参数

*库*\
静态库的可选路径名。 链接器包含此库中的每个对象文件。

## <a name="remarks"></a>备注

/WHOLEARCHIVE 选项强制链接器包含指定的静态库中的每个对象文件，或者，如果未指定任何库，则从所有指定到 LINK 命令的静态库。 若要为多个库指定/WHOLEARCHIVE 选项，可以在链接器命令行中使用多个/WHOLEARCHIVE 开关。 默认情况下，链接器仅在链接的输出中包含对象文件，而这些文件导出可执行文件中的其他对象文件引用的符号。 /WHOLEARCHIVE 选项使链接器将存档在静态库中的所有对象文件视为在链接器命令行上单独指定。

/WHOLEARCHIVE 选项可用于重新导出静态库中的所有符号。 这使你可以确保在从多个静态库中创建组件时，包含所有库代码、资源和元数据。 如果在创建包含要导出的 Windows 运行时组件的静态库时看到警告 LNK4264，请在将库链接到其他组件或应用时使用/WHOLEARCHIVE 选项。

Visual Studio 2015 Update 2 中引入了/WHOLEARCHIVE 选项。

### <a name="to-set-this-linker-option-in-visual-studio"></a>在 Visual Studio 中设置此链接器选项

1. 打开项目“属性页” 对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择 "**配置属性**"、"**链接器**" 下的 "**命令行**" 属性页。

1. 将/WHOLEARCHIVE 选项添加到 "**其他选项**" 文本框中。

## <a name="see-also"></a>另请参阅

[MSVC 链接器参考](linking.md)<br/>
[MSVC 链接器选项](linker-options.md)
