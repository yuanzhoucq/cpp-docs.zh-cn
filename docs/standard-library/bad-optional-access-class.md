---
title: bad_optional_access 类
ms.date: 11/04/2016
f1_keywords:
- optional/std::bad_optional_access
ms.assetid: 89a3b805-ab60-4858-b772-5855130c11b1
ms.openlocfilehash: f898d1e30dd173339192bdb3b75581d12b62fca7
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2019
ms.locfileid: "68269139"
---
# <a name="badoptionalaccess-class"></a>bad_optional_access 类

定义类型的对象为例外，以将情况汇报尝试访问的值，其中引发`optional`不包含值的对象。

## <a name="syntax"></a>语法

```cpp
class bad_optional_access : public exception
{
    public: bad_optional_access();
};
```
