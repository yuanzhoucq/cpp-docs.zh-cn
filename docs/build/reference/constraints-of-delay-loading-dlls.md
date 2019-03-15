---
title: 延迟加载 DLL 的约束
ms.date: 11/04/2016
helpviewer_keywords:
- constraints [C++], delayed loading of DLLs
- delayed loading of DLLs, constraints
- DLLs [C++], constraints
ms.assetid: 0097ff65-550f-4a4e-8ac3-39bf6404f926
ms.openlocfilehash: e37890fcd757a52ddeff0ccd79289bbc0c35e042
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57816576"
---
# <a name="constraints-of-delay-loading-dlls"></a>延迟加载 DLL 的约束

导入延迟加载有一些约束。

- 不支持数据导入。 变通的办法是使用 `LoadLibrary`（或者，如果知道延迟加载 Helper 已加载了 DLL，则使用 `GetModuleHandle`）和 `GetProcAddress` 自己显式处理数据导入。

- 不支持延迟加载 Kernel32.dll。 延迟加载 Helper 例程执行延迟加载时需要该 DLL。

- [绑定](binding-imports.md)的入口点转发不受支持。

- 如果在延迟加载的 DLL 的入口点发生每个进程初始化，则 DLL 的延迟加载可能不会造成进程行为相同。 其他情况包括静态 TLS （线程本地存储区），使用声明[__declspec （thread)](../../cpp/thread.md)，这不处理时通过加载了 DLL `LoadLibrary`。 使用 `TlsAlloc`、`TlsFree`、`TlsGetValue` 和 `TlsSetValue` 的动态 TLS 仍可在静态或者延迟加载的 DLL 中使用。

- 初次调用静态（全局）函数后，应将其指针重新初始化为导入函数。 这是因为该函数指针在初次使用时将指向 thunk。

- 目前还没有办法在使用正常导入机制时，只延迟加载 DLL 中的特定过程。

- 不支持自定义调用约定（例如在 x86 体系结构上使用条件代码）。 此外，任何平台上都不保存浮点寄存器。 如果自定义 Helper 例程或挂钩例程使用浮点类型，则它们需要在具有浮点参数的寄存器调用约定的计算机上完全保存和恢复浮点状态。 如果在 Help 函数中调用采用数值数据处理器 (NDP) 堆栈上的浮点参数的 CRT 函数，延迟加载 CRT DLL 时请小心谨慎。

## <a name="see-also"></a>请参阅

[延迟加载 DLL 的链接器支持](linker-support-for-delay-loaded-dlls.md)<br/>
[LoadLibrary 函数](/windows/desktop/api/libloaderapi/nf-libloaderapi-loadlibrarya)<br/>
[GetModuleHandle 函数](/windows/desktop/api/libloaderapi/nf-libloaderapi-getmodulehandlea)<br/>
[GetProcAddress 函数](/windows/desktop/api/libloaderapi/nf-libloaderapi-getprocaddress)<br/>
[TlsAlloc 函数](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-tlsalloc)<br/>
[TlsFree 函数](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-tlsfree)<br/>
[TlsGetValue 函数](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-tlsgetvalue)<br/>
[TlsSetValue 函数](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-tlssetvalue)
