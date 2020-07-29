---
title: 编译器警告（等级 4）C4510
description: 编译器警告 C4510 说明和解决方案。
ms.date: 09/22/2019
f1_keywords:
- C4510
helpviewer_keywords:
- C4510
ms.assetid: fd28d1d4-ad27-4dad-94c0-9dba46c93180
ms.openlocfilehash: e4bb688266d9fe638978d2d3fa2666b83b3e6cc9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225249"
---
# <a name="compiler-warning-level-4-c4510"></a>编译器警告（等级 4）C4510

> "*class*"：未能生成默认构造函数

编译器无法为指定的类生成默认构造函数，该构造函数没有用户定义的构造函数。 无法创建此类型的对象。

有几种情况会阻止编译器生成默认构造函数，包括：

- **`const`** 数据成员。

- 一个引用的数据成员。

若要解决此问题，请为初始化这些成员的类创建用户定义的默认构造函数。
