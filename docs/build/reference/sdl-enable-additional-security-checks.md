---
title: /sdl（启用附加安全检查）
ms.date: 11/26/2018
f1_keywords:
- VC.Project.VCCLCompilerTool.SDLCheck
ms.assetid: 3dcf86a0-3169-4240-9f29-e04a9f535826
ms.openlocfilehash: d5a85f9648ebcc4064146f22cf5da020e06b7ba3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218970"
---
# <a name="sdl-enable-additional-security-checks"></a>/sdl（启用附加安全检查）

添加建议的安全开发生命周期 (SDL) 检查。 这些检查包括额外的被视为错误的安全相关警告以及其他安全代码生成功能。

## <a name="syntax"></a>语法

> **`/sdl`**[**`-`**]

## <a name="remarks"></a>备注

**/sdl**启用由提供的基线安全检查的超集 [`/GS`](gs-buffer-security-check.md) ，并替代 **`/GS-`** 。 默认情况下， **`/sdl`** 处于关闭状态。 **`/sdl-`** 禁用其他安全检查。

## <a name="compile-time-checks"></a>编译时检查

**`/sdl`** 启用这些警告作为错误：

|/sdl 启用的警告|等效的命令行开关|描述|
|------------------------------|-------------------------------------|-----------------|
|[C4146](../../error-messages/compiler-warnings/compiler-warning-level-2-c4146.md)|/we4146|将一元减号运算符应用于无符号类型，并生成了无符号的结果。|
|[C4308](../../error-messages/compiler-warnings/compiler-warning-level-2-c4308.md)|/we4308|将负整型常数转换为无符号类型，并生成了可能无意义的结果。|
|[C4532](../../error-messages/compiler-warnings/compiler-warning-level-1-c4532.md)|/we4532|在 `continue` `break` `goto` 块中使用或关键字在 `__finally` / `finally` 异常终止期间具有未定义的行为。|
|[C4533](../../error-messages/compiler-warnings/compiler-warning-level-1-c4533.md)|/we4533|初始化变量的代码不会执行。|
|[C4700](../../error-messages/compiler-warnings/compiler-warning-level-1-and-level-4-c4700.md)|/we4700|使用未初始化的局部变量。|
|[C4703](../../error-messages/compiler-warnings/compiler-warning-level-4-c4703.md)|/we4703|使用可能未初始化的局部指针变量。|
|[C4789](../../error-messages/compiler-warnings/compiler-warning-level-1-c4789.md)|/we4789|使用特定 C 运行时 (CRT) 函数时缓冲区溢出。|
|[C4995](../../error-messages/compiler-warnings/compiler-warning-level-3-c4995.md)|/we4995|使用标记有杂注的函数 [`deprecated`](../../preprocessor/deprecated-c-cpp.md) 。|
|[C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)|/we4996|使用标记为的函数 [`deprecated`](../../cpp/deprecated-cpp.md) 。|

## <a name="runtime-checks"></a>运行时检查

**`/sdl`** 启用后，编译器将生成代码以在运行时执行这些检查：

- 启用 **`/GS`** 运行时缓冲区溢出检测的严格模式，等效于与的编译 `#pragma strict_gs_check(push, on)` 。

- 执行有限的指针清理。 在不涉及取消引用的表达式和没有用户定义的析构函数的类型中，在调用后，指针引用将设置为无效的地址 **`delete`** 。 这有助于防止重复使用已过时的指针引用。

- 执行类成员指针初始化。 自动将指针类型的类成员初始化为 **`nullptr`** 对象实例化（在构造函数运行之前）。 这有助于防止使用未初始化的指针，该构造函数不会显式初始化。 将调用编译器生成的成员指针初始化，条件是：

  - 未使用自定义（用户定义）分配对象`operator new`

  - 不将对象分配为数组的一部分（例如 `new A[x]` ）

  - 不管理或导入类

  - 类具有用户定义的默认构造函数。

  若要由编译器生成的类初始化函数进行初始化，成员必须是指针，而不是属性或常量。

## <a name="remarks"></a>备注

有关详细信息，请参阅[警告、/sdl 和改进未初始化的变量检测](https://cloudblogs.microsoft.com/microsoftsecure/2012/06/06/warnings-sdl-and-improving-uninitialized-variable-detection/)。

#### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择 " **c/c + +** " 文件夹。

1. 在 "**常规**" 页上，从 " **SDL 检查**" 下拉列表中选择选项。

## <a name="see-also"></a>另请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
