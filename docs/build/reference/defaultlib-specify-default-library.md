---
title: /DEFAULTLIB （指定默认库） |Microsoft 文档
ms.custom: ''
ms.date: 05/29/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.DefaultLibraries
- /defaultlib
dev_langs:
- C++
helpviewer_keywords:
- -DEFAULTLIB linker option
- DEFAULTLIB linker option
- /DEFAULTLIB linker option
- libraries, adding to list of
ms.assetid: 6af7ff49-c170-4a13-97e2-2b9ae2de20c9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9afcaa0e229ec34ba91b4d60a7a4fa9acec2d7e3
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/01/2018
ms.locfileid: "34569776"
---
# <a name="defaultlib-specify-default-library"></a>/DEFAULTLIB（指定默认库）

指定要搜索以解析外部引用默认库。

## <a name="syntax"></a>语法

> **/DEFAULTLIB**:_库_

### <a name="arguments"></a>自变量

|参数|描述|
|-|-|
*库*|在解析外部引用时搜索的库的名称。

## <a name="remarks"></a>备注

**/DEFAULTLIB**选项添加一个*库*到的链接将在解析引用时搜索的库的列表。 使用指定的库 **/DEFAULTLIB**搜索后显式指定命令行上和之前在.obj 文件中命名的默认库的库。

当使用不带参数， [/NODEFAULTLIB （忽略所有默认库）](../../build/reference/nodefaultlib-ignore-libraries.md)选项将重写所有 **/DEFAULTLIB**:*库*选项。 **/NODEFAULTLIB**:*库*选项替代 **/DEFAULTLIB**:*库*时相同*库*中同时指定名称。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 选择**配置属性** > **链接器** > **命令行**属性页。

1. 在**其他选项**，输入 **/DEFAULTLIB**:*库*搜索每个库的选项。 选择**确定**以保存所做的更改。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

- [设置链接器选项](../../build/reference/setting-linker-options.md)
- [链接器选项](../../build/reference/linker-options.md)
