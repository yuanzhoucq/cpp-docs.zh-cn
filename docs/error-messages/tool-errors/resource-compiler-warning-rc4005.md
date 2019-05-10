---
title: 资源编译器警告 RC4005
ms.date: 11/04/2016
f1_keywords:
- RC4005
helpviewer_keywords:
- RC4005
ms.assetid: 71f03b4a-c9a9-415d-920f-bf2e58507f93
ms.openlocfilehash: 571c4ac285e9477b017dbc21cf9ff733539759d2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62346179"
---
# <a name="resource-compiler-warning-rc4005"></a>资源编译器警告 RC4005

identifier： 宏重定义

两次定义的标识符。 编译器使用在第二个宏的定义。

可以通过在命令行上和与代码中定义宏导致该警告`#define`指令。 它还可以通过从包含文件中导入的宏导致。

若要消除此警告，请删除其中一个定义，或使用`#undef`指令之前第二个定义。