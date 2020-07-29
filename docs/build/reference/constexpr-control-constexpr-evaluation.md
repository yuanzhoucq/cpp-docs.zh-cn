---
title: /constexpr（控制 constexpr 计算）
ms.date: 08/15/2017
f1_keywords:
- /constexpr
- -constexpr
helpviewer_keywords:
- /constexpr control constexpr evaluation [C++]
- -constexpr control constexpr evaluation [C++]
- constexpr control constexpr evaluation [C++]
ms.assetid: 76d56784-f5ad-401d-841d-09d1059e8b8c
ms.openlocfilehash: 7b3ae1cd732fe1ec234e2734ea4c6fa86db9d5af
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223858"
---
# <a name="constexpr-control-constexpr-evaluation"></a>/constexpr（控制 constexpr 计算）

使用 **/constexpr**编译器选项可以 **`constexpr`** 在编译时控制计算参数。

## <a name="syntax"></a>语法

> **/constexpr：深度**<em>N</em>\
> **/constexpr： backtrace**<em>N</em>\
> **/constexpr：步骤**<em>N</em>

## <a name="arguments"></a>参数

**深度**<em>N</em>将递归函数调用的深度限制 **`constexpr`** 为*N*级。 默认值为 512。

**backtrace**<em>n</em>在诊断中显示最多*n* **`constexpr`** 个评估。 默认值为 10。

**步骤**<em>n</em> **`constexpr`** 在*N*个步骤后终止计算。 默认值为100000。

## <a name="remarks"></a>备注

**/Constexpr**编译器选项控制表达式的编译时计算 **`constexpr`** 。 评估步骤、递归级别和 backtrace 深度是控制的，以防止编译器花费太多时间来 **`constexpr`** 计算。 有关 language 元素的详细信息 **`constexpr`** ，请参阅[Constexpr （c + +）](../../cpp/constexpr-cpp.md)。

从 Visual Studio 2015 开始，可以使用 **/constexpr**选项。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的 "**属性页**" 对话框。

2. 在 "**配置属性**" 下，展开 " **c/c + +** " 文件夹，然后选择 "**命令行**" 属性页。

3. 在 "**附加选项**" 框中输入任何 **/constexpr**编译器选项。 选择 **"确定" 或 "** **应用**" 保存更改。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
