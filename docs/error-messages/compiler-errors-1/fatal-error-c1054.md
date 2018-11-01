---
title: 错误 C1054
ms.date: 11/04/2016
f1_keywords:
- C1054
helpviewer_keywords:
- C1054
ms.assetid: 9cfb7307-b22a-4418-b7c0-2621b0ab5b1b
ms.openlocfilehash: 0bfd0c03378b1a9c616a014ac96153b3ab04af9d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50569191"
---
# <a name="fatal-error-c1054"></a>错误 C1054

编译器限制： 初始值设定项嵌套太深

代码超出了初始值设定项 （10-15 级别，具体取决于正在初始化的类型的组合） 的嵌套限制。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用以下可能的解决方案进行修复

1. 简化正在初始化以减少嵌套的数据类型。

1. 声明后初始化单独的语句中的变量。