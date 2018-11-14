---
title: '&lt;iterator&gt; 函数'
ms.date: 11/04/2016
f1_keywords:
- xutility/std::advance
- xutility/std::back_inserter
- xutility/std::begin
- xutility/std::cbegin
- xutility/std::cend
- xutility/std::distance
- xutility/std::end
- xutility/std::front_inserter
- xutility/std::inserter
- xutility/std::make_checked_array_iterator
- xutility/std::make_move_iterator
- xutility/std::make_unchecked_array_iterator
- xutility/std::next
- xutility/std::prev
ms.assetid: 4a57c9a3-7e36-411f-8655-e0be2eec88e7
helpviewer_keywords:
- std::advance [C++]
- std::back_inserter [C++]
- std::begin [C++]
- std::cbegin [C++]
- std::cend [C++]
- std::distance [C++]
- std::end [C++]
- std::front_inserter [C++]
- std::inserter [C++]
- std::make_checked_array_iterator [C++]
- std::make_move_iterator [C++]
- std::make_unchecked_array_iterator [C++]
- std::next [C++]
- std::prev [C++]
ms.openlocfilehash: f6ea1ac49dabbfc34af9c8ddd020543f606d37a4
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/10/2018
ms.locfileid: "51523671"
---
# <a name="ltiteratorgt-functions"></a>&lt;iterator&gt; 函数

