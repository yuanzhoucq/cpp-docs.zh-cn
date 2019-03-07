---
title: 开发您自己的 Helper 函数
ms.date: 11/04/2016
helpviewer_keywords:
- helper functions
ms.assetid: a845429d-68b1-4e14-aa88-f3f5343bd490
ms.openlocfilehash: 2601aff6b53e9ad3a970dbe1be008efdd7008ef8
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57424426"
---
# <a name="developing-your-own-helper-function"></a>开发您自己的 Helper 函数

您可能想要提供自己的例程，以执行特定进程上的 DLL 或导入的名称基于版本。 执行此操作的两种方法： 编写自己的可能根据所提供的代码，或只挂接所提供的版本使用上文详述的通知挂钩。

## <a name="code-your-own"></a>代码自己

这是相当简单，因为您实际上可以用提供的代码原则是新建一个。 当然，它必须遵循的调用约定，如果它返回到链接器生成 thunk，它必须返回正确的函数指针。 一次在代码中，可以执行几乎任何您想以满足在调用或获取的调用。

## <a name="use-the-start-processing-notification-hook"></a>使用启动处理通知挂钩

它可能是最简单的方法只需提供指向接收通知 dliStartProcessing 上的默认帮助器相同的值的用户提供通知挂钩函数的新指针。 此时，挂钩函数实质上是可以成为新的帮助器函数，因为默认帮助程序成功返回时将绕过默认帮助程序中的所有其他处理。

## <a name="see-also"></a>请参阅

[延迟加载 DLL 的链接器支持](../../build/reference/linker-support-for-delay-loaded-dlls.md)
