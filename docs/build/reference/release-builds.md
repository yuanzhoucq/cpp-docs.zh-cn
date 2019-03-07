---
title: 发行版本
ms.date: 11/04/2016
helpviewer_keywords:
- debugging [C++], release builds
- release builds
- debug builds, converting to release build
ms.assetid: fa9a78fa-f4b5-4722-baf4-aec655c4ff0f
ms.openlocfilehash: 346beace1979871cfd9bf4ee0d487e7f85a26eaa
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57426090"
---
# <a name="release-builds"></a>发行版本

发布版本使用的优化。 当您使用优化创建发布版本时，编译器将生成符号化调试信息。 符号化调试信息，以及这一事实，代码不会生成用于跟踪和断言没有调用，表示可执行文件的大小会减少，因此将更快。

本部分介绍为什么以及何时想要从调试版本更改为发布版本的信息。 它还介绍了一些从调试版本更改为发布版本时可能遇到的问题：

- [创建发布版本](../../build/reference/how-to-create-a-release-build.md)

- [创建发行版本时遇到的常见问题](../../build/reference/common-problems-when-creating-a-release-build.md)

- [修复发行版本问题](../../build/reference/fixing-release-build-problems.md)

   - [检查 ASSERT 语句](../../build/reference/using-verify-instead-of-assert.md)

   - [使用调试版本检查内存改写](../../build/reference/using-the-debug-build-to-check-for-memory-overwrite.md)

   - [调试版本生成](../../build/reference/how-to-debug-a-release-build.md)

   - [检查内存改写](../../build/reference/checking-for-memory-overwrites.md)

## <a name="see-also"></a>请参阅

[在 Visual Studio 中生成 C++ 项目](../../ide/building-cpp-projects-in-visual-studio.md)<br/>
[C/C++ 生成参考](../../build/reference/c-cpp-building-reference.md)
