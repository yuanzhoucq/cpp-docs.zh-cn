---
title: 资源编译器警告 RC4005 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC4005
dev_langs:
- C++
helpviewer_keywords:
- RC4005
ms.assetid: 71f03b4a-c9a9-415d-920f-bf2e58507f93
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 589fd008b3927887a8144b2fc63d2cbbde2af913
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46028514"
---
# <a name="resource-compiler-warning-rc4005"></a>资源编译器警告 RC4005

identifier： 宏重定义

两次定义的标识符。 编译器使用在第二个宏的定义。

可以通过在命令行上和与代码中定义宏导致该警告`#define`指令。 它还可以通过从包含文件中导入的宏导致。

若要消除此警告，请删除其中一个定义，或使用`#undef`指令之前第二个定义。