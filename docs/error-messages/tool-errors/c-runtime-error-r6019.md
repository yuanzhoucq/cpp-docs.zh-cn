---
title: C 运行时错误 R6019 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6019
dev_langs:
- C++
helpviewer_keywords:
- R6019
ms.assetid: 8129923e-7db2-40ee-9602-def9365f8d28
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 13653f54551501d5e35bd1285dc3d3f1a74343f1
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/08/2018
ms.locfileid: "48861587"
---
# <a name="c-runtime-error-r6019"></a>C 运行时错误 R6019

无法打开控制台设备

> [!NOTE]
> 如果运行应用时遇到此错误消息，该应用已关闭，因为它尝试访问控制台中，但它还没有足够的权限。 有多种原因引起此错误，但通常是因为必须以管理员身份运行程序或程序中是一个 bug。
>
> 可以尝试以下步骤来修复此错误：
>
> - 以管理员身份运行程序。
> - 使用**应用程序和功能**或**程序和功能**页**控制面板**来修复或重新安装该程序。
> - 检查**Windows Update**中**控制面板**的软件更新。
> - 检查应用程序的更新版本。 如果问题仍然存在，请与应用供应商联系。

**程序员提供的的信息**

此错误是因为应用程序调用的控制台函数，但操作系统未授予对控制台的访问。 除在调试模式下，控制台函数通常不允许在 Microsoft Store 应用中。 如果您的应用程序需要管理员特权才能运行，请确保它已安装默认情况下以管理员身份运行。