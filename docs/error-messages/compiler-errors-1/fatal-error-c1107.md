---
title: 错误 C1107
ms.date: 11/04/2016
f1_keywords:
- C1107
helpviewer_keywords:
- C1107
ms.assetid: 541a4d9f-10bc-4dd8-b68e-15e548f3dc0a
ms.openlocfilehash: 6e8df232b4d3f3b18eb7c37bcc418ca030a93aef
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203783"
---
# <a name="fatal-error-c1107"></a>错误 C1107

找不到程序集 "file"：请使用/AI 或通过设置 LIBPATH 环境变量指定程序集搜索路径

一个元数据文件被传递到编译器无法找到的[#using](../../preprocessor/hash-using-directive-cpp.md)指令中。

LIBPATH （在 `#using`的主题中介绍）和[/AI](../../build/reference/ai-specify-metadata-directories.md)编译器选项允许你指定编译器将在其中查找引用的元数据文件的目录。
