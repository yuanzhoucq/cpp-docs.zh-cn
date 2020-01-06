---
title: C++标准库头文件
ms.date: 07/12/2019
helpviewer_keywords:
- header files, C++ Standard Library
- C++ Standard Library, header files
ms.assetid: e7bf497a-0f63-48d0-9b54-cb0eef4073c4
ms.openlocfilehash: 807e65c69e55d8790b77a493e4ae1878aa740557
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/21/2019
ms.locfileid: "74305414"
---
# <a name="c-standard-library-header-files"></a>C++标准库头文件

C++标准库和扩展的头文件（按类别）。

## <a name="headers-by-category"></a>按类别列出的标头

::: moniker range=">=vs-2017"

| 类别 | 标头 |
| - | - |
| [算法](../cpp/algorithms-modern-cpp.md) | [\<算法 >](algorithm.md)， [\<b >](cstdlib.md)， [\<数值 >](numeric.md) |
| 原子操作 |  [\<原子 >](atomic.md)<sup>11</sup> |
| C 库包装 | [\<cassert>](cassert.md), [\<ccomplex>](ccomplex.md)<sup>11 a b</sup>, [\<cctype>](cctype.md), [\<cerrno>](cerrno.md), [\<cfenv>](cfenv.md)<sup>11</sup>, [\<cfloat>](cfloat.md), [\<cinttypes>](cinttypes.md)<sup>11</sup>, [\<ciso646>](ciso646.md)<sup>b</sup>, [\<climits>](climits.md), [\<clocale>](clocale.md), [\<cmath>](cmath.md), [\<csetjmp>](csetjmp.md), [\<csignal>](csignal.md), [\<cstdalign>](cstdalign.md)<sup>11 a b</sup>, [\<cstdarg>](cstdarg.md), [\<cstdbool>](cstdbool.md)<sup>11 a b</sup>, [\<cstddef>](cstddef.md), [\<cstdint>](cstdint.md)<sup>11</sup>, [\<cstdio>](cstdio.md), [\<cstdlib>](cstdlib.md), [\<cstring>](cstring.md), [\<ctgmath>](ctgmath.md)<sup>11 a b</sup>, [\<ctime>](ctime.md), [\<cuchar>](cuchar.md)<sup>11</sup>, [\<cwchar>](cwchar.md), [\<cwctype>](cwctype.md) |
| 概念 | \<概念 ><sup>20</sup> |
| [容器](../cpp/containers-modern-cpp.md) | |
| 序列容器 | [\<数组 >](array.md)<sup>11</sup>， [\<deque >](deque.md)， [\<forward_list](forward-list.md)><sup>11</sup>\<[>\<](list.md) [>](vector.md) |
| 排序关联容器| [\<map>](map.md), [\<set>](set.md) |
| 无序关联容器 | [\<unordered_map >](unordered-map.md)<sup>11</sup>， [\<unordered_set](unordered-set.md)><sup>11</sup> |
| 容器适配器 | [\<queue>](queue.md), [\<stack>](stack.md) |
| 容器视图 | \<span ><sup>20</sup> |
| [错误和异常处理](../cpp/errors-and-exception-handling-modern-cpp.md) | [\<cassert >](cassert.md)， [\<exception >](exception.md)， [\<stdexcept> >](stdexcept.md)， [\<system_error](system-error.md)><sup>11</sup> |
| 常规实用工具 | \<any><sup>17</sup>, [\<bitset>](bitset.md), \<charconv><sup>17</sup>, [\<cstdlib>](cstdlib.md), \<execution><sup>17</sup>, [\<functional>](functional.md), [\<memory>](memory.md), \<memory_resource><sup>17</sup>, \<optional><sup>17</sup>, [\<ratio>](ratio.md)<sup>11</sup>, [\<scoped_allocator>](scoped-allocator.md)<sup>11</sup>, [\<tuple>](tuple.md)<sup>11</sup>, [\<type_traits>](type-traits.md)<sup>11</sup>, [\<typeindex>](typeindex.md)<sup>11</sup>, [\<utility>](utility.md), \<variant><sup>17</sup> |
| [I/o 和格式设置](../text/string-and-i-o-formatting-modern-cpp.md) | [\<cinttypes>](cinttypes.md)<sup>11</sup>, [\<cstdio>](cstdio.md), [\<filesystem>](filesystem.md)<sup>17</sup>, [\<fstream>](fstream.md), [\<iomanip>](iomanip.md), [\<ios>](ios.md), [\<iosfwd>](iosfwd.md), [\<iostream>](iostream.md), [\<istream>](istream.md), [\<ostream>](ostream.md), [\<sstream>](sstream.md), [\<streambuf>](streambuf.md), [\<strstream>](strstream.md)<sup>c</sup>, \<syncstream><sup>20</sup> |
| 迭代器 | [\<iterator>](iterator.md) |
| 语言支持 | [\<cfloat >](cfloat.md)， [\<climits >](climits.md)， [\<codecvt >](codecvt.md)<sup>11 a</sup>，\<比较 ><sup>20</sup>，\<协定 ><sup>20</sup>，\<协同程序 ><sup>20</sup>， [\<csetjmp >](csetjmp.md)， [\<csignal >](csignal.md)， [\<cstdarg >](cstdarg.md)， [\<cstddef >，](cstddef.md)\<[cstdint >](cstdint.md)<sup>\<</sup>> [b](cstdlib.md)\<> 的[异常](exception.md)， [\<initializer_list >](initializer-list.md)<sup>11</sup>， [\<限制 >](limits.md)\<[>\<](new.md) [> \<](typeinfo.md)><sup></sup> |
| 本地化 | [\<clocale >](clocale.md)， [\<codecvt >](codecvt.md)<sup>11 a</sup>， [\<cvt/wbuffer >](cvt-wbuffer.md)\<[cvt/wstring >](cvt-wstring.md)\<[区域设置 >](locale.md) |
| 数学和数字 | \<bit><sup>20</sup>, [\<cfenv>](cfenv.md)<sup>11</sup>, [\<cmath>](cmath.md), [\<complex>](complex.md), [\<cstdlib>](cstdlib.md), [\<limits>](limits.md), [\<numeric>](numeric.md), [\<random>](random.md)<sup>11</sup>, [\<ratio>](ratio.md)<sup>11</sup>, [\<valarray>](valarray.md) |
| [内存管理](../cpp/smart-pointers-modern-cpp.md) | [\<分配器 >](allocators-header.md)， [\<内存 >](memory.md)，\<memory_resource ><sup>17</sup>\<[new >](new.md) [\<scoped_allocator >](scoped-allocator.md)<sup>11</sup> |
| 多线程处理 | [\<原子 >](atomic.md)<sup>11</sup>、 [\<condition_variable >](condition-variable.md)<sup>11</sup>、 [\<未来 >](future.md)<sup>11</sup>、 [\<互斥 >](mutex.md)<sup>11</sup>、 [\<shared_mutex](shared-mutex.md)><sup>14</sup>\<[线程 >](thread.md)<sup>11</sup> |
| 范围 | \<范围 ><sup>20</sup> |
| 正则表达式 | [\<regex >](regex.md)<sup>11</sup> |
| 字符串和字符数据 | [\<cctype >](cctype.md)， [\<b >](cstdlib.md)， [\<cstring >](cstring.md)， [\<cuchar >](cuchar.md)<sup>11</sup>， [\<cwchar >](cwchar.md)， [\<cwctype >](cwctype.md)， [\<regex >](regex.md)<sup>11</sup>\<[string >](string.md)\<[string_view >](string-view.md)<sup>17</sup> |
| 时间 | [\<chrono >](chrono.md)<sup>11</sup>， [\<ctime >](ctime.md) |

