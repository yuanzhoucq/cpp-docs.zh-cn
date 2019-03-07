---
title: 了解 Helper 函数
ms.date: 11/04/2016
helpviewer_keywords:
- delayed loading of DLLs, helper function
- __delayLoadHelper2 function
- delayimp.lib
- __delayLoadHelper function
- delayhlp.cpp
- delayimp.h
- helper functions
ms.assetid: 6279c12c-d908-4967-b0b3-cabfc3e91d3d
ms.openlocfilehash: 955ae0ed8feac22da19eb13218e2332849477e29
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57421369"
---
# <a name="understanding-the-helper-function"></a>了解 Helper 函数

链接器支持延迟加载 helper 函数是什么实际上在运行时加载的 DLL。 可以修改要自定义其行为，通过编写自己的函数并将其链接到你的程序而不是使用 Delayimp.lib 中提供的帮助器函数的帮助程序函数。 一个帮助程序函数是所有的延迟加载 Dll。

如果你想要对其进行特定处理基于 DLL 或导入的名称，可以提供自己的 helper 函数版本。

帮助程序函数执行以下操作：

- 检查以查看已加载的库存储句柄

- 调用**LoadLibrary**尝试加载的 dll

- 调用**GetProcAddress**尝试获取过程的地址

- 返回到延迟导入加载转换 （thunk） 来调用当前加载的入口点

以下操作的每轮之后，帮助程序函数可以回调在程序中的通知挂钩：

- 帮助器函数启动时

- 再**LoadLibrary**帮助程序函数中调用

- 再**GetProcAddress**帮助程序函数中调用

- 如果在调用**LoadLibrary**帮助程序函数中失败

- 如果在调用**GetProcAddress**帮助程序函数中失败

- 之后该帮助器函数完成处理

每种挂钩点可以返回一个值，将更改以某种方式除外返回到延迟导入负载转换 （thunk） 的帮助器例程的正常处理。

默认帮助程序代码可以 Delayhlp.cpp 和 Delayimp.h 中找到 （在 vc\include)，并且在 Delayimp.lib 中编译 （以 vc\lib)。 你将需要在编译中包含此库，除非您编写自己的帮助器函数。

以下主题介绍了帮助程序函数：

- [自 Visual C++ 6.0 以来 DLL 延迟加载 Helper 函数所做的更改](../../build/reference/changes-in-the-dll-delayed-loading-helper-function-since-visual-cpp-6-0.md)

- [调用约定、参数和返回类型](../../build/reference/calling-conventions-parameters-and-return-type.md)

- [结构和常量定义](../../build/reference/structure-and-constant-definitions.md)

- [计算所需值](../../build/reference/calculating-necessary-values.md)

- [卸载延迟加载的 DLL](../../build/reference/explicitly-unloading-a-delay-loaded-dll.md)

## <a name="see-also"></a>请参阅

[延迟加载 DLL 的链接器支持](../../build/reference/linker-support-for-delay-loaded-dlls.md)
