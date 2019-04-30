---
title: 错误 C1009
ms.date: 11/04/2016
f1_keywords:
- C1009
helpviewer_keywords:
- C1009
ms.assetid: dcc8383c-3362-4c47-9c26-25d2451ebd53
ms.openlocfilehash: c4654d37f5ce184f6fa5b8888e6ca0184267be07
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62364306"
---
# <a name="fatal-error-c1009"></a>错误 C1009

编译器限制： 宏嵌套太深

编译器尝试进行一次展开太多的宏。 编译器的限制为 256 级嵌套宏。 将嵌套的宏拆分为更简单的宏。