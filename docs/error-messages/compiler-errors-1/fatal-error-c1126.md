---
title: 错误 C1126
ms.date: 11/04/2016
f1_keywords:
- C1126
helpviewer_keywords:
- C1126
ms.assetid: f22b26a6-8ad7-47cf-a237-196c8ea60aca
ms.openlocfilehash: a6c9d06cd087eb4462ae475cc1f6d64ba451887f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203619"
---
# <a name="fatal-error-c1126"></a>错误 C1126

"identifier"：自动分配超出大小

为函数的局部变量分配的空间（加上编译器使用的有限空间量，如用于交换函数的额外20个字节）超过限制。

若要更正此错误，请使用 `malloc` 或 `new` 分配大量的数据。
