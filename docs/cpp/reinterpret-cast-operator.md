---
title: reinterpret_cast 运算符
ms.date: 11/04/2016
f1_keywords:
- reinterpret_cast_cpp
helpviewer_keywords:
- reinterpret_cast keyword [C++]
ms.assetid: eb3283c7-7f88-467e-affd-407d37b46d6c
ms.openlocfilehash: 421a1fdce6834f800cd33a55d75c9dc4f88ffc93
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403420"
---
# <a name="reinterpretcast-operator"></a>reinterpret_cast 运算符

允许将任何指针转换为任何其他指针类型。 也允许将任何整数类型转换为任何指针类型以及反向转换。

## <a name="syntax"></a>语法

```
reinterpret_cast < type-id > ( expression )
```

## <a name="remarks"></a>备注

误用**reinterpret_cast**运算符可能很容易。 除非所需转换本身是低级别的，否则应使用其他强制转换运算符之一。

**Reinterpret_cast**运算符可用于转换如`char*`到`int*`，或`One_class*`到`Unrelated_class*`，哪些是本质上是不安全。

结果**reinterpret_cast**中不能安全地使用强制转换回其原始类型之外的任何内容。 在最好的情况下，其他用途也是不可移植的。

**Reinterpret_cast**运算符无法转换掉**const**，**易失性**，或者 **__unaligned**属性。 请参阅[const_cast 运算符](../cpp/const-cast-operator.md)有关删除这些属性的信息。

**Reinterpret_cast**运算符将 null 指针值转换为目标类型的 null 指针值。

一个实际用途**reinterpret_cast**是在哈希函数中，哪些将值映射到两个不同的方式中的索引的值几乎不结束了相同的索引。

```cpp
#include <iostream>
using namespace std;

// Returns a hash code based on an address
unsigned short Hash( void *p ) {
   unsigned int val = reinterpret_cast<unsigned int>( p );
   return ( unsigned short )( val ^ (val >> 16));
}

using namespace std;
int main() {
   int a[20];
   for ( int i = 0; i < 20; i++ )
      cout << Hash( a + i ) << endl;
}

Output:
64641
64645
64889
64893
64881
64885
64873
64877
64865
64869
64857
64861
64849
64853
64841
64845
64833
64837
64825
64829
```

**Reinterpret_cast**允许要被视为一种整型类型的指针。 结果随后将按位移位并与自身进行“异或”运算以生成唯一的索引（具有唯一性的概率非常高）。 该索引随后被标准 C 样式强制转换截断为函数的返回类型。

## <a name="see-also"></a>请参阅

[强制转换运算符](../cpp/casting-operators.md)<br/>
[关键字](../cpp/keywords-cpp.md)