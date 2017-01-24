---
title: "指定要延迟加载的 DLL | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/DELAYLOAD 链接器选项"
  - "DLL 的延迟加载"
  - "DLL 的延迟加载, 指定"
  - "DELAYLOAD 链接器选项"
ms.assetid: 94cbecfe-7a42-40d1-a618-9f2786bac0d8
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 指定要延迟加载的 DLL
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

您可以指定哪个 Dll 延迟加载 [\/delayload](../../build/reference/delayload-delay-load-import.md)：`dllname`链接器选项。  如果您不打算使用您自己的一个帮助程序函数版本，您还必须链接您的程序与 delayimp.lib （对于桌面应用程序） 或 dloadhelper.lib （针对应用商店应用）。  
  
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
  
 生成项目的调试版本。  使用调试器单步调试该代码，您会注意到只有在您调用到`MessageBox`时才加载该 user32.dll。  
  
## 请参阅  
 [链接器的延迟加载 DLL 支持](../../build/reference/linker-support-for-delay-loaded-dlls.md)