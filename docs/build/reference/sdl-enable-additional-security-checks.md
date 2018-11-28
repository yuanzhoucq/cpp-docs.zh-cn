---
title: /sdl（启用附加安全检查）
ms.date: 11/26/2018
f1_keywords:
- VC.Project.VCCLCompilerTool.SDLCheck
ms.assetid: 3dcf86a0-3169-4240-9f29-e04a9f535826
ms.openlocfilehash: 49ac57f81ef07eb2a9c1e11280e160f0c48fce73
ms.sourcegitcommit: d04dfe95801bafcbd5371e40e626fe5c678343b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/27/2018
ms.locfileid: "52389937"
---
# <a name="sdl-enable-additional-security-checks"></a>/sdl（启用附加安全检查）

添加建议的安全开发生命周期 (SDL) 检查。 这些检查包括额外的被视为错误的安全相关警告以及其他安全代码生成功能。

## <a name="syntax"></a>语法

```
/sdl[-]
```

## <a name="remarks"></a>备注

**/sdl**使提供的基线安全检查的超集[/GS](../../build/reference/gs-buffer-security-check.md)并重写 **/GS-**。 默认情况下 **/sdl**处于关闭状态。 **/sdl-** 禁用额外的安全检查。

## <a name="compile-time-checks"></a>编译时检查

**/sdl**使这些警告视为错误：

|/sdl 启用的警告|等效的命令行开关|描述|
|------------------------------|-------------------------------------|-----------------|
|[C4146](../../error-messages/compiler-warnings/compiler-warning-level-2-c4146.md)|/we4146|将一元减号运算符应用于无符号类型，并生成了无符号的结果。|
|[C4308](../../error-messages/compiler-warnings/compiler-warning-level-2-c4308.md)|/we4308|将负整型常数转换为无符号类型，并生成了可能无意义的结果。|
|[C4532](../../error-messages/compiler-warnings/compiler-warning-level-1-c4532.md)|/we4532|利用`continue`，`break`或`goto`中的关键字`__finally` / `finally`块已在异常终止期间未定义行为。|
|[C4533](../../error-messages/compiler-warnings/compiler-warning-level-1-c4533.md)|/we4533|初始化变量的代码不会执行。|
|[C4700](../../error-messages/compiler-warnings/compiler-warning-level-1-and-level-4-c4700.md)|/we4700|使用未初始化的局部变量。|
|[C4703](../../error-messages/compiler-warnings/compiler-warning-level-4-c4703.md)|/we4703|使用可能未初始化的局部指针变量。|
|[C4789](../../error-messages/compiler-warnings/compiler-warning-level-1-c4789.md)|/we4789|使用特定 C 运行时 (CRT) 函数时缓冲区溢出。|
|[C4995](../../error-messages/compiler-warnings/compiler-warning-level-3-c4995.md)|/we4995|使用函数标记有杂注[弃用](../../preprocessor/deprecated-c-cpp.md)。|
|[C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)|/we4996|使用函数标记为[弃用](../../cpp/deprecated-cpp.md)。|

## <a name="runtime-checks"></a>运行时检查

当 **/sdl**是启用，编译器生成代码，以执行这些检查在运行时：

- 启用严格模式下的 **/GS**运行时缓冲区溢出检测，等效于使用编译`#pragma strict_gs_check(push, on)`。

- 执行有限的指针清理。 在不涉及取消引用的表达式中以及没有用户定义的析构函数的类型中，在调用 `delete` 后，指针引用将设置为无效的地址。 这有助于防止重复使用已过时的指针引用。

- 执行类成员的指针初始化。 初始化类成员的指针类型设置为自动**nullptr**上 （在之前的构造函数运行） 的对象实例化。 这有助于防止使用未初始化构造函数不会显式初始化的指针。 调用编译器生成的成员的指针初始化为：

  - 不使用自定义 （用户定义） 分配对象 `operator new`

  - 作为数组的一部分不分配对象 (例如`new A[x]`)

  - 类是未托管或导入

  - 该类具有用户定义的默认构造函数。

  若要初始化的编译器生成的类初始化函数，成员必须是指针，并不是属性或常量。

## <a name="remarks"></a>备注

有关详细信息，请参阅[警告、 /sdl 和改进未初始化的变量检测](https://cloudblogs.microsoft.com/microsoftsecure/2012/06/06/warnings-sdl-and-improving-uninitialized-variable-detection/)。

#### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 选择**C/c + +** 文件夹。

1. 上**常规**页上，选择从选项**SDL 检查**下拉列表。

## <a name="see-also"></a>请参阅

[编译器选项](../../build/reference/compiler-options.md)<br/>
[设置编译器选项](../../build/reference/setting-compiler-options.md)