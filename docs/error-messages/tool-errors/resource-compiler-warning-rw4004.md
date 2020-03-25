---
title: 资源编译器警告 RW4004
ms.date: 11/04/2016
f1_keywords:
- RW4004
helpviewer_keywords:
- RW4004
ms.assetid: 596b6a89-9ce7-4ba7-bdcb-e8054c7efafa
ms.openlocfilehash: ca0fb271a5ab43994ec37cc8d59c33877903f6e8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182339"
---
# <a name="resource-compiler-warning-rw4004"></a>资源编译器警告 RW4004

ASCII 字符不等价于虚拟键代码

字符串文本已用于 VIRTKEY 类型快捷键中的虚拟键代码。

此警告允许你继续操作，但请注意，生成的快捷键可能与你指示的字符串不匹配。 （VIRTKEYs 与 ASCII 快捷键使用不同的键代码。）

尽管字符串文本在语法上是有效的，但您只能通过使用**VK_\*** WINDOWS 中的 #define 值来确保获取所需的快捷键。
