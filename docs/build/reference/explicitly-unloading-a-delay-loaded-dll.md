---
title: 显式卸载延迟加载的 DLL
ms.date: 11/04/2016
helpviewer_keywords:
- /DELAY:UNLOAD linker option
- DELAY:UNLOAD linker option
- __FUnloadDelayLoadedDLL2
- delayed loading of DLLs, unloading
ms.assetid: 1c4c5172-fd06-45d3-9e4f-f12343176b3c
ms.openlocfilehash: f661694dd791ed8db3cd9f5b72a021c7470d17f3
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57420448"
---
# <a name="explicitly-unloading-a-delay-loaded-dll"></a>显式卸载延迟加载的 DLL

[/延迟](../../build/reference/delay-delay-load-import-settings.md): unload 链接器选项可以卸载已被延迟加载的 DLL。 默认情况下，当你的代码卸载该 DLL (使用 /delay: unload 并 **__FUnloadDelayLoadedDLL2**)，延迟加载导入内容保留在导入地址表 (IAT)。 但是，如果您使用 /delay: unload 链接器命令行上，该帮助器函数将支持显式卸载 DLL，正在 IAT 重置为其原始形式;现在无效指针将被覆盖。 IAT 是中的字段[ImgDelayDescr](../../build/reference/calling-conventions-parameters-and-return-type.md) （如果存在） 包含一份原始 IAT 的地址。

## <a name="example"></a>示例

### <a name="code"></a>代码

```
// link with /link /DELAYLOAD:MyDLL.dll /DELAY:UNLOAD
#include <windows.h>
#include <delayimp.h>
#include "MyDll.h"
#include <stdio.h>

#pragma comment(lib, "delayimp")
#pragma comment(lib, "MyDll")
int main()
{
    BOOL TestReturn;
    // MyDLL.DLL will load at this point
    fnMyDll();

    //MyDLL.dll will unload at this point
    TestReturn = __FUnloadDelayLoadedDLL2("MyDll.dll");

    if (TestReturn)
        printf_s("\nDLL was unloaded");
    else
        printf_s("\nDLL was not unloaded");
}
```

### <a name="comments"></a>注释

卸载延迟加载的 DLL 的重要说明：

- 您可以找到的实现 **__FUnloadDelayLoadedDLL2**文件中的函数 \VC7\INCLUDE\DELAYHLP。CPP。

- Name 参数 **__FUnloadDelayLoadedDLL2**函数必须完全匹配 （包括示例） 导入库包含的内容 （即字符串也是在图像中导入表中）。 可以查看的内容使用的导入库[DUMPBIN /DEPENDENTS](../../build/reference/dependents.md)。 如果需要，不区分大小写的字符串匹配，则可以更新 **__FUnloadDelayLoadedDLL2**使用一个 CRT 字符串函数或 Windows API 调用。

请参阅[卸载延迟加载的 DLL](../../build/reference/unloading-a-delay-loaded-dll.md)有关详细信息。

## <a name="see-also"></a>请参阅

[延迟加载 DLL 的链接器支持](../../build/reference/linker-support-for-delay-loaded-dlls.md)
