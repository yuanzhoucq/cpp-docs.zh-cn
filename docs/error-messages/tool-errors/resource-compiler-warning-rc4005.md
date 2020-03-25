---
title: 资源编译器警告 RC4005
ms.date: 11/04/2016
f1_keywords:
- RC4005
helpviewer_keywords:
- RC4005
ms.assetid: 71f03b4a-c9a9-415d-920f-bf2e58507f93
ms.openlocfilehash: c428fefa90cceed6a8bc9b7f6e4b95ec2db5e039
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182404"
---
# <a name="resource-compiler-warning-rc4005"></a>资源编译器警告 RC4005

"identifier"：宏重定义

标识符定义了两次。 编译器使用第二个宏定义。

通过在命令行和带 `#define` 指令的代码中定义宏，可导致此警告。 它也可能是从包含文件导入的宏导致的。

若要消除此警告，请删除其中一个定义，或者在第二个定义之前使用 `#undef` 指令。
