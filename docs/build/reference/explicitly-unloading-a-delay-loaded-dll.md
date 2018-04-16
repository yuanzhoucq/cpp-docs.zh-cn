---
title: "显式卸载延迟加载的 DLL |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- /DELAY:UNLOAD linker option
- DELAY:UNLOAD linker option
- __FUnloadDelayLoadedDLL2
- delayed loading of DLLs, unloading
ms.assetid: 1c4c5172-fd06-45d3-9e4f-f12343176b3c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b26a1a17952693be9db6a80649aad2c40227d53e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="explicitly-unloading-a-delay-loaded-dll"></a>显式卸载延迟加载的 DLL
[/延迟](../../build/reference/delay-delay-load-import-settings.md): unload 链接器选项允许您卸载已被延迟加载的 DLL。 默认情况下，当你的代码卸载 DLL (使用 /delay: unload 和**__FUnloadDelayLoadedDLL2**)，在导入地址表 (IAT) 中保留的延迟加载导入。 但是，如果你使用 /delay: unload 链接器命令行上，则 helper 函数将支持显式卸载 DLL，正在 IAT 重置为其原始格式;现在无效指针将被覆盖。 IAT 是中的字段[ImgDelayDescr](../../build/reference/calling-conventions-parameters-and-return-type.md)包含原始 IAT 的副本的地址 （如果存在）。  
  
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
  
-   你可以找到的实现**__FUnloadDelayLoadedDLL2**文件中的函数 \VC7\INCLUDE\DELAYHLP。CPP。  
  
-   Name 参数**__FUnloadDelayLoadedDLL2**函数必须完全匹配 （包括用例） 导入库包含的内容 （即字符串也在映像中导入表中）。 你可以查看的导入库的内容[DUMPBIN /DEPENDENTS](../../build/reference/dependents.md)。 如果需要不区分大小写的字符串匹配，则可以更新**__FUnloadDelayLoadedDLL2**若要使用 CRT 字符串函数或 Windows API 调用之一。  
  
 请参阅[卸载延迟加载的 DLL](../../build/reference/unloading-a-delay-loaded-dll.md)有关详细信息。  
  
## <a name="see-also"></a>请参阅  
 [延迟加载 DLL 的链接器支持](../../build/reference/linker-support-for-delay-loaded-dlls.md)