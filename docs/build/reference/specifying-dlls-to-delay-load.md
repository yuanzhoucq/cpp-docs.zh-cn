---
title: 指定要延迟加载的 DLL
ms.date: 11/04/2016
helpviewer_keywords:
- DELAYLOAD linker option
- delayed loading of DLLs
- delayed loading of DLLs, specifying
- /DELAYLOAD linker option
ms.assetid: 94cbecfe-7a42-40d1-a618-9f2786bac0d8
ms.openlocfilehash: 2b6737abd76c03186881e83bbd2bf286be6ffe2f
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57813222"
---
# <a name="specifying-dlls-to-delay-load"></a>指定要延迟加载的 DLL

您可以指定哪个 Dll 延迟加载，出现[/delayload](delayload-delay-load-import.md):`dllname`链接器选项。 如果您不打算使用您自己的一个帮助程序函数版本，您还必须链接您的程序与 delayimp.lib （对于桌面应用程序） 或 dloadhelper.lib （针对应用商店应用）。

以下是延迟加载 DLL 的一个简单示例：

```
// cl t.cpp user32.lib delayimp.lib  /link /DELAYLOAD:user32.dll
#include <windows.h>
// uncomment these lines to remove .libs from command line
// #pragma comment(lib, "delayimp")
// #pragma comment(lib, "user32")

int main() {
   // user32.dll will load at this point
   MessageBox(NULL, "Hello", "Hello", MB_OK);
}
```

生成项目的调试版本。 使用调试器单步调试该代码，你会注意到只有在你调用到`MessageBox`时才加载该 user32.dll。

## <a name="see-also"></a>请参阅

[延迟加载 DLL 的链接器支持](linker-support-for-delay-loaded-dlls.md)
