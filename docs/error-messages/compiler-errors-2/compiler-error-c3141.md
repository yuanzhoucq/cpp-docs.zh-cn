---
title: 编译器错误 C3141
ms.date: 11/04/2016
f1_keywords:
- C3141
helpviewer_keywords:
- C3141
ms.assetid: b4fd65c3-50cc-46cd-8de0-6a6d24cb9cda
ms.openlocfilehash: e19de95b5b2c967d71a4b06aca431df8ffe9dc14
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50552150"
---
# <a name="compiler-error-c3141"></a>编译器错误 C3141

interface_name： 接口只支持公共继承

使用定义的接口[接口 （或 __interface）](../../cpp/interface.md)关键字只支持公共继承。

下面的示例生成 C3141:

```
// C3141.cpp
__interface IBase {};
__interface IDerived1 : protected IBase {};  // C3141
__interface IDerived2 : private IBase {};    // C3141
```