<sup>11</sup> c + + 11 标准版中添加了11。
c + + 14 标准版中添加了<sup>14</sup>个。
<sup>17</sup> （c + + 17 标准版）。
标准版 c + + 20 标准版中添加了<sup>20</sup> 。 \
c + + 17 标准版中<sup>的</sup>弃用。
<sup>b</sup>在标准版 c + + 20 标准版中删除。
<sup>c</sup> + + 98 标准版中已弃用。

::: moniker-end

::: moniker range="vs-2015"

|类别|标头|
|-|-|
|[算法](../cpp/algorithms-modern-cpp.md)|[\<算法>](algorithm.md)|
|C 库包装|[\<cassert>](cassert.md), [\<cctype>](cctype.md), [\<cerrno>](cerrno.md), [\<cfenv>](cfenv.md), [\<cfloat>](cfloat.md), [\<cinttypes>](cinttypes.md), [\<ciso646>](ciso646.md), [\<climits>](climits.md), [\<clocale>](clocale.md), [\<cmath>](cmath.md), [\<csetjmp>](csetjmp.md), [\<csignal>](csignal.md), [\<cstdarg>](cstdarg.md), [\<cstdbool>](cstdbool.md), [\<cstddef>](cstddef.md), [\<cstdint>](cstdint.md), [\<cstdio>](cstdio.md), [\<cstdlib>](cstdlib.md), [\<cstring>](cstring.md), [\<ctgmath>](ctgmath.md), [\<ctime>](ctime.md), [\<cwchar>](cwchar.md), [\<cwctype>](cwctype.md)|
|[容器](../cpp/containers-modern-cpp.md)||
|序列容器|[\<数组 >](array.md)， [\<deque >](deque.md)， [\<forward_list >](forward-list.md)\<[>\<](list.md) [>](vector.md)|
|排序关联容器| [\<map>](map.md), [\<set>](set.md)|
|无序关联容器|[\<unordered_map >](unordered-map.md)， [\<unordered_set](unordered-set.md) >|
|适配器容器|[\<queue>](queue.md), [\<stack>](stack.md)|
|[错误和异常处理](../cpp/errors-and-exception-handling-modern-cpp.md)|[\<异常 >](exception.md)， [\<stdexcept> >](stdexcept.md)， [\<system_error](system-error.md) >|
|[I/o 和格式设置](../text/string-and-i-o-formatting-modern-cpp.md)|[\<filesystem>](filesystem.md), [\<fstream>](fstream.md), [\<iomanip>](iomanip.md), [\<ios>](ios.md), [\<iosfwd>](iosfwd.md), [\<iostream>](iostream.md), [\<istream>](istream.md), [\<ostream>](ostream.md), [\<sstream>](sstream.md), [\<streambuf>](streambuf.md), [\<strstream>](strstream.md)|
|迭代器|[\<iterator>](iterator.md)|
|本地化|[\<codecvt>](codecvt.md), [\<cvt/wbuffer>](cvt-wbuffer.md), [\<cvt/wstring>](cvt-wstring.md), [\<locale>](locale.md)|
|数学和数字|[\<complex>](complex.md), [\<limits>](limits.md), [\<numeric>](numeric.md), [\<random>](random.md), [\<ratio>](ratio.md), [\<valarray>](valarray.md)|
|[内存管理](../cpp/smart-pointers-modern-cpp.md)|[\<分配器 >](allocators-header.md)， [\<内存 >](memory.md)， [\<new >](new.md)\<[scoped_allocator](scoped-allocator.md) >|
|多线程处理|[\<原子 >](atomic.md)， [\<condition_variable >](condition-variable.md)、 [\<未来 >](future.md)、 [\<互斥 >](mutex.md)、 [\<shared_mutex >](shared-mutex.md)、 [\<线程 >](thread.md)|
|其他实用工具|[\<bitset>](bitset.md), [\<chrono>](chrono.md), [\<functional>](functional.md), [\<initializer_list>](initializer-list.md), [\<tuple>](tuple.md), [\<type_traits>](type-traits.md), [\<typeinfo>](typeinfo.md), [\<typeindex>](typeindex.md), [\<utility>](utility.md)|
|字符串和字符数据|[\<regex >](regex.md)， [\<string >](string.md)， [\<string_view](string-view.md) >

::: moniker-end

## <a name="see-also"></a>另请参阅

[使用C++库标头](using-cpp-library-headers.md)\
[C++标准库](cpp-standard-library-reference.md)
