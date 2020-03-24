---
title: 错误 C1054
ms.date: 11/04/2016
f1_keywords:
- C1054
helpviewer_keywords:
- C1054
ms.assetid: 9cfb7307-b22a-4418-b7c0-2621b0ab5b1b
ms.openlocfilehash: d094d0892d43a5f9894f03538f72e59b57bad6db
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80204459"
---
# <a name="fatal-error-c1054"></a>错误 C1054

编译器限制：初始值设定项嵌套太深

代码超出了初始值设定项的嵌套限制（10-15 级别，具体取决于所初始化的类型的组合）。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用以下可能的解决方案进行修复

1. 简化要初始化的数据类型，以减少嵌套。

1. 在声明后，在单独的语句中初始化变量。
