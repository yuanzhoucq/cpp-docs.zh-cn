---
title: /CLRIMAGETYPE （指定 CLR 映像的类型） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /CLRIMAGETYPE
- VC.Project.VCLinkerTool.CLRImageType
dev_langs:
- C++
helpviewer_keywords:
- /CLRIMAGETYPE linker option
- -CLRIMAGETYPE linker option
ms.assetid: 04c60ee6-9dd7-4391-bc03-6926ad0fa116
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b5efb2e73e854591be7134753cec21a708fff3e5
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2018
ms.locfileid: "34705005"
---
# <a name="clrimagetype-specify-type-of-clr-image"></a>/CLRIMAGETYPE（指定 CLR 映像的类型）

在链接的图像中设置的 CLR 映像类型。

## <a name="syntax"></a>语法

> **/CLRIMAGETYPE:**{**IJW**|**纯**|**安全**|**SAFE32BITPREFERRED**}

## <a name="remarks"></a>备注

链接器接受本机对象以及 MSIL 对象编译的使用[/clr](../../build/reference/clr-common-language-runtime-compilation.md)。 **/Clr: pure**和 **/clr: safe**编译器选项已弃用 Visual Studio 2015 中，在 Visual Studio 2017 中不受支持。 同一版本中传递混合对象时，结果输出文件的可验证性级别默认等于输入模块的最低可验证性级别。 例如，如果传递本机映像和混合的模式映像 (使用编译的 **/clr**)，结果映像将为混合的模式映像。

你可以使用 **/CLRIMAGETYPE**指定较低级别的可验证性，如果你的需要。

有关如何确定文件的 CLR 映像类型的信息，请参阅 [/CLRHEADER](../../build/reference/clrheader.md)。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 展开“配置属性”节点。

1. 展开**链接器**节点。

1. 选择**高级**属性页。

1. 修改**CLR 映像类型**属性。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

1. 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRImageType%2A>。

## <a name="see-also"></a>请参阅

- [设置链接器选项](../../build/reference/setting-linker-options.md)
- [链接器选项](../../build/reference/linker-options.md)
