---
title: /sourceDependencies （报表源级别的依赖项）
description: Microsoft c + + 中的/sourceDependencies 编译器选项的参考指南。
ms.date: 07/29/2020
f1_keywords:
- /sourceDependencies
helpviewer_keywords:
- /sourceDependencies compiler option
- /sourceDependencies
ms.openlocfilehash: 3198353ea7569c426a556522d6b931fe23c7f12c
ms.sourcegitcommit: f2a135d69a2a8ef1777da60c53d58fe06980c997
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/03/2020
ms.locfileid: "87520701"
---
# <a name="sourcedependencies-report-source-level-dependencies"></a>`/sourceDependencies`（报表源级别依赖项）

指示编译器生成一个 JSON 文件，该文件详细说明在编译期间使用的源级依赖项。

JSON 文件包含源依赖项的列表，其中包括：
- 标头文件（可传递和直接包含的标头）。
- 使用的 PCH （如果 **`/Yu`** 指定了）。
- 导入的模块和导入的标头单元（可传递和直接导入的模块/标题单元）。

## <a name="syntax"></a>语法

> **`/sourceDependencies`***filename*\
> **`/sourceDependencies`***目录*

## <a name="arguments"></a>参数

*名字*\
编译器会将源依赖项输出写入指定的文件名，其中可能包括相对或绝对路径。

*文件夹*\
如果参数是一个目录，则编译器将在指定的目录中生成源依赖项文件。 输出文件的名称基于输入文件的全名，附加了 *`.json`* 扩展名。 例如，如果为编译器提供的文件是，则 *`main.cpp`* 生成的输出文件名为 *`main.cpp.json`* 。

## <a name="remarks"></a>备注

**`/sourceDependencies`** 编译器选项在 Visual Studio 2019 版本16.7 中开始提供。 默认情况下不启用它。

指定 **`/MP`** 编译器选项时，我们建议你使用 **`/sourceDependencies`** with directory 参数。 如果提供单个 filename 参数，则两个编译器实例可能尝试同时打开输出文件并导致错误。 有关的详细信息 **`/MP`** ，请参阅[ `/MP` （包含多个进程）](mp-build-with-multiple-processes.md)。

发生非致命编译器错误时，依赖关系信息仍会写入到输出文件中。

所有文件路径在输出中都显示为绝对路径。

### <a name="examples"></a>示例

给定下面的示例代码：

```cpp
// main.cpp
#include "header.h"
import m;
import "other.h";

int main() { }
```

你可以将 **`/sourceDependencies`** 与其他编译器选项一起使用：

> `cl ... /sourceDependencies output.json ... main.cpp`

其中 `...` 表示其他编译器选项。 此命令行生成一个 JSON 文件 *`output.json`* ，其中包含类似于以下内容的内容：

```JSON
{
    "Version": "1.0",
    "Data": {
        "Source": "C:\\...\\main.cpp",
        "PCH": "C:\\...\\pch.pch",
        "Includes": [
            "C:\\...\\header.h"
        ],
        "Modules": [
            "C:\\...\\m.ifc",
            "C:\\...\\other.h.ifc"
        ]
    }
}
```

我们已使用 `...` 为报告的路径缩写; 报表中包含绝对路径。 报告的路径取决于编译器查找依赖项的位置。 如果结果不是预期的，则可能需要检查项目的 "包含路径" 设置。

### <a name="to-set-the-sourcedependencies-compiler-option-in-visual-studio"></a>在 Visual Studio 中设置/sourceDependencies 编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择 "**配置属性**" "  >  **c/c + +**  >  **命令行**" 属性页。

1. 在 "**附加选项**" 框中，添加， *`/sourceDependencies: <filename>`* 然后选择**Apply** **"确定" 或 "应用"** 保存更改。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 此选项不具有编程等效项。

## <a name="see-also"></a>请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)<br/>
