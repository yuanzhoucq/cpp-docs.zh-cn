---
title: 错误 C1852
ms.date: 11/04/2016
f1_keywords:
- C1852
helpviewer_keywords:
- C1852
ms.assetid: fa011004-b8d6-46f1-ba80-4785e4ce137f
ms.openlocfilehash: 540febabc8f2947f11b58cf7eadee53d47f7bef3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202873"
---
# <a name="fatal-error-c1852"></a>错误 C1852

“filename”不是有效的预编译头文件

文件不是预编译头文件。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复

1. 使用 **/Yu** 或 **#pragma hdrstop**指定的无效文件。

1. 如果未另行指定，编译器将假定 .pch 为文件扩展名。
