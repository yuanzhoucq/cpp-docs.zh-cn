---
title: C++ 安全性最佳做法
ms.date: 05/08/2018
f1_keywords:
- securitybestpracticesVC
helpviewer_keywords:
- Visual C++, security
- security [C++]
- security [C++], best practices
ms.assetid: 86acaccf-cdb4-4517-bd58-553618e3ec42
ms.openlocfilehash: 6816a7ffbc09d0e01659dd56282e238fdbfc4a27
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50462294"
---
# <a name="security-best-practices-for-c"></a>C++ 安全性最佳做法

本文包含有关安全工具和做法的信息。 使用这些工具和做法并不会使应用程序免受攻击，但能降低攻击成功的可能性。

## <a name="visual-c-security-features"></a>Visual C++ 安全功能

这些安全功能内置于 Visual C++ 编译器和链接器中：

[/guard（启用控制流保护）](../build/reference/guard-enable-control-flow-guard.md)<br/>
使编译器在编译时，分析为间接调用目标的控制流，然后插入代码以在运行时验证目标。

[/GS（缓冲区安全检查）](../build/reference/gs-buffer-security-check.md)<br/>
指示编译器将溢出检测代码插入到面临被利用风险的函数中。 检测到溢出时，则停止执行。 默认情况下，此选项处于启用状态。

[/SAFESEH（图像具有安全异常处理程序）](../build/reference/safeseh-image-has-safe-exception-handlers.md)<br/>
指示链接器在输出映像中包括一个包含每个异常处理程序的地址的表。 在运行时，操作系统使用此表来确保只执行合法的异常处理程序。 这有助于防止在运行时执行由恶意攻击引入的异常处理程序。 默认情况下关闭此选项。

[/NXCOMPAT](../build/reference/nxcompat.md)， [/NXCOMPAT （与数据执行保护兼容）](../build/reference/nxcompat-compatible-with-data-execution-prevention.md)这些编译器和链接器选项启用数据执行保护 (DEP) 兼容性。 DEP 可防止 CPU 执行非代码页。

[/analyze（代码分析）](../build/reference/analyze-code-analysis.md)<br/>
此编译器选项将激活报告潜在安全问题（比如缓冲区溢出、未初始化的内存、null 指针取消引用和内存泄漏）的代码分析。 默认情况下关闭此选项。 有关详细信息，请参阅[的代码分析 C/c + + 概述](/visualstudio/code-quality/code-analysis-for-c-cpp-overview)。

[/DYNAMICBASE（使用地址空间布局随机化）](../build/reference/dynamicbase-use-address-space-layout-randomization.md)<br/>
通过使用此链接器选项，可以生成一个在执行开始时可在内存的不同位置加载的可执行映像。 此选项还使内存中的堆栈位置更加不可预测。

## <a name="security-enhanced-crt"></a>增强了安全性的 CRT

已扩充 C 运行库 (CRT) 以包括面临安全风险的函数的安全版本（例如，未经检查的 `strcpy` 字符串复制函数）。 由于这些函数的早期、不安全版本现已被弃用，因此它们将导致编译时警告。 建议您使用这些 CRT 函数的安全版本，而不是选择禁止显示编译警告。 有关详细信息，请参阅 [Security Features in the CRT](../c-runtime-library/security-features-in-the-crt.md)。

## <a name="safeint-library"></a>SafeInt 库

[SafeInt 库](../windows/safeint-library.md)有助于防止整数溢出以及应用程序执行数学运算时可能发生其他可利用错误。 `SafeInt`库包含[SafeInt 类](../windows/safeint-class.md)，则[SafeIntException 类](../windows/safeintexception-class.md)，以及几个[SafeInt 函数](../windows/safeint-functions.md)。

`SafeInt` 类可防止整数溢出和被零除攻击。 您可以使用它处理不同类型的值之间的比较。 它提供了两个错误处理策略。 默认策略是针对引发 `SafeInt` 类异常的 `SafeIntException` 类，以报告无法完成数学运算的原因。 第二个策略针对 `SafeInt` 类，用以停止程序的执行。 还可以定义自定义策略。

每个 `SafeInt` 函数各保护一个数学运算免于出现可被利用的错误。 您可使用两种不同的参数，而不必将它们转换为相同类型。 若要保护多个数学运算，请使用 `SafeInt` 类。

## <a name="checked-iterators"></a>经过检查的迭代器

经过检查的迭代器强制实施容器边界。 默认情况下，当检查的迭代器超出范围时，它将生成异常并终止程序的执行。 检查迭代器提供了其他级别的响应取决于分配给预处理器的值定义，如 **\_SECURE\_SCL\_引发**和 **\_迭代器\_调试\_级别**。 例如，在**\_迭代器\_调试\_LEVEL = 2**，经检查迭代器提供了全面的正确性检查处于调试模式，这可供使用断言。 有关详细信息，请参阅[Checked Iterators](../standard-library/checked-iterators.md)并[\_迭代器\_调试\_级别](../standard-library/iterator-debug-level.md)。

## <a name="code-analysis-for-managed-code"></a>托管代码的代码分析

托管代码的代码分析，又称 FxCop，是检查程序集与 .NET Framework 设计准则的一致性的工具。 FxCop 分析各个程序集中的代码和元数据以检查下列区域的缺陷：

- 库设计

- 本地化

- 命名约定

- 性能

- 安全性

## <a name="windows-application-verifier"></a>Windows 应用程序验证工具

[Application Verifier (AppVerifier)](/windows-hardware/drivers/debugger/application-verifier
)可帮助你识别潜在的应用程序兼容性、 稳定性和安全问题。

AppVerifier 可监视应用程序使用操作系统的方式。 在应用程序运行的过程中，此工具会监视文件系统、注册表、内存和 API，并针对它发现的问题给出源代码修复的建议。

您可以使用 AppVerifier 来：

- 检测由常见编程错误导致的潜在应用程序兼容性错误。

- 检查应用程序是否存在内存相关问题。

- 确定应用程序中的潜在安全问题。

## <a name="windows-user-accounts"></a>Windows 用户帐户

使用属于管理员组的 Windows 用户帐户将使开发人员和引申到的相关客户暴露在安全风险下。 有关详细信息，请参阅[用户组的成员身份运行](running-as-a-member-of-the-users-group.md)并[如何用户帐户控制 (UAC) 会影响应用程序](how-user-account-control-uac-affects-your-application.md)。

## <a name="guidance-for-speculative-execution-side-channels"></a>推理执行端通道的指南

有关如何识别和缓解针对 c + + 软件中的推理执行端通道硬件漏洞的信息，请参阅[推理执行端通道的 c + + 开发人员指南](developer-guidance-speculative-execution.md)。

## <a name="see-also"></a>请参阅

<xref:System.Security> <br/>
[安全性](/dotnet/standard/security/index)<br/>
[用户帐户控制 (UAC) 如何影响应用程序](how-user-account-control-uac-affects-your-application.md)