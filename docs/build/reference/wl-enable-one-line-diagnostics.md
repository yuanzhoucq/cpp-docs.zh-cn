---
title: /WL（启用单行诊断）
ms.date: 11/04/2016
f1_keywords:
- /wl
helpviewer_keywords:
- -WL compiler option [C++]
- /WL compiler option [C++]
- WL compiler option [C++]
ms.assetid: 332cadb4-8ea6-45fe-b67d-33ddec1f2c2e
ms.openlocfilehash: 2d2f3c1c7bac19fc0e401067f43e78e3770c6304
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50428153"
---
# <a name="wl-enable-one-line-diagnostics"></a>/WL（启用单行诊断）

将附加信息追加到错误或警告消息。

## <a name="syntax"></a>语法

```
/WL
```

## <a name="remarks"></a>备注

错误和警告消息，从 c + + 编译器可以跟默认情况下，新行上显示的其他信息。 从命令行编译时，可以将附加信息行追加到错误或警告消息。 如果捕获到日志文件生成输出，然后处理该日志以查找所有错误和警告，这可能是可取。 分号将从其他行分隔的错误或警告消息。

并非所有错误和警告消息都具有附加行的信息。 下面的代码将生成的错误的附加行的信息;它会让您测试的影响，当您使用 **/WL**。

```
// compiler_option_WL.cpp
// compile with: /WL
#include <queue>
int main() {
   std::queue<int> q;
   q.fromthecontinuum();   // C2039
}
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 单击 **“C/C++”** 文件夹。

1. 点击“命令行”  属性页。

1. 在 **“附加选项”** 框中键入编译器选项。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

[编译器选项](../../build/reference/compiler-options.md)<br/>
[设置编译器选项](../../build/reference/setting-compiler-options.md)