---
title: C 运行时错误 R6017 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6017
dev_langs:
- C++
helpviewer_keywords:
- R6017
ms.assetid: df3ec5f5-6771-4648-ba06-0e26c6a1cc6a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: acd380c8eee7b4fa1b325e8dee0bfad55a42c790
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/08/2018
ms.locfileid: "48861065"
---
# <a name="c-runtime-error-r6017"></a>C 运行时错误 R6017

意外的多线程锁定错误

> [!NOTE]
> 如果运行应用时遇到此错误消息，该应用已关闭，因为它具有内部问题。 有多种原因引起此错误，但通常由应用程序的代码中的一个缺陷。
>
> 可以尝试以下步骤来修复此错误：
>
> - 使用**应用程序和功能**或**程序和功能**页**控制面板**来修复或重新安装该程序。
> - 检查**Windows Update**中**控制面板**的软件更新。
> - 检查应用程序的更新版本。 如果问题仍然存在，请与应用供应商联系。

**程序员提供的的信息**

该过程尝试访问系统资源上的 C 运行时多线程锁定时收到了意外的错误。 如果该过程会无意中更改运行时堆数据，通常会出现此错误。 但是，它可以也会导致运行时库或操作系统代码中出现内部错误。

若要解决此问题，请检查在代码中的堆损坏错误。 有关详细信息和示例，请参阅[CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。 接下来，检查您的应用程序部署使用最新可再发行组件。 有关信息，请参阅[Visual c + + 中的部署](../../ide/deployment-in-visual-cpp.md)。