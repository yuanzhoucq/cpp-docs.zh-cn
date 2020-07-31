---
title: /Zc:throwingNew（假定运算符执行新的引发操作）
ms.date: 03/01/2018
f1_keywords:
- throwingNew
- /Zc:throwingNew
helpviewer_keywords:
- -Zc compiler options (C++)
- throwingNew
- Assume operator new Throws
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 20ff0101-9677-4d83-8c7b-8ec9ca49f04f
ms.openlocfilehash: 7593107a280995145d252efa76e0a88bddbd2275
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211861"
---
# <a name="zcthrowingnew-assume-operator-new-throws"></a>/Zc:throwingNew（假定运算符执行新的引发操作）

指定 **/zc： throwingNew**选项时，编译器会优化对的调用， `operator new` 以便跳过对空指针返回的检查。 此选项告知编译器假定和自定义分配器的所有链接实现都 `operator new` 符合 c + + 标准并引发分配失败。 默认情况下，在 Visual Studio 中，编译器 pessimistically 为这些调用生成 null 检查（**/zc： throwingNew**），因为用户可以与的非引发实现进行链接 `operator new` 或编写返回 null 指针的自定义分配器例程。

## <a name="syntax"></a>语法

> **/Zc： throwingNew**[ **-** ]

## <a name="remarks"></a>备注

自 ISO c + + 98 起，标准已指定默认[运算符](../../standard-library/new-operators.md#op_new)在 `std::bad_alloc` 内存分配失败时引发。 Visual C++ 多个版本的 Visual Studio 6.0 在分配失败时返回了 null 指针。 从 Visual Studio 2002 开始， `operator new` 符合标准并在失败时引发。 为了支持使用较旧分配样式的代码，Visual Studio 在 nothrownew.obj 中提供了可链接实现 `operator new` ，该实现在失败时返回 null 指针。 默认情况下，编译器还会生成防御性 null 检查，以防止这些旧样式的分配器导致失败时立即崩溃。 **/Zc： throwingNew**选项告知编译器省略这些 null 检查，假设所有链接内存分配器都符合标准。 这不适用于显式非引发 `operator new` 重载，这些重载通过使用类型的附加参数进行声明， `std::nothrow_t` 并具有显式 **`noexcept`** 规范。

从概念上讲，若要在免费存储中创建对象，编译器将生成代码以分配其内存，然后调用其构造函数来初始化内存。 由于 MSVC 编译器通常无法判断此代码是否将链接到不一致的非引发分配器，因此默认情况下，它还会在调用构造函数之前生成 null 检查。 如果非引发分配失败，此操作可防止在构造函数调用中出现空指针取消引用。 在大多数情况下，不需要进行这些检查，因为默认 `operator new` 分配器会引发，而不是返回 null 指针。 检查也具有不幸的副作用。 它们会使代码大小膨胀，它们会使分支预测器扩散，并阻止其他有用的编译器优化，如 devirtualization 或从已初始化对象中进行的 const 传播。 这些检查只是为了支持链接到*nothrownew.obj*的代码或具有自定义的非一致性实现的代码 `operator new` 。 如果不使用不一致 `operator new` ，建议使用 **/Zc： throwingNew**优化代码。

默认情况下， **/zc： throwingNew**选项处于关闭状态，并且不受[/permissive-](permissive-standards-conformance.md)选项的影响。

如果使用链接时间代码生成（LTCG）进行编译，则无需指定 **/zc： throwingNew**。 使用 LTCG 编译代码时，编译器可以检测是否使用默认的一致 `operator new` 实现。 如果是这样，编译器将自动省略 null 检查。 链接器将查找 **/ThrowingNew**标志，以判断的实现 `operator new` 是否一致。 可以通过在自定义运算符新实现的源中包含此指令，为链接器指定此标志：

```cpp
#pragma comment(linker, "/ThrowingNew")
```

有关 Visual C++ 中一致性问题的详细信息，请参阅 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)。

## <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 从 "**配置**" 下拉菜单中，选择 "**所有配置**"。

1. 选择 "**配置属性**" "  >  **c/c + +**  >  **命令行**" 属性页。

1. 修改 "**附加选项**" 属性以包括 **/zc： throwingNew**或 **/zc： ThrowingNew** ，然后选择 **"确定"**。

## <a name="see-also"></a>另请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)<br/>
[/Zc（一致性）](zc-conformance.md)<br/>
[noexcept (C++)](../../cpp/noexcept-cpp.md)<br/>
[异常规范 (throw) (C++)](../../cpp/exception-specifications-throw-cpp.md)<br/>
[终止（例外）](../../standard-library/exception-functions.md#terminate)<br/>
