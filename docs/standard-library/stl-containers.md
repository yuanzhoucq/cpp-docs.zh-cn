---
title: C++ 标准库容器
ms.date: 11/04/2016
helpviewer_keywords:
- C++ Standard Library, class template containers
- containers, C++ Standard Library
ms.assetid: 8e915ca1-19ba-4f0d-93c8-e2c3bfd638eb
ms.openlocfilehash: 01be754dd7b418f64cf495d7563f65b323265df8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376701"
---
# <a name="c-standard-library-containers"></a>C++ 标准库容器

标准库为相关对象的存储集合提供了各种类型安全容器。 容器是类模板。 声明容器变量时，可以指定容器将容纳的元素的类型。 可以使用初始值设定项列表构造容器。 它们具有用于添加和删除元素以及执行其他操作的成员函数。

可使用[迭代器](../standard-library/iterators.md)循环访问容器中的元素以及访问单个元素。 您可以使用迭代器的成员函数、运算符和全局函数显式使用迭代器。 还可以隐式使用它们，例如通过使用范围 for 循环。 所有 C++ 标准库容器的迭代器都有一个通用接口，但是每个容器都会定义自己的专用迭代器。

容器可以分为三个类别：序列容器、关联容器和容器适配器。

## <a name="sequence-containers"></a><a name="sequence_containers"></a>序列容器

序列容器维护你指定的插入元素的顺序。

`vector` 容器的行为类似于数组，但可以根据要求自动增长。 它可以随机访问、连续存储，长度也非常灵活。 基于上述和其他原因，`vector` 是多数应用程序的首选序列容器。 若不确定要使用哪种序列容器，请首先使用矢量！ 有关详细信息，请参阅 [vector 类](../standard-library/vector-class.md)。

`array`容器具有一些优点`vector`，但长度并不灵活。 有关详细信息，请参阅 [array 类](../standard-library/array-class-stl.md)。

`deque`（双端队列）容器支持在容器的起点和终点进行快速插入和删除。 它共享 的随机访问和灵活长度的优点`vector`，但不是连续的。 有关详细信息，请参阅 [deque 类](../standard-library/deque-class.md)。

`list`容器是一个双链接列表，可在容器中的任何位置实现双向访问、快速插入和快速删除，但不能随机访问容器中的元素。 有关详细信息，请参阅 [list 类](../standard-library/list-class.md)。

`forward_list` 容器是单独链表，`list` 的向前访问版本。 有关详细信息，请参阅 [forward_list 类](../standard-library/forward-list-class.md)。

## <a name="associative-containers"></a>关联容器

在关联容器中，按照预定义的顺序插入元素，例如按升序排序。 无序的关联容器也可用。 关联容器可分为两个子集：映射和组集。

`map`，有时称为字典，包含键/值对。 键用于对序列排序，值与该键关联。 例如，`map`可能包含许多键（代表文本中每个独特的单词）和相应的值（代表每个单词在文本中出现的次数）。 `map`的无序版本是 `unordered_map`。 有关详细信息，请参阅 [map 类](../standard-library/map-class.md)和 [unordered_map 类](../standard-library/unordered-map-class.md)。

`set`仅是按升序排列每个元素的容器，值也是键。 `set`的无序版本是 `unordered_set`。 有关详细信息，请参阅 [set 类](../standard-library/set-class.md)和 [unordered_map 类](../standard-library/unordered-set-class.md)。

`map` 和 `set` 都仅允许将键或元素的一个实例插入容器中。 如果需要元素的多个实例，请使用`multimap`或`multiset`。 无序版本是 `unordered_multimap` 和 `unordered_multiset`。 有关详细信息，请参阅 [multimap 类](../standard-library/multimap-class.md)、[unordered_multimap 类](../standard-library/unordered-multimap-class.md)、[multiset 类](../standard-library/multiset-class.md)和 [unordered_multiset 类](../standard-library/unordered-multiset-class.md)。

有序的映射和组集支持双向迭代器，其未排序副本支持向前迭代器。 有关更多信息，请参见 [迭代器](../standard-library/iterators.md)。

### <a name="heterogeneous-lookup-in-associative-containers-c14"></a>关联容器中的异类查找 (C++14)

有序的关联容器（映射、多映射、集和多集）现在支持异构查找，这意味着您不再需要传递与 成员函数（如`find()`和`lower_bound()`） 中的键或元素完全相同的对象类型。 相反，可以传递为定义了重载 `operator<` 以启用对键类型的比较的类型。

当你在声明容器变量时指定 `std::less<>` 或 `std::greater<>`“菱形函子”比较运算符，会选择性加入启用异类查询：

```cpp
std::set<BigObject, std::less<>> myNewSet;
```

如果你使用默认的比较运算符，该容器的行为会与在 C++11 和更早版本中完全一样。

下面的示例演示如何重载`operator<`，使 用户`std::set`只需传入一个可以与每个对象`BigObject::id`的成员进行比较的小字符串，即可执行查找。

