---
title: C 运行时错误 R6035
ms.date: 11/04/2016
f1_keywords:
- R6035
helpviewer_keywords:
- R6035
ms.assetid: f8fb50b8-18bf-4258-b96a-b0a9de468d16
ms.openlocfilehash: ff3cd0259df92aa5cdade3f78a240e69f8f6f7de
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377483"
---
# <a name="c-runtime-error-r6035"></a>C 运行时错误 R6035

Microsoft Visual C++运行时库，错误 R6035 - 此应用程序中的一个模块正在初始化模块的全局安全 Cookie，而依赖于该安全 Cookie 的函数处于活动状态。  提前致电__security_init_cookie。

在首次使用全局安全 Cookie 之前，必须调用[__security_init_cookie。](../../c-runtime-library/reference/security-init-cookie.md)

全局安全 Cookie 用于使用[/GS （缓冲区安全检查）](../../build/reference/gs-buffer-security-check.md)编译的代码和使用结构化异常处理的代码中的缓冲区溢出保护。 基本上，在进入受溢出保护的函数时，将 Cookie 放在堆栈上，在退出时，堆栈上的值与全局 Cookie 进行比较。 它们之间的任何差异都表明发生了缓冲区溢出，导致程序立即终止。

错误 R6035 表示在输入`__security_init_cookie`受保护函数后对进行了调用。 如果继续执行，将检测到虚假缓冲区溢出，因为堆栈上的 Cookie 将不再与全局 Cookie 匹配。

请考虑以下 DLL 示例。 DLL 入口点通过链接器[/ENTRY（入口符号）](../../build/reference/entry-entry-point-symbol.md)选项设置为 DllEntryPoint。 这绕过了 CRT 的初始化，该初始化通常会初始化全局安全 Cookie，因此 DLL 本身`__security_init_cookie`必须调用 。

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

此示例将生成错误 R6035，因为 DllEntryPoint 使用结构化异常处理，因此使用安全 Cookie 检测缓冲区溢出。 在调用 Dll 初始化时，全局安全 Cookie 已放在堆栈上。

此示例演示了正确的方法：

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

在这种情况下，DllEntryPoint 不受缓冲区溢出的保护（它没有本地字符串缓冲区，并且不使用结构化异常处理）;因此，它可以安全地调用`__security_init_cookie`。 然后，它调用受保护的帮助器函数。

> [!NOTE]
> 错误消息 R6035 仅由 x86 调试 CRT 生成，仅用于结构化异常处理，但条件是所有平台上的错误，以及所有形式的异常处理（如 C++ EH）。

## <a name="see-also"></a>另请参阅

[MSVC 中的安全功能](https://blogs.msdn.microsoft.com/vcblog/2017/06/28/security-features-in-microsoft-visual-c/)
