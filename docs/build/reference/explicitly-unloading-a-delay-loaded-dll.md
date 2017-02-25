---
title: "显式卸载延迟加载的 DLL | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/DELAY:UNLOAD 链接器选项"
  - "__FUnloadDelayLoadedDLL2"
  - "DELAY:UNLOAD 链接器选项"
  - "DLL 的延迟加载, 卸载"
ms.assetid: 1c4c5172-fd06-45d3-9e4f-f12343176b3c
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 显式卸载延迟加载的 DLL
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

[\/delay](../../build/reference/delay-delay-load-import-settings.md):unload 链接器选项使您能够卸载被延迟加载的 DLL。  默认情况下，当代码卸载 DLL 时（使用 \/delay:unload 和 **\_\_FUnloadDelayLoadedDLL2**），延迟加载的导入将保留在导入地址表 \(IAT\) 中。  但是，如果您在链接器命令行上使用 \/delay:unload，Helper 函数将支持显式卸载 DLL，将 IAT 重置为其原始格式；当前无效的指针将被覆盖。  IAT 是 [ImgDelayDescr](../../build/reference/calling-conventions-parameters-and-return-type.md) 中的一个字段，它包含原始 IAT 副本（如果存在）的地址。  
  
## 示例  
  
### 代码  
  
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
  
### 注释  
 关于卸载延迟加载的 DLL 的重要说明：  
  
-   在文件 \\VC7\\INCLUDE\\DELAYHLP.CPP 中可以找到 **\_\_FUnloadDelayLoadedDLL2** 函数的实现。  
  
-   **\_\_FUnloadDelayLoadedDLL2** 函数的名称参数必须与导入库中所包含的名称参数完全匹配，包括大小写匹配，该字符串也显示在映像中的导入表中。  可以用 [DUMPBIN \/DEPENDENTS](../../build/reference/dependents.md) 查看导入库中的内容。  如果匹配时不需要区分大小写，可更新 **\_\_FUnloadDelayLoadedDLL2** 以使用其中一个 CRT 字符串函数或 Windows API 调用。  
  
 有关更多信息，请参见[卸载延迟加载的 DLL](../../build/reference/unloading-a-delay-loaded-dll.md)。  
  
## 请参阅  
 [链接器的延迟加载 DLL 支持](../../build/reference/linker-support-for-delay-loaded-dlls.md)