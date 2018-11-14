---
title: /DEFAULTLIB（指定默认库）
ms.date: 05/29/2018
f1_keywords:
- VC.Project.VCLinkerTool.DefaultLibraries
- /defaultlib
helpviewer_keywords:
- -DEFAULTLIB linker option
- DEFAULTLIB linker option
- /DEFAULTLIB linker option
- libraries, adding to list of
ms.assetid: 6af7ff49-c170-4a13-97e2-2b9ae2de20c9
ms.openlocfilehash: 59a4b48e412cee6b2a90608747aa6fb3e1b79ca7
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2018
ms.locfileid: "51326381"
---
# <a name="defaultlib-specify-default-library"></a>/DEFAULTLIB（指定默认库）

指定要搜索以解析外部引用的默认库。

## <a name="syntax"></a>语法

> **/DEFAULTLIB**:_库_

### <a name="arguments"></a>自变量

*库*<br/>
一个库来解析外部引用时搜索的名称。

## <a name="remarks"></a>备注

**/DEFAULTLIB**选项将添加一个*库*到解析引用时搜索链接的库的列表。 使用指定的库 **/DEFAULTLIB**搜索后在命令行上和在.obj 文件中命名的默认库之前显式指定的库。

当使用不带参数， [/NODEFAULTLIB （忽略所有默认库）](../../build/reference/nodefaultlib-ignore-libraries.md)选项可重写所有 **/DEFAULTLIB**:*库*选项。 **/NODEFAULTLIB**:*库*选项重写 **/DEFAULTLIB**:*库*时相同*库*中同时指定名称。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 选择**配置属性** > **链接器** > **命令行**属性页。

1. 在中**其他选项**，输入 **/DEFAULTLIB**:*库*搜索每个库的选项。 选择**确定**以保存所做的更改。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

- [设置链接器选项](../../build/reference/setting-linker-options.md)
- [链接器选项](../../build/reference/linker-options.md)
