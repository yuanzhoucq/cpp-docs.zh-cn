---
title: piecewise_contruct_t 结构
ms.date: 11/04/2016
f1_keywords:
- utility/std::piecewise_contruct_t
helpviewer_keywords:
- piecewise_contruct_t class
- piecewise_contruct_t structure
ms.openlocfilehash: 6a9a6af97ca5c7751d64cd1fa70c9d9eba87da7c
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2019
ms.locfileid: "68268359"
---
# <a name="piecewisecontructt-structure"></a>piecewise_contruct_t 结构

该结构`piecewise_construct_t`是空的结构类型用于保留单独的构造函数和函数重载。 具体而言，`pair`具有与构造函数`piecewise_construct_t`作为第一个参数后, 跟两个`tuple`自变量。

## <a name="syntax"></a>语法

```cpp
struct piecewise_construct_t { explicit piecewise_construct_t() = default; };

inline constexpr piecewise_construct_t piecewise_construct{};
```