```cpp
#include <set>
#include <string>
#include <iostream>
#include <functional>

using namespace std;

class BigObject
{
public:
    string id;
    explicit BigObject(const string& s) : id(s) {}
    bool operator< (const BigObject& other) const
    {
        return this->id < other.id;
    }

    // Other members....
};

inline bool operator<(const string& otherId, const BigObject& obj)
{
    return otherId < obj.id;
}

inline bool operator<(const BigObject& obj, const string& otherId)
{
    return obj.id < otherId;
}

int main()
{
    // Use C++14 brace-init syntax to invoke BigObject(string).
    // The s suffix invokes string ctor. It is a C++14 user-defined
    // literal defined in <string>
    BigObject b1{ "42F"s };
    BigObject b2{ "52F"s };
    BigObject b3{ "62F"s };
    set<BigObject, less<>> myNewSet; // C++14
    myNewSet.insert(b1);
    myNewSet.insert(b2);
    myNewSet.insert(b3);
    auto it = myNewSet.find(string("62F"));
    if (it != myNewSet.end())
        cout << "myNewSet element = " << it->id << endl;
    else
        cout << "element not found " << endl;

    // Keep console open in debug mode:
    cout << endl << "Press Enter to exit.";
    string s;
    getline(cin, s);
    return 0;
}

//Output: myNewSet element = 62F
```

地图、多映射、集和多集中中的以下成员函数已过载，以支持异构查找：

1. find

1. count

1. lower_bound

1. upper_bound

1. equal_range

## <a name="container-adapters"></a>容器适配器

容器适配器是序列容器或关联容器的变体，为了简单明确起见，它对接口进行限制。 容器适配器不支持迭代器。

`queue`容器遵循 FIFO（先进先出）语义。 第一个*推送*（即插入队列中）的元素将第一个*弹出*（即从队列中删除）。 有关详细信息，请参阅 [queue 类](../standard-library/queue-class.md)。

`priority_queue`容器也是如此组织，因此具有最高值的元素始终排在队列的第一位。 有关详细信息，请参阅 [priority_queue 类](../standard-library/priority-queue-class.md)。

`stack`容器遵循 LIFO（后进先出）语义。 堆栈上最后推送的元素将第一个弹出。 有关详细信息，请参阅 [stack 类](../standard-library/stack-class.md)。

由于容器适配器不支持迭代器，因此不能将其与C++标准库算法一起使用。 有关详细信息，请参阅[算法](../standard-library/algorithms.md)。

## <a name="requirements-for-container-elements"></a>容器元素的需求

通常，如果插入 C++ 标准库容器中的元素可复制，那么这些元素可以是任何对象类型。 只要你不调用尝试复制元素的成员函数，仅可移动的元素（例如，那些类似于 `vector<unique_ptr<T>>`、使用 `unique_ptr<>` 创建的元素）会一直工作。

析构函数不允许引发异常。

有序的关联容器（本文之前所述）必须已定义公共比较运算符。 （默认情况下，该运算符是 `operator<`，即使不能与 `operator<` 共同使用的类型也会受支持。）

容器中的某些操作可能还需要公共默认构造函数和公共等效运算符。 例如，未排序的关联容器需要支持相等性和哈希处理。

## <a name="accessing-container-elements"></a>正在访问容器元素

使用迭代器访问容器的元素。 有关更多信息，请参见 [迭代器](../standard-library/iterators.md)。

> [!NOTE]
> 还可以使用[基于范围的 for 循环](../cpp/range-based-for-statement-cpp.md)来循环访问 C++ 标准库集合。

## <a name="comparing-containers"></a>比较容器

所有容器都重载运算符 == 用于比较同一类型的两个具有相同的元素类型的容器。 可以使用 * 将\<矢量字符串>另一个向量\<字符串>，但不能使用它将矢量\<字符串>比较到列表\<字符串>或向量\<字符串>矢量\<字符串>。  在 C++98/03 中，可以使用[std：：等于](algorithm-functions.md#equal)或[std：：：不匹配](algorithm-functions.md#mismatch)来比较不同的容器类型和/或元素类型。 在 C++11 中，您还可以使用[std：：is_permutation](algorithm-functions.md#is_permutation)。 但在所有这些情况下，函数假定容器的长度相同。 如果第二个范围比第一个短，则产生未定义的行为。 如果第二个范围的更长，结果可能仍然不正确，因为第一个范围结束后比较不会继续。

### <a name="comparing-dissimilar-containers-c14"></a>比较不同的容器 (C++14)

在 C++14 及更高版本中，可以使用具有两个完整范围的`std::equal`、或`std::mismatch``std::is_permutation`函数重载之一比较不同的容器和/或不同的元素类型。 这些重载使你能够比较具有不同长度的容器。 这些重载使用户非常不易遭受错误，并进行了优化，当比较不同长度的容器时会在固定时间内返回错误。 因此，我们建议您使用这些重载，除非您有明确的理由不使用，或者您使用的是[std：：list](../standard-library/list-class.md)容器，该容器不受益于双范围优化。

## <a name="see-also"></a>另请参阅

[并行容器](../parallel/concrt/parallel-containers-and-objects.md)\
[\<示例容器>](../standard-library/sample-container.md)\
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
