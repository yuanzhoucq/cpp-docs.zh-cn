---
title: C 运行时错误 R6035
ms.date: 11/04/2016
f1_keywords:
- R6035
helpviewer_keywords:
- R6035
ms.assetid: f8fb50b8-18bf-4258-b96a-b0a9de468d16
ms.openlocfilehash: 7c497347689bcfc5528280bd22aa5183d5fafd61
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80196999"
---
# <a name="c-runtime-error-r6035"></a>C 运行时错误 R6035

Microsoft Visual C++运行时库，错误 R6035-此应用程序中的模块正在初始化模块的全局安全 cookie，而依赖于该安全 cookie 的函数处于活动状态。  调用 __security_init_cookie 前面的。

首次使用 global security cookie 之前，必须先调用[__security_init_cookie](../../c-runtime-library/reference/security-init-cookie.md) 。

全局安全 cookie 用于在使用[/gs （缓冲区安全检查）](../../build/reference/gs-buffer-security-check.md)和使用结构化异常处理的代码中编译的代码中进行缓冲区溢出保护。 实质上，在进入溢出保护的函数时，cookie 会置于堆栈上，并在退出时，将堆栈上的值与全局 cookie 进行比较。 它们之间的任何差异表明发生了缓冲区溢出，并导致程序立即终止。

错误 R6035 指示在输入受保护的函数后，对 `__security_init_cookie` 的调用。 如果执行继续，则将检测到虚假的缓冲区溢出，因为堆栈上的 cookie 将不再与全局 cookie 匹配。

请看下面的 DLL 示例。 DLL 入口点通过链接器[/ENTRY （入口点符号）](../../build/reference/entry-entry-point-symbol.md)选项设置为 DllEntryPoint。 这会绕过 CRT 初始化，这通常会初始化全局安全 cookie，因此 DLL 本身必须调用 `__security_init_cookie`。

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

此示例将生成错误 R6035，因为 DllEntryPoint 使用结构化异常处理，因此使用安全 cookie 来检测缓冲区溢出。 在调用 DllInitialize 时，全局安全 cookie 已放在堆栈上。

在此示例中演示了正确的方法：

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

在这种情况下，DllEntryPoint 不会受到缓冲区溢出的保护（它没有本地字符串缓冲区并且不使用结构化异常处理）;因此，它可以安全地调用 `__security_init_cookie`。 然后，它调用受保护的 helper 函数。

> [!NOTE]
>  错误消息 R6035 仅由 x86 调试 CRT 生成，并且仅用于结构化异常处理，但条件是所有平台上的错误和异常处理的所有形式（如C++ EH）。

## <a name="see-also"></a>另请参阅

[MSVC 中的安全功能](https://blogs.msdn.microsoft.com/vcblog/2017/06/28/security-features-in-microsoft-visual-c/)
