---
title: "C 运行时错误 R6035 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: R6035
dev_langs: C++
helpviewer_keywords: R6035
ms.assetid: f8fb50b8-18bf-4258-b96a-b0a9de468d16
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6f0f6e34ef6c95d4c1942cdc1348000213647b0b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="c-runtime-error-r6035"></a>C 运行时错误 R6035
函数依赖于该安全 cookie 处于活动状态时，Microsoft Visual c + + 运行时库，错误 R6035-此应用程序中的模块正在初始化的模块的全局安全 cookie。  调用 __security_init_cookie 更早版本。  
  
 [__security_init_cookie](../../c-runtime-library/reference/security-init-cookie.md)必须在全局安全 cookie 首次使用之前调用。  
  
 全局安全 cookie 用于与编译的代码中的缓冲区溢出保护[/GS （缓冲区安全检查）](../../build/reference/gs-buffer-security-check.md)并在代码中使用结构化的异常处理。 实质上，在进入受到溢出保护的函数，cookie 被置于堆栈上，并在退出时，在堆栈上的值进行比较与全局 cookie。 它们之间存在任何差异指示缓冲区溢出出现，并导致该程序的立即终止。  
  
 错误 R6035 指示调用`__security_init_cookie`后输入受保护的函数创建的。 如果要继续执行，因为在堆栈上的 cookie 将不再匹配全局 cookie 检测虚假的缓冲区溢出。  
  
 例如，以下 DLL。 通过链接器的 DLL 入口点设置为 DllEntryPoint [/ENTRY （入口点符号）](../../build/reference/entry-entry-point-symbol.md)选项。 这会跳过的 CRT 初始化这通常会初始化全局安全 cookie，使 DLL 本身必须调用`__security_init_cookie`。  
  
```  
// Wrong way to call __security_init_cookie  
DllEntryPoint(...) {  
   DllInitialize();  
   ...  
   __try {  
      ...  
   } __except()... {  
      ...  
   }  
}  
  
void DllInitialize() {  
   __security_init_cookie();  
}  
```  
  
 此示例将生成错误 R6035，因为 DllEntryPoint 使用结构化的异常处理，并因此使用安全 cookie 来检测缓冲区溢出。 调用 DllInitialize 时，全局安全 cookie 已置于堆栈上。  
  
 在此示例演示了正确的方法：  
  
```  
// Correct way to call __security_init_cookie  
DllEntryPoint(...) {  
   __security_init_cookie();  
   DllEntryHelper();  
}  
  
void DllEntryHelper() {  
   ...  
   __try {  
      ...  
   } __except()... {  
      ...  
   }  
}  
```  
  
 在这种情况下，DllEntryPoint 不会受到缓冲区溢出 （它具有任何本地字符串缓冲区和不使用结构化的异常处理）;因此它可以安全调用`__security_init_cookie`。 然后，它调用受保护的帮助器函数。  
  
> [!NOTE]
>  错误消息 R6035 仅通过 x86 生成调试 CRT，并仅为结构化的异常处理，但条件错误在所有平台上以及为各种形式的异常处理，例如 c + + EH。  
  
## <a name="see-also"></a>另请参阅  
 [编译器安全检查深入介绍](http://go.microsoft.com/fwlink/?linkid=7260)