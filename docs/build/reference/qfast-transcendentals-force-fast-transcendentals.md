---
title: -Qfast_transcendentals （强制快速先验） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /Qfast_transcendentals
dev_langs:
- C++
helpviewer_keywords:
- /Qfast_transcendentals
- Force Fast Transcendentals
ms.assetid: 4de24bd1-38e6-49d4-9a05-04c9937d24ac
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8edfcdc6881ef3d140a80113047722a62e5bd517
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46420252"
---
# <a name="qfasttranscendentals-force-fast-transcendentals"></a>/Qfast_transcendentals（强制快速先验）

生成先验函数的内联代码。

## <a name="syntax"></a>语法

```
/Qfast_transcendentals
```

## <a name="remarks"></a>备注

此编译器选项强制先验函数转换为内联代码，以提高执行速度。 此选项时不起作用仅搭配 **/fp： 除外**或 **/fp： 精确**。 生成先验函数的内联代码已下的默认行为 **/fp: fast**。

此选项与不兼容 **/fp: strict**。 请参阅[/fp （指定浮点行为）](../../build/reference/fp-specify-floating-point-behavior.md)有关浮点编译器选项的详细信息。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 单击 **“C/C++”** 文件夹。

1. 点击“命令行”  属性页。

1. 在 **“附加选项”** 框中键入编译器选项。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

[/Q 选项（低级别操作）](../../build/reference/q-options-low-level-operations.md)<br/>
[编译器选项](../../build/reference/compiler-options.md)<br/>
[设置编译器选项](../../build/reference/setting-compiler-options.md)