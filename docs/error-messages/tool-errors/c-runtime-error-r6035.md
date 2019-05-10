---
title: C 运行时错误 R6035
ms.date: 11/04/2016
f1_keywords:
- R6035
helpviewer_keywords:
- R6035
ms.assetid: f8fb50b8-18bf-4258-b96a-b0a9de468d16
ms.openlocfilehash: cbade3ce8686c8c293b8d40a73c546805e42215d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399975"
---
# <a name="c-runtime-error-r6035"></a>C 运行时错误 R6035

Microsoft VisualC++运行时库、 错误 R6035-此应用程序中的模块依赖于该安全 cookie 的函数处于活动状态时，正在初始化模块的全局安全 cookie。  先前调用 __security_init_cookie。

[__security_init_cookie](../../c-runtime-library/reference/security-init-cookie.md)全局安全 cookie 在首次使用前，必须调用。

全局安全 cookie 用于编译的代码中的缓冲区溢出保护[/GS （缓冲区安全检查）](../../build/reference/gs-buffer-security-check.md) ，并在代码中使用结构化的异常处理。 实质上，在进入受到溢出保护的函数，cookie 被置于堆栈上，并在退出时，在堆栈上的值与全局 cookie 进行比较。 它们之间的任何差异，指示缓冲区溢出已发生，导致程序立即终止。

错误 R6035 指示调用`__security_init_cookie`后输入的受保护的函数创建的。 如果要继续执行，虚假的缓冲区溢出会检测到因为堆栈上的 cookie 将不再匹配全局 cookie。

请考虑以下 DLL 示例。 通过链接器的 DLL 入口点设置为 DllEntryPoint [/ENTRY （入口点符号）](../../build/reference/entry-entry-point-symbol.md)选项。 这将跳过的 CRT 初始化它通常将初始化全局安全 cookie，必须调用 DLL 本身`__security_init_cookie`。

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

此示例将生成错误 R6035，因为 DllEntryPoint 使用结构化的异常处理，因此会使用安全 cookie 来检测缓冲区溢出。 调用 DllInitialize 时，全局安全 cookie 已放置在堆栈上。

在此示例中演示的正确方法：

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

在这种情况下，DllEntryPoint 不保护不受缓冲区溢出 （它具有任何本地字符串缓冲区和不使用结构化的异常处理）;因此它可以安全地调用`__security_init_cookie`。 然后，它调用受保护的帮助器函数。

> [!NOTE]
>  R6035 是错误消息仅由 x86 生成调试 CRT，并仅为结构化的异常处理，但条件错误和异常的所有窗体的所有平台上处理，如C++EH。

## <a name="see-also"></a>请参阅

[MSVC 中的安全功能](https://blogs.msdn.microsoft.com/vcblog/2017/06/28/security-features-in-microsoft-visual-c/)