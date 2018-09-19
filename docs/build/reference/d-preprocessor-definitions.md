---
title: -D （预处理器定义） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCNMakeTool.PreprocessorDefinitions
- VC.Project.VCCLCompilerTool.PreprocessorDefinitions
- /d
dev_langs:
- C++
helpviewer_keywords:
- preprocessor definition symbols
- constants, defining
- macros, compiling
- /D compiler option [C++]
- -D compiler option [C++]
- D compiler option [C++]
ms.assetid: b53fdda7-8da1-474f-8811-ba7cdcc66dba
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3dc4da4235b57e9abd8e5f32b8f3e696bd1ce2de
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46397177"
---
# <a name="d-preprocessor-definitions"></a>/D（预处理器定义）

定义源文件的预处理符号。

## <a name="syntax"></a>语法

```
/Dname[= | # [{string | number}] ]
```

## <a name="remarks"></a>备注

可以将此符号与 `#if` 或 `#ifdef` 一起使用，以便有条件地编译源代码。 在代码中重新定义或通过 `#undef` 指令在代码中取消定义符号前，符号定义保持有效。

**/D**具有相同的效果`#define`指令的源代码文件，不同之处在于开头 **/D**命令行上去除引号和`#define`保留它们。

默认情况下，与符号关联的值为 1。 例如， **/D** `name`等效于 **/D**`name`**= 1**。 在本文中，定义的末尾的示例**测试**显示的是用于打印`1`。

使用编译 **/D** `name` **=** 导致符号没有关联的值。 尽管该符号仍可用于有条件地编译代码，但它不会计算出任何结果。 在示例中，如果通过使用编译 **/DTEST =**，出现错误。 此行为类似于带或不带值使用 `#define`。

此命令在 TEST.c 中定义符号 DEBUG：

**CL /DDEBUG 测试。C**

此命令移除 TEST.c 中关键字 `__far` 的所有匹配项：

**CL /D__far = TEST。C**

**CL**环境变量不能设置为包含等号的字符串。 若要使用 **/D**连同**CL**环境变量，则必须指定数字符号而不是等号：

```
SET CL=/DTEST#0
```

在命令提示符处定义预处理符号时，应同时考虑编译器分析规则和 shell 分析规则。 例如，若要在程序中定义百分号预处理符号 (%)，请在命令提示符处指定两个百分号字符 (%%)：如果只指定一个，则会发出分析错误。

```
CL /DTEST=%% TEST.C
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 在左窗格中，选择**配置属性**， **C/c + +**，**预处理器**。

1. 在右窗格中，在右侧列中的**预处理器定义**属性中，打开下拉列表菜单，然后选择**编辑**。

1. 在中**预处理器定义**对话框中，添加 （每行一个）、 修改或删除一个或多个定义。 选择**确定**以保存所做的更改。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PreprocessorDefinitions%2A>。

## <a name="example"></a>示例

```
// cpp_D_compiler_option.cpp
// compile with: /DTEST
#include <stdio.h>

int main( )
{
    #ifdef TEST
        printf_s("TEST defined %d\n", TEST);
    #else
        printf_s("TEST not defined\n");
    #endif
}
```

```Output
TEST defined 1
```

## <a name="see-also"></a>请参阅

[编译器选项](../../build/reference/compiler-options.md)<br/>
[设置编译器选项](../../build/reference/setting-compiler-options.md)<br/>
[/U、/u（未定义符号）](../../build/reference/u-u-undefine-symbols.md)<br/>
[#undef 指令 (C/C++)](../../preprocessor/hash-undef-directive-c-cpp.md)<br/>
[#define 指令 (C/C++)](../../preprocessor/hash-define-directive-c-cpp.md)