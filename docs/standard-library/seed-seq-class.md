---
title: seed_seq 类 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- random/std::seed_seq
- random/std::seed_seq::result_type
- random/std::seed_seq::generate
- random/std::seed_seq::size
- random/std::seed_seq::param
dev_langs:
- C++
helpviewer_keywords:
- std::seed_seq [C++]
- std::seed_seq [C++], result_type
- std::seed_seq [C++], generate
- std::seed_seq [C++], size
- std::seed_seq [C++], param
ms.assetid: cba114f7-9ac6-4f2f-b773-9c84805401d6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8e466d8a176d5c4c7fd1e2250373b42ee263a6d4
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="seedseq-class"></a>seed_seq 类

存储可以为随机数引擎提供随机化种子的无符号整数值的矢量。

## <a name="syntax"></a>语法

```cpp
class seed_seq
   {
public:
   // types
   typedef unsigned int result_type;

   // constructors
   seed_seq();
   template <class T>
      seed_seq(initializer_list<T> initlist);
   template <class InputIterator>
      seed_seq(InputIterator begin, InputIterator end);

   // generating functions
   template <class RandomAccessIterator>
      void generate(RandomAccessIterator begin, RandomAccessIterator end);

   // property functions
   size_t size() const;
   template <class OutputIterator>
      void param(OutputIterator dest) const;

   // no copy functions
   seed_seq(const seed_seq&) = delete;
   void operator=(const seed_seq&) = delete;
   };
```

## <a name="types"></a>类型

`typedef unsigned int result_type;` 种子序列的元素的类型。 32 位无符号整数类型。

## <a name="constructors"></a>构造函数

`seed_seq();` 默认构造函数，初始化具有空的内部序列。

`template<class T>` `seed_seq(initializer_list<T> initlist);` 使用`initlist`设置内部序列。
`T` 必须为整型。

`template<class InputIterator>` `seed_seq(InputIterator begin, InputIterator end);` 初始化使用提供的输入迭代器范围中所有元素的内部序列。
`iterator_traits<InputIterator>::value_type` 必须为整型。

## <a name="members"></a>成员

### <a name="generating-functions"></a>生成函数

`template<class RandomAccessIterator> void generate(RandomAccessIterator begin,          RandomAccessIterator end);` 填充使用内部算法所提供序列的元素。 此算法受初始化 `seed_seq` 的内部序列影响。
如果 `begin == end`，则不执行任何操作。

### <a name="property-functions"></a>属性函数

`size_t size() const;` 返回中的元素数`seed_seq`。

`template<class OutputIterator> void param(OutputIterator dest) const;` 将内部序列复制到输出迭代器`dest`。

## <a name="example"></a>示例

以下代码示例练习了三种构造函数，并且从分配到数组时生成的 `seed_seq` 实例中生成输出。 有关将 `seed_seq` 与随机数生成器一起使用的示例，请参阅 [\<random>](../standard-library/random.md)。

```cpp
#include <iostream>
#include <random>
#include <string>
#include <array>

using namespace std;

void test(const seed_seq& sseq) {
    cout << endl << "seed_seq::size(): " << sseq.size() << endl;

    cout << "seed_seq::param(): ";
    ostream_iterator<unsigned int> out(cout, " ");
    sseq.param(out);
    cout << endl;

    cout << "Generating a sequence of 5 elements into an array: " << endl;
    array<unsigned int, 5> seq;
    sseq.generate(seq.begin(), seq.end());
    for (unsigned x : seq) { cout << x << endl; }
}

int main()
{
    seed_seq seed1;
    test(seed1);

    seed_seq seed2 = { 1701, 1729, 1791 };
    test(seed2);

    string sstr = "A B C D"; // seed string
    seed_seq seed3(sstr.begin(), sstr.end());
    test(seed3);
}
```

```Output
seed_seq::size(): 0
seed_seq::param():
Generating a sequence of 5 elements into an array:
505382999
163489202
3932644188
763126080
73937346

seed_seq::size(): 3
seed_seq::param(): 1701 1729 1791
Generating a sequence of 5 elements into an array:
1730669648
1954224479
2809786021
1172893117
2393473414

seed_seq::size(): 7
seed_seq::param(): 65 32 66 32 67 32 68
Generating a sequence of 5 elements into an array:
3139879222
3775111734
1084804564
2485037668
1985355432
```

## <a name="remarks"></a>备注

此类的成员函数不会引发异常。

## <a name="requirements"></a>要求

**标头：**\<random>

**命名空间：** std

## <a name="see-also"></a>请参阅

[\<random>](../standard-library/random.md)<br/>
