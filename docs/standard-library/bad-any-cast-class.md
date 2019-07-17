---
title: bad_any_cast 类
ms.date: 04/04/2019
f1_keywords:
- any/std::bad_any_cast
- any/std::bad_any_cast::what
helpviewer_keywords:
- any/std::bad_any_cast
- any/std::bad_any_cast::what
ms.openlocfilehash: 5172281d1918a8b4ac33bcf412bf4be82b04ef56
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2019
ms.locfileid: "68268679"
---
# <a name="badanycast-class"></a>bad_any_cast 类

对象引发的故障`any_cast`。

## <a name="syntax"></a>语法

```cpp
class bad_any_cast
```

### <a name="member-functions"></a>成员函数

|||
|-|-|
|[what](#what)|返回的类型。|

## <a name="what"></a> 什么

返回的类型。

```cpp
const char* what() const noexcept override;
```
