---
title: C 运行时错误 R6017
ms.date: 11/04/2016
f1_keywords:
- R6017
helpviewer_keywords:
- R6017
ms.assetid: df3ec5f5-6771-4648-ba06-0e26c6a1cc6a
ms.openlocfilehash: 2d868939425c11f13dffd84e28c1afee45e3b11a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197297"
---
# <a name="c-runtime-error-r6017"></a>C 运行时错误 R6017

意外多线程锁定错误

> [!NOTE]
> 如果在运行应用程序时遇到此错误消息，则该应用程序已关闭，因为它有一个内部问题。 此错误有几个可能的原因，但通常是由于应用程序的代码中的缺陷导致的。
>
> 可以尝试以下步骤来修复此错误：
>
> - 使用**控制面板**中的 "**应用和功能**" 或 "**程序和功能**" 页来修复或重新安装该程序。
> - 检查 "**控制面板**" 中的 "软件更新" **Windows 更新**。
> - 检查应用的更新版本。 如果问题仍然存在，请与应用程序供应商联系。

**面向程序员的信息**

尝试访问系统资源上的 C 运行时多线程锁时，进程收到意外错误。 如果进程无意中更改了运行时堆数据，通常会发生此错误。 但是，它也可能是由运行时库或操作系统代码中的内部错误引起的。

若要解决此问题，请检查代码中的堆损坏错误。 有关详细信息和示例，请参阅[CRT 调试堆详细信息](/visualstudio/debugger/crt-debug-heap-details)。 接下来，请检查是否正在使用适用于你的应用部署的最新可再发行组件。 有关信息，请参阅[ C++Visual 中的部署](../../windows/deployment-in-visual-cpp.md)。
