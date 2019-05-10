---
title: 资源编译器警告 RW4004
ms.date: 11/04/2016
f1_keywords:
- RW4004
helpviewer_keywords:
- RW4004
ms.assetid: 596b6a89-9ce7-4ba7-bdcb-e8054c7efafa
ms.openlocfilehash: bafd1084a665fc656fe184064a48e5fffc61c957
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62346075"
---
# <a name="resource-compiler-warning-rw4004"></a>资源编译器警告 RW4004

ASCII 字符不等价于虚拟键代码

字符串文本已用于 VIRTKEY 类型快捷键中的虚拟键代码。

此警告允许你继续操作，但请注意，生成的快捷键可能与你指示的字符串不匹配。 （VIRTKEYs 与 ASCII 快捷键使用不同的键代码。）

当字符串文本在语法上有效时，您只能确保获取你想使用的加速器**VK_\* #define** WINDOWS.h 中的值。