---
title: /c（在不链接的情况下进行编译）
ms.date: 11/04/2016
f1_keywords:
- /c
helpviewer_keywords:
- suppress link
- cl.exe compiler, compiling without linking
- -c compiler option [C++]
- c compiler option [C++]
- /c compiler option [C++]
ms.assetid: 8017fc3d-e5dd-4668-a1f7-3120daa95d20
ms.openlocfilehash: 6be3b15efb56e97d658edb5890c3bdce4f64fbd8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50625129"
---
# <a name="c-compile-without-linking"></a>/c（在不链接的情况下进行编译）

可防止对链接的自动调用。

## <a name="syntax"></a>语法

```
/c
```

## <a name="remarks"></a>备注

使用编译 **/c**创建仅限用于.obj 文件。 使用正确的文件和选项来执行生成的链接阶段，必须显式调用链接。

在开发环境中创建任何内部项目都使用 **/c**默认情况下的选项。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

- 此选项不是仅在开发环境中可用。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 若要以编程方式设置此编译器选项，请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CompileOnly%2A>。

## <a name="example"></a>示例

下面的命令行创建对象文件 FIRST.obj 和 SECOND.obj。THIRD.obj 将被忽略。

```
CL /c FIRST.C SECOND.C THIRD.OBJ
```

若要创建的可执行文件，必须调用链接：

```
LINK firsti.obj second.obj third.obj /OUT:filename.exe
```

## <a name="see-also"></a>请参阅

[编译器选项](../../build/reference/compiler-options.md)<br/>
[设置编译器选项](../../build/reference/setting-compiler-options.md)