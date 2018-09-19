---
title: 加载延迟加载的 DLL 的所有导入 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- __HrLoadAllImportsForDll linker option
ms.assetid: 975fcd97-1a56-4a16-9698-e1a249d2d592
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 29ef1c576af7930e157dafd0f57bf0b8dff49fa6
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45715573"
---
# <a name="loading-all-imports-for-a-delay-loaded-dll"></a>加载被延迟加载的 DLL 的所有导入

**__HrLoadAllImportsForDll**函数，delayhlp.cpp 中定义，则告知链接器从指定的 DLL 加载所有导入[/delayload](../../build/reference/delayload-delay-load-import.md)链接器选项。

加载所有导入，可将放在代码中的一个位置中的错误处理，而不必使用异常处理的导入的实际调用附近。 它还避免了你的应用程序失败的部分通过一个由于无法加载导入的帮助器代码的过程的情况。

调用 **__HrLoadAllImportsForDll**不会更改行为的挂钩和错误处理; 请参阅[错误处理和通知](../../build/reference/error-handling-and-notification.md)有关详细信息。

DLL 名称传递给 **__HrLoadAllImportsForDll**与存储在 DLL 本身的名称进行比较并区分大小写。

下面的示例演示如何调用 **__HrLoadAllImportsForDll**:

```
if (FAILED(__HrLoadAllImportsForDll("delay1.dll"))) {
   printf ( "failed on snap load, exiting\n" );
   exit(2);
}
```

## <a name="see-also"></a>请参阅

[延迟加载 DLL 的链接器支持](../../build/reference/linker-support-for-delay-loaded-dlls.md)