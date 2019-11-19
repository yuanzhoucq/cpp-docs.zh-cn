---
title: 将 C++ 项目配置为可用于 ARM 处理器
ms.date: 07/11/2018
ms.assetid: 3d95f221-656a-480d-9651-9ad263895747
ms.openlocfilehash: 0dc87e9a119f82c03a11dde0d90c27de71618f5a
ms.sourcegitcommit: e805200eaef4fe7a65a00051bbd305273af94fe7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/18/2019
ms.locfileid: "74163428"
---
# <a name="configure-c-projects-for-arm-processors"></a>将 C++ 项目配置为可用于 ARM 处理器

文档的本节包含有关如何使用 MSVC 生成工具来面向 ARM 硬件的信息。

## <a name="in-this-section"></a>本节内容

[ARM ABI 约定概述](overview-of-arm-abi-conventions.md)\
描述由 ARM 上的 Windows 用于进行注册、调用约定以及处理异常的应用程序二进制接口。

[ARM64 ABI 约定概述](arm64-windows-abi-conventions.md)\
介绍 ARM64 上的 Windows 用于注册使用、调用约定和异常处理的应用程序二进制接口。

[常见的 MSVC ARM 迁移问题](common-visual-cpp-arm-migration-issues.md)\
描述了通常被认为可以跨体系结构移植的 C++ 代码元素，但它们为 ARM 产生的结果不同于为 x86 和 x64 产生的结果。

[ARM 异常处理](arm-exception-handling.md)\
描述了在 ARM 上的 Windows 中在结构化异常处理期间用于展开堆栈的编码方案。

[ARM64 异常处理](arm64-exception-handling.md)\
描述在 ARM64 上的 Windows 中的结构化异常处理期间用于堆栈展开的编码方案。

## <a name="related-sections"></a>相关章节

[ARM 内部函数](../intrinsics/arm-intrinsics.md)\
描述适用于使用 ARM 架构的处理器的编译器内部函数。

[ARM64 内部函数](../intrinsics/arm-intrinsics.md)\
介绍了使用 ARM64 体系结构的处理器的编译器内部函数。