||||
|-|-|-|
|[advance](#advance)|[back_inserter](#back_inserter)|[begin](#begin)|
|[cbegin](#cbegin)|[cend](#cend)|[distance](#distance)|
|[end](#end)|[front_inserter](#front_inserter)|[inserter](#inserter)|
|[make_checked_array_iterator](#make_checked_array_iterator)|[make_move_iterator](#make_move_iterator)|[make_unchecked_array_iterator](#make_unchecked_array_iterator)|
|[next](#next)|[prev](#prev)|

## <a name="advance"></a>advance

使迭代器递增指定数量的位置。

```cpp
template <class InputIterator, class Distance>
void advance(
    InputIterator& InIt,
    Distance Off);
```

### <a name="parameters"></a>参数

*InIt*<br/>
要递增的迭代器，且必须满足输入迭代器的需求。

*Off*<br/>
可转换为迭代器的距离类型的整型值，用于指定要将迭代器位置前移的递增数。

### <a name="remarks"></a>备注

前移范围必须非奇数，这种情况下，迭代器必须可解引用或超过结尾。

如果`InputIterator`满足双向迭代器类型的要求，则*关闭*可以是负数。 如果`InputIterator`是输入或向前迭代器类型，*关闭*必须为非负。

前移函数具有恒定的复杂性时`InputIterator`满足的要求随机访问迭代器; 否则为它具有线性复杂度，因此会可能很重要。

### <a name="example"></a>示例

```cpp
// iterator_advance.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   list<int> L;
   for ( i = 1 ; i < 9 ; ++i )
   {
      L.push_back ( i );
   }
   list <int>::iterator L_Iter, LPOS = L.begin ( );

   cout << "The list L is: ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)
      cout << *L_Iter << " ";
   cout << ")." << endl;

   cout << "The iterator LPOS initially points to the first element: "
        << *LPOS << "." << endl;

   advance ( LPOS , 4 );
   cout << "LPOS is advanced 4 steps forward to point"
        << " to the fifth element: "
        << *LPOS << "." << endl;

   advance ( LPOS , -3 );
   cout << "LPOS is moved 3 steps back to point to the "
        << "2nd element: " << *LPOS << "." << endl;
}
```

```Output
The list L is: ( 1 2 3 4 5 6 7 8 ).
The iterator LPOS initially points to the first element: 1.
LPOS is advanced 4 steps forward to point to the fifth element: 5.
LPOS is moved 3 steps back to point to the 2nd element: 2.
```

## <a name="back_inserter"></a>back_inserter

创建一个可以在指定容器的后面插入元素的迭代器。

```cpp
template <class Container>
back_insert_iterator<Container> back_inserter(Container& _Cont);
```

### <a name="parameters"></a>参数

*_Cont*<br/>
一个容器，将向其执行后插入。

### <a name="return-value"></a>返回值

一个`back_insert_iterator`与容器对象相关联 *_Cont*。

### <a name="remarks"></a>备注

C++ 标准库中，此自变量必须引用具有成员函数 `push_back`: [deque 类](../standard-library/deque-class.md)、[list 类](../standard-library/list-class.md) 或 [vector 类](../standard-library/vector-class.md) 的三个序列容器中的一个容器。

### <a name="example"></a>示例

```cpp
// iterator_back_inserter.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for ( i = 0 ; i < 3 ; ++i )
   {
      vec.push_back ( i );
   }

   vector <int>::iterator vIter;
   cout << "The initial vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   // Insertions can be done with template function
   back_insert_iterator<vector<int> > backiter ( vec );
*backiter = 30;
   backiter++;
*backiter = 40;

   // Alternatively, insertions can be done with the
   // back_insert_iterator member function
   back_inserter ( vec ) = 500;
   back_inserter ( vec ) = 600;

   cout << "After the insertions, the vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;
}
```

```Output
The initial vector vec is: ( 0 1 2 ).
After the insertions, the vector vec is: ( 0 1 2 30 40 500 600 ).
```

## <a name="begin"></a>begin

检索一个指向指定容器中第一个元素的迭代器。

```cpp
template <class Container>
auto begin(Container& cont)  `
   -> decltype(cont.begin());

template <class Container>
auto begin(const Container& cont)   `
   -> decltype(cont.begin());

template <class Ty, class Size>
Ty *begin(Ty (& array)[Size]);
```

### <a name="parameters"></a>参数

*cont*<br/>
容器。

*array*<br/>
`Ty` 类型对象的数组。

### <a name="return-value"></a>返回值

前两个模板函数返回 `cont.begin()`。 第一个函数为非常量；第二个函数为常量。

第三个模板函数返回*数组*。

### <a name="example"></a>示例

当需要多个泛型行为时，我们建议使用此模板函数来代替容器成员 `begin()`。

```cpp
// cl.exe /EHsc /nologo /W4 /MTd
#include <algorithm>
#include <functional>
#include <iostream>
#include <iterator>
#include <vector>

template <typename C> void reverse_sort(C& c) {
    using std::begin;
    using std::end;

    std::sort(begin(c), end(c), std::greater<>());
}

template <typename C> void print(const C& c) {
    for (const auto& e : c) {
        std::cout << e << " ";
    }

    std::cout << "\n";
}

int main() {
    std::vector<int> v = { 11, 34, 17, 52, 26, 13, 40, 20, 10, 5, 16, 8, 4, 2, 1 };

    print(v);
    reverse_sort(v);
    print(v);

    std::cout << "--\n";

    int arr[] = { 23, 70, 35, 106, 53, 160, 80, 40, 20, 10, 5, 16, 8, 4, 2, 1 };

    print(arr);
    reverse_sort(arr);
    print(arr);
}
```

```Output
11 34 17 52 26 13 40 20 10 5 16 8 4 2 1
52 40 34 26 20 17 16 13 11 10 8 5 4 2 1
--
23 70 35 106 53 160 80 40 20 10 5 16 8 4 2 1
160 106 80 70 53 40 35 23 20 16 10 8 5 4 2 1
```

除常规数组外，函数 `reverse_sort` 支持任何类型的容器，因为它调用 `begin()` 的非成员版本。 如果将 `reverse_sort` 编码为使用容器成员 `begin()`：

```cpp
template <typename C>
void reverse_sort(C& c) {
    using std::begin;
    using std::end;

    std::sort(c.begin(), c.end(), std::greater<>());

}
```

则向其发送数组时将会导致下列编译器错误：

```Output
error C2228: left of '.begin' must have class/struct/union
```

## <a name="cbegin"></a>cbegin

检索指向指定容器中第一个元素的常量迭代器。

```cpp
template <class Container>
auto cbegin(const Container& cont)
   -> decltype(cont.begin());
```

### <a name="parameters"></a>参数

*cont*<br/>
容器或 initializer_list。

### <a name="return-value"></a>返回值

常量 `cont.begin()`。

### <a name="remarks"></a>备注

此函数适用于 [initializer_list](../standard-library/initializer-list-class.md) 和所有 C++ 标准库容器。

可以使用此成员函数替代 `begin()` 模板函数，以保证返回值为 `const_iterator`。 它一般与 [auto](../cpp/auto-cpp.md) 类型推导关键字联合使用，如下例所示。 在示例中，请考虑`Container`的可修改 (非**const**) 容器或`initializer_list`的任何类型的支持`begin()`和`cbegin()`。

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="cend"></a>cend

检索指向指定容器中最后元素之后的元素的常量迭代器。

```cpp
template <class Container>
auto cend(const Container& cont)
   -> decltype(cont.end());
```

### <a name="parameters"></a>参数

*cont*<br/>
容器或 initializer_list。

### <a name="return-value"></a>返回值

常量 `cont.end()`。

### <a name="remarks"></a>备注

此函数适用于 [initializer_list](../standard-library/initializer-list-class.md) 和所有 C++ 标准库容器。

可以使用此成员函数替代 [end()](../standard-library/iterator-functions.md#end) 模板函数，以保证返回值为 `const_iterator`。 它一般与 [auto](../cpp/auto-cpp.md) 类型推导关键字联合使用，如下例所示。 在示例中，请考虑`Container`的可修改 (非**const**) 容器或`initializer_list`的任何类型的支持`end()`和`cend()`。

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

## <a name="distance"></a>distance

确定两个迭代器定址位置之间的增量数。

```cpp
template <class InputIterator>
typename iterator_traits<InputIterator>::difference_type distance(InputIterator first, InputIterator last);
```

### <a name="parameters"></a>参数

*first*<br/>
第一个迭代器，将要确定其与第二个迭代器之间的距离。

*最后一个*<br/>
第二个迭代器，将要确定其与第一个迭代器之间的距离。

### <a name="return-value"></a>返回值

数乘以*第一个*必须递增到等于*最后一个*。

### <a name="remarks"></a>备注

Distance 函数具有恒定的复杂性时`InputIterator`满足的要求随机访问迭代器; 否则为它具有线性复杂度，因此会可能很昂贵。

### <a name="example"></a>示例

```cpp
// iterator_distance.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   list<int> L;
   for ( i = -1 ; i < 9 ; ++i )
   {
      L.push_back ( 2 * i );
   }
   list <int>::iterator L_Iter, LPOS = L.begin ( );

   cout << "The list L is: ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++ )
      cout << *L_Iter << " ";
   cout << ")." << endl;

   cout << "The iterator LPOS initially points to the first element: "
        << *LPOS << "." << endl;

   advance ( LPOS , 7 );
   cout << "LPOS is advanced 7 steps forward to point "
        << " to the eighth element: "
        << *LPOS << "." << endl;

   list<int>::difference_type Ldiff ;
   Ldiff = distance ( L.begin ( ) , LPOS );
   cout << "The distance from L.begin( ) to LPOS is: "
        << Ldiff << "." << endl;
}
```

```Output
The list L is: ( -2 0 2 4 6 8 10 12 14 16 ).
The iterator LPOS initially points to the first element: -2.
LPOS is advanced 7 steps forward to point  to the eighth element: 12.
The distance from L.begin( ) to LPOS is: 7.
```

## <a name="end"></a>end

检索指向指定容器中最后一个元素之后的元素的迭代器。

```cpp
template <class Container>
auto end(Container& cont)
   -> decltype(cont.end());

template <class Container>
auto end(const Container& cont)
   -> decltype(cont.end());

template <class Ty, class Size>
Ty *end(Ty (& array)[Size]);
```

### <a name="parameters"></a>参数

*cont*<br/>
容器。

*array*<br/>
`Ty` 类型对象的数组。

### <a name="return-value"></a>返回值

前两个模板函数返回 `cont.end()`（第一个为非常量函数，第二个为常量函数）。

第三个模板函数返回 `array + Size`。

### <a name="remarks"></a>备注

有关代码示例，请参阅 [begin](../standard-library/iterator-functions.md#begin)。

## <a name="front_inserter"></a>front_inserter

创建一个可以在指定容器前面插入元素的迭代器。

```cpp
template <class Container>
front_insert_iterator<Container> front_inserter(Container& _Cont);
```

### <a name="parameters"></a>参数

*_Cont*<br/>
其前部要插入元素的容器对象。

### <a name="return-value"></a>返回值

一个`front_insert_iterator`与容器对象相关联 *_Cont*。

### <a name="remarks"></a>备注

也可使用 front_insert_iterator 类的成员函数 [front_insert_iterator](../standard-library/front-insert-iterator-class.md#front_insert_iterator)。

C++ 标准库中，此自变量必须引用具有成员函数 `push_back`: [deque 类](../standard-library/deque-class.md)或“列表类”的两个序列容器中的一个容器。

### <a name="example"></a>示例

```cpp
// iterator_front_inserter.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   int i;
   list <int>::iterator L_Iter;

   list<int> L;
   for ( i = -1 ; i < 9 ; ++i )
   {
      L.push_back ( i );
   }

   cout << "The list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)
      cout << *L_Iter << " ";
   cout << ")." << endl;

   // Using the template function to insert an element
   front_insert_iterator< list < int> > Iter(L);
*Iter = 100;

   // Alternatively, you may use the front_insert member function
   front_inserter ( L ) = 200;

   cout << "After the front insertions, the list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)
      cout << *L_Iter << " ";
   cout << ")." << endl;
}
```

```Output
The list L is:
( -1 0 1 2 3 4 5 6 7 8 ).
After the front insertions, the list L is:
( 200 100 -1 0 1 2 3 4 5 6 7 8 ).
```

## <a name="inserter"></a>inserter

使您可以使用一个帮助程序模板函数`inserter(_Cont, _Where)`而不是`insert_iterator<Container>(_Cont, _Where)`。

```cpp
template <class Container>
insert_iterator<Container>
inserter(
    Container& _Cont,
    typename Container::iterator _Where);
```

### <a name="parameters"></a>参数

*_Cont*<br/>
要向其添加新元素的容器。

*_Where*<br/>
定位插入点的迭代器。

### <a name="remarks"></a>备注

模板函数返回[insert_iterator](../standard-library/insert-iterator-class.md#insert_iterator)`<Container>(_Cont, _Where)`。

### <a name="example"></a>示例

```cpp
// iterator_inserter.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   int i;
   list <int>::iterator L_Iter;

   list<int> L;
   for (i = 2 ; i < 5 ; ++i )
   {
      L.push_back ( 10 * i );
   }

   cout << "The list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++ )
      cout << *L_Iter << " ";
   cout << ")." << endl;

   // Using the template version to insert an element
   insert_iterator<list <int> > Iter( L, L.begin ( ) );
*Iter = 1;

   // Alternatively, using the member function to insert an element
   inserter ( L, L.end ( ) ) = 500;

   cout << "After the insertions, the list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)
      cout << *L_Iter << " ";
   cout << ")." << endl;
}
```

```Output
The list L is:
( 20 30 40 ).
After the insertions, the list L is:
( 1 20 30 40 500 ).
```

## <a name="make_checked_array_iterator"></a>make_checked_array_iterator

创建可由其他算法使用的 [checked_array_iterator](../standard-library/checked-array-iterator-class.md)。

> [!NOTE]
> 该函数是 C++ 标准库的 Microsoft 扩展。 使用该函数实现的代码不可移植到不支持该 Microsoft 扩展的 C++ 标准生成环境中。

```cpp
template <class Iter>
checked_array_iterator<Iter>
    make_checked_array_iterator(
Iter Ptr,
    size_t Size,
    size_t Index = 0);
```

### <a name="parameters"></a>参数

*ptr*<br/>
指向目标数组的指针。

*Size*<br/>
目标数组的大小。

*Tuple*<br/>
数组的可选索引。

### <a name="return-value"></a>返回值

`checked_array_iterator` 的一个实例。

### <a name="remarks"></a>备注

`make_checked_array_iterator` 函数在 `stdext` 命名空间中定义。

此函数采用原始指针（此指针通常会导致有关边界溢出的问题），并将其包装在执行检查的 [checked_array_iterator](../standard-library/checked-array-iterator-class.md) 类中。 由于此类标记为已检查，因此 C++ 标准库不会对此发出警告。 有关详细信息和代码示例，请参阅[经过检查的迭代器](../standard-library/checked-iterators.md)。

### <a name="example"></a>示例

在下面的示例中，将创建一个 [vector](../standard-library/vector-class.md)，并在其中填充 10 项。 矢量内容通过复制算法复制到数组，随后使用 `make_checked_array_iterator` 指定目标。 这在有意违反边界后进行，因此将触发调试断言失败。

```cpp
// make_checked_array_iterator.cpp
// compile with: /EHsc /W4 /MTd

#include <algorithm>
#include <iterator> // stdext::make_checked_array_iterator
#include <memory> // std::make_unique
#include <iostream>
#include <vector>
#include <string>

using namespace std;

template <typename C> void print(const string& s, const C& c) {
    cout << s;

    for (const auto& e : c) {
        cout << e << " ";
    }

    cout << endl;
}

int main()
{
    const size_t dest_size = 10;
    // Old-school but not exception safe, favor make_unique<int[]>
    // int* dest = new int[dest_size];
    unique_ptr<int[]> updest = make_unique<int[]>(dest_size);
    int* dest = updest.get(); // get a raw pointer for the demo

    vector<int> v;

    for (int i = 0; i < dest_size; ++i) {
        v.push_back(i);
    }
    print("vector v: ", v);

    copy(v.begin(), v.end(), stdext::make_checked_array_iterator(dest, dest_size));

    cout << "int array dest: ";
    for (int i = 0; i < dest_size; ++i) {
        cout << dest[i] << " ";
    }
    cout << endl;

    // Add another element to the vector to force an overrun.
    v.push_back(10);
    // The next line causes a debug assertion when it executes.
    copy(v.begin(), v.end(), stdext::make_checked_array_iterator(dest, dest_size));
}
```

## <a name="make_move_iterator"></a>make_move_iterator

创建一个将所提供的迭代器包含在内作为 `stored` 迭代器的 `move iterator`。

```cpp
template <class Iterator>
move_iterator<Iterator>
make_move_iterator(const Iterator& _It);
```

### <a name="parameters"></a>参数

*_It*<br/>
存储在新移动迭代器中的迭代器。

### <a name="remarks"></a>备注

模板函数返回`move_iterator` `<Iterator>(_It)`。

## <a name="make_unchecked_array_iterator"></a>make_unchecked_array_iterator

创建可由其他算法使用的 [unchecked_array_iterator](../standard-library/unchecked-array-iterator-class.md)。

> [!NOTE]
> 该函数是 C++ 标准库的 Microsoft 扩展。 使用该函数实现的代码不可移植到不支持该 Microsoft 扩展的 C++ 标准生成环境中。

```cpp
template <class Iter>
unchecked_array_iterator<Iter>
    make_unchecked_array_iterator(Iter Ptr);
```

### <a name="parameters"></a>参数

*ptr*<br/>
指向目标数组的指针。

### <a name="return-value"></a>返回值

`unchecked_array_iterator` 的一个实例。

### <a name="remarks"></a>备注

`make_unchecked_array_iterator` 函数在 `stdext` 命名空间中定义。

该函数采用原始指针并将其包装在不执行检查的类中，因此没有进行任何优化，但它还静默处理编译器警告，例如 [C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)。 因此，这是一个有针对性的方法，既可处理未经检查的指针警告，又无需从全局静默处理这些警告或产生检查成本。 有关详细信息和代码示例，请参阅[经过检查的迭代器](../standard-library/checked-iterators.md)。

### <a name="example"></a>示例

在下面的示例中，将创建一个 [vector](../standard-library/vector-class.md)，并在其中填充 10 项。 矢量内容通过复制算法复制到数组，随后使用 `make_unchecked_array_iterator` 指定目标。

```cpp
// make_unchecked_array_iterator.cpp
// compile with: /EHsc /W4 /MTd

#include <algorithm>
#include <iterator> // stdext::make_unchecked_array_iterator
#include <iostream>
#include <vector>
#include <string>

using namespace std;

template <typename C> void print(const string& s, const C& c) {
    cout << s;

    for (const auto& e : c) {
        cout << e << " ";
    }

    cout << endl;
}

int main()
{
    const size_t dest_size = 10;
    int *dest = new int[dest_size];
    vector<int> v;

    for (int i = 0; i < dest_size; ++i) {
        v.push_back(i);
    }
    print("vector v: ", v);

    // COMPILER WARNING SILENCED: stdext::unchecked_array_iterator is marked as checked in debug mode
    // (it performs no checking, so an overrun will trigger undefined behavior)
    copy(v.begin(), v.end(), stdext::make_unchecked_array_iterator(dest));

    cout << "int array dest: ";
    for (int i = 0; i < dest_size; ++i) {
        cout << dest[i] << " ";
    }
    cout << endl;

    delete[] dest;
}
```

## <a name="next"></a>next

迭代指定的次数并返回新的迭代器位置。

```cpp
template <class InputIterator>
InputIterator next(
    InputIterator first,
    typename iterator_traits<InputIterator>::difference_type _Off = 1);
```

### <a name="parameters"></a>参数

*first*<br/>
当前位置。

*_Off*<br/>
循环访问次数。

### <a name="return-value"></a>返回值

循环访问之后，返回新的迭代器位置 *_Off*时间。

### <a name="remarks"></a>备注

模板函数返回`next`递增 *_Off*时间

## <a name="prev"></a>prev

反向迭代指定的次数并返回新的迭代器位置。

```cpp
template <class BidirectionalIterator>
BidirectionalIterator prev(
    BidirectionalIterator first,
    typename iterator_traits<BidirectionalIterator>::difference_type _Off = 1);
```

### <a name="parameters"></a>参数

*first*<br/>
当前位置。

*_Off*<br/>
循环访问次数。

### <a name="remarks"></a>备注

模板函数返回 `next` 递减 `off` 次数。

## <a name="see-also"></a>请参阅

[\<iterator>](../standard-library/iterator.md)<br/>
