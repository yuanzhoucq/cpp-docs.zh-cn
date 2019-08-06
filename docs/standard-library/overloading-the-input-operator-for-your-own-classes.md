---
title: 为自己的类重载 &gt;&gt; 运算符
ms.date: 11/04/2016
helpviewer_keywords:
- operator>>
- operator>>, overloading for your own classes
- operator >>, overloading for your own classes
ms.assetid: 40dab4e0-3f97-4745-9cc8-b86e740fa246
ms.openlocfilehash: 672dfb7ec40b2f18cbde0adc92522d3194a5e738
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68450128"
---
# <a name="overloading-the-gtgt-operator-for-your-own-classes"></a>为自己的类重载 &gt;&gt; 运算符

输出流使用标准类型的提取 (`>>`) 运算符。 你可以为自己的类型编写相似的提取运算符；成功与否取决于对空格的精确使用。

下面是前文中列举的 `Date` 类的一个提取运算符示例：

```cpp
istream& operator>> (istream& is, Date& dt)
{
    is>> dt.mo>> dt.da>> dt.yr;
    return is;
}
```

## <a name="see-also"></a>请参阅

[输入流](../standard-library/input-streams.md)
