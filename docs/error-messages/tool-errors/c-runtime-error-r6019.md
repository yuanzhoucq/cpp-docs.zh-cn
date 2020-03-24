---
title: C 运行时错误 R6019
ms.date: 11/04/2016
f1_keywords:
- R6019
helpviewer_keywords:
- R6019
ms.assetid: 8129923e-7db2-40ee-9602-def9365f8d28
ms.openlocfilehash: b647825b7e856be9dc51a5a652be87a4cc6d0e23
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197257"
---
# <a name="c-runtime-error-r6019"></a>C 运行时错误 R6019

无法打开控制台设备

> [!NOTE]
> 如果在运行应用程序时遇到此错误消息，则该应用程序已关闭，因为它尝试访问控制台，但它没有足够的权限。 此错误有几个可能的原因，但通常是因为程序必须以管理员身份运行，或者程序中存在 bug。
>
> 可以尝试以下步骤来修复此错误：
>
> - 以管理员身份运行该程序。
> - 使用**控制面板**中的 "**应用和功能**" 或 "**程序和功能**" 页来修复或重新安装该程序。
> - 检查 "**控制面板**" 中的 "软件更新" **Windows 更新**。
> - 检查应用的更新版本。 如果问题仍然存在，请与应用程序供应商联系。

**面向程序员的信息**

之所以发生此错误，是因为应用程序调用了控制台函数，但操作系统并未向控制台授予访问权限。 在调试模式下，通常不允许在 Microsoft Store 应用中使用控制台函数。 如果你的应用程序需要管理员权限才能运行，请确保它已安装为默认以管理员身份运行。
