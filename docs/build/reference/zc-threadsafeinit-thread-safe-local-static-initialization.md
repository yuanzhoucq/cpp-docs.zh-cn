---
title: '/Zc: threadsafeinit （线程安全的本地静态初始化）'
ms.date: 03/14/2018
f1_keywords:
- threadSafeInit
- /Zc:threadSafeInit
helpviewer_keywords:
- -Zc compiler options (C++)
- threadSafeInit
- Thread-safe Local Static Initialization
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: a0fc4b34-2cf0-45a7-a642-b8afc4ca19f2
ms.openlocfilehash: a0a5edda3d0d178a03fa98cf689b257cd5ab3f53
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50605824"
---
# <a name="zcthreadsafeinit-thread-safe-local-static-initialization"></a>/Zc: threadsafeinit （线程安全的本地静态初始化）

**/Zc: threadsafeinit**编译器选项告知编译器来初始化静态本地 （函数范围） 变量中以线程安全的方式，不必进行手动同步。 只有初始化是线程安全的。 使用和修改静态本地变量由多个线程必须仍是手动同步。 从 Visual Studio 2015 开始，提供此选项。 默认情况下，Visual Studio 启用此选项。

## <a name="syntax"></a>语法

> **/Zc:threadSafeInit**[**-**]

## <a name="remarks"></a>备注

中的 C + + 11 标准，块范围变量具有静态或线程存储持续时间必须是零初始化之前发生的任何其他初始化。 初始化发生时控件第一次传递的变量声明。 如果在初始化期间引发异常，该变量被视为未初始化的并且初始化是重试的下一步的时间控制将传递通过声明。 如果控件输入与初始化、 初始化完成时的并发执行块同时声明。 如果控件重新初始化过程中输入声明以递归方式，该行为不确定。 默认情况下，启动 Visual Studio 2015 中的 Visual Studio 实施此标准行为。 此行为可通过设置显式指定 **/zc: threadsafeinit**编译器选项。

**/Zc: threadsafeinit**编译器选项是在默认情况下。 [触发-](permissive-standards-conformance.md)选项不会影响 **/zc: threadsafeinit**。

静态本地变量的线程安全初始化依赖于实现通用 C 运行时库 (UCRT) 中的代码。 若要避免依赖于 UCRT，或保留版本的 Visual Studio 2015 之前的 Visual Studio 的非线程安全初始化行为，请使用 **/zc: threadsafeinit-** 选项。 如果您知道该线程安全性不需要，使用此选项以生成针对的静态局部声明略小、 更快地进行编码。

线程安全静态局部变量内部使用线程本地存储 (TLS) 来提供有效的执行，在已经初始化静态。 此功能的实现依赖于在 Windows Vista 和更高版本操作系统的 Windows 操作系统支持函数。 Windows XP、 Windows Server 2003 和较早的操作系统不具有这种支持，因此它们不会收到效率优势。 这些操作系统还具有可以加载的 TLS 部分数较低的限制。 超出了 TLS 部分限制可能会导致崩溃。 如果这是在代码中，特别是在必须在较早的操作系统运行的代码问题，使用 **/zc: threadsafeinit-** 禁用线程安全初始化代码。

有关 Visual C++ 中一致性问题的详细信息，请参阅 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 从**配置**下拉列表菜单中，选择**所有配置**。

1. 选择**配置属性** > **C/c + +** > **命令行**属性页。

1. 修改**其他选项**属性以包含 **/zc: threadsafeinit**或 **/zc: threadsafeinit-** ，然后选择**确定**。

## <a name="see-also"></a>请参阅

[编译器选项](../../build/reference/compiler-options.md)<br/>
[设置编译器选项](../../build/reference/setting-compiler-options.md)<br/>
[/Zc（一致性）](../../build/reference/zc-conformance.md)<br/>
