---
title: 加载被延迟加载的 DLL 的所有导入
ms.date: 11/04/2016
helpviewer_keywords:
- __HrLoadAllImportsForDll linker option
ms.assetid: 975fcd97-1a56-4a16-9698-e1a249d2d592
ms.openlocfilehash: e855b648dc7a9ee0670c3704a11aa1897a238403
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57811909"
---
# <a name="loading-all-imports-for-a-delay-loaded-dll"></a>加载被延迟加载的 DLL 的所有导入

**__HrLoadAllImportsForDll**函数，delayhlp.cpp 中定义，则告知链接器从指定的 DLL 加载所有导入[/delayload](delayload-delay-load-import.md)链接器选项。

加载所有导入，可将放在代码中的一个位置中的错误处理，而不必使用异常处理的导入的实际调用附近。 它还避免了你的应用程序失败的部分通过一个由于无法加载导入的帮助器代码的过程的情况。

调用 **__HrLoadAllImportsForDll**不会更改行为的挂钩和错误处理; 请参阅[错误处理和通知](error-handling-and-notification.md)有关详细信息。

DLL 名称传递给 **__HrLoadAllImportsForDll**与存储在 DLL 本身的名称进行比较并区分大小写。

下面的示例演示如何调用 **__HrLoadAllImportsForDll**:

```
if (FAILED(__HrLoadAllImportsForDll("delay1.dll"))) {
   printf ( "failed on snap load, exiting\n" );
   exit(2);
}
```

## <a name="see-also"></a>请参阅

[延迟加载 DLL 的链接器支持](linker-support-for-delay-loaded-dlls.md)
