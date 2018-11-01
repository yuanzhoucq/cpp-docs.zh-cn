---
title: 指定要延迟加载的 DLL
ms.date: 11/04/2016
helpviewer_keywords:
- DELAYLOAD linker option
- delayed loading of DLLs
- delayed loading of DLLs, specifying
- /DELAYLOAD linker option
ms.assetid: 94cbecfe-7a42-40d1-a618-9f2786bac0d8
ms.openlocfilehash: 986dab0621127c90097808025825930bf9974a7a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50549859"
---
# <a name="specifying-dlls-to-delay-load"></a>指定要延迟加载的 DLL

您可以指定哪个 Dll 延迟加载，出现[/delayload](../../build/reference/delayload-delay-load-import.md):`dllname`链接器选项。 如果您不打算使用您自己的一个帮助程序函数版本，您还必须链接您的程序与 delayimp.lib （对于桌面应用程序） 或 dloadhelper.lib （针对应用商店应用）。

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

[延迟加载 DLL 的链接器支持](../../build/reference/linker-support-for-delay-loaded-dlls.md)