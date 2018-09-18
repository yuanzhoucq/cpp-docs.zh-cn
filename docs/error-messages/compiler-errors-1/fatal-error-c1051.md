---
title: 错误 C1051 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1051
dev_langs:
- C++
helpviewer_keywords:
- C1051
ms.assetid: 87dcbd3b-0952-499a-bd42-64f9e8de2605
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2bbd385d685f671d171ee5aaa967e92acab7fb38
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46057933"
---
# <a name="fatal-error-c1051"></a>错误 C1051

程序数据库文件，pdbfile 具有过时的格式，将其删除并重新编译

编译器无法更新程序数据库文件的较旧的版本号。 删除该文件并重新编译您的程序与 **/Zi**或 **/ZI**。 有关详细信息，请参阅[/Z7、 /Zi、 /ZI （调试信息格式）](../../build/reference/z7-zi-zi-debug-information-format.md)