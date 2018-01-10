---
title: "/Zc:threadSafeInit （线程安全本地静态初始化） |Microsoft 文档"
ms.custom: 
ms.date: 12/13/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- threadSafeInit
- /Zc:threadSafeInit
dev_langs: C++
helpviewer_keywords:
- -Zc compiler options (C++)
- threadSafeInit
- Thread-safe Local Static Initialization
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: a0fc4b34-2cf0-45a7-a642-b8afc4ca19f2
caps.latest.revision: "1"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a03f3ea67c9ecabd6fa68d653a3e1812fb0266cc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="zcthreadsafeinit-thread-safe-local-static-initialization"></a>/Zc:threadSafeInit （线程安全本地静态初始化）  
`/Zc:threadSafeInit`编译器选项告知编译器以线程安全的方式，无需手动同步初始化静态本地 （函数范围） 变量。 只有初始化是线程安全的。 使用和修改多个线程的静态本地变量仍必须手动同步。 此选项是在 Visual Studio 2015 中开始提供。 默认情况下，Visual Studio 启用此选项。  
  
## <a name="syntax"></a>语法  
  
`/Zc:threadSafeInit`[`-`]  
  
## <a name="remarks"></a>备注  
  
C + + 11 标准中，块范围变量与静态或线程存储持续时间必须将初始化为零的任何其他初始化发生之前。 控制第一次传递的变量声明时进行初始化。 如果在初始化期间引发异常，变量被视为未初始化，并且初始化是重新尝试下一步的时间控制权将传递通过声明。 如果控制进入与初始化，并发执行块时初始化完成后同时声明。 如果控件重新声明以递归方式进入在初始化期间，该行为不确定。 默认情况下，Visual Studio 启动 Visual Studio 2015 中实现此标准行为。 此行为可以通过设置显式指定`/Zc:threadSafeInit`编译器选项。  
  
线程安全的静态局部变量的初始化依赖于通用 C 运行时库 (UCRT) 实现的代码。 若要避免产生 UCRT，依赖关系或保留版本的 Visual Studio 2015 之前的 Visual Studio 的非线程安全初始化行为，请使用`/Zc:threadSafeInit-`选项。 如果你知道该线程安全性不需要，使用此选项以生成略小、 更快的代码周围的静态局部声明。  
  
线程安全的静态局部变量内部使用线程本地存储 (TLS) 已初始化静态时提供有效的执行。 此功能的实现依赖于在 Windows Vista 和更高版本操作系统的 Windows 操作系统支持函数。 Windows XP、 Windows Server 2003、 和较早的操作系统不具有此支持，因此它们不会获得与效率优势。 这些操作系统的系统还具有可以加载的 TLS 节的数目较低的限制。 超出了 TLS 部分限制可能会导致崩溃。 如果这是一个问题在代码中，特别是在必须在较早的操作系统运行的代码使用`/Zc:threadSafeInit-`禁用线程安全的初始化代码。  
  
有关 Visual C++ 中一致性问题的详细信息，请参阅 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)。
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。
2.  从**配置**下拉列表菜单中，选择**所有配置**。
3.  选择**配置属性**， **C/c + +**，**命令行**属性页。
4.  修改**其他选项**属性以包含`/Zc:threadSafeInit`或`/Zc:threadSafeInit-`，然后选择**确定**。

## <a name="see-also"></a>请参阅  
[编译器选项](../../build/reference/compiler-options.md)  
[设置编译器选项](../../build/reference/setting-compiler-options.md)  
[/Zc （一致性）](../../build/reference/zc-conformance.md)  
