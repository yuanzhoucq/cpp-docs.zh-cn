---
title: 错误 C1055
ms.date: 11/04/2016
f1_keywords:
- C1055
helpviewer_keywords:
- C1055
ms.assetid: a9fb9190-d7eb-4d5f-b1a2-a41e584a28c1
ms.openlocfilehash: e6df4870d7af49c369be7e513791955599c48326
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62390641"
---
# <a name="fatal-error-c1055"></a>错误 C1055

编译器限制： 超出键

源代码文件包含的符号太多。 编译器用尽了符号表的哈希键。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用以下可能的解决方案进行修复

1. 将源文件拆分为较小的文件。

1. 消除不必要的标头文件。

1. 重复使用而不是创建新的临时和全局变量。