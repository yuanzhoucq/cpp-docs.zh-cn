---
title: C++标准库头文件
ms.date: 07/12/2019
helpviewer_keywords:
- header files, C++ Standard Library
- C++ Standard Library, header files
ms.assetid: e7bf497a-0f63-48d0-9b54-cb0eef4073c4
ms.openlocfilehash: dc337ef078108d86849aa7b7452512dfb69e6e18
ms.sourcegitcommit: 0867d648e0955ebad7260b5fbebfd6cd4d58f3c7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/19/2019
ms.locfileid: "68341121"
---
# <a name="c-standard-library-header-files"></a>C++标准库头文件

C++标准库和扩展的头文件 (按类别)。

## <a name="headers-by-category"></a>按类别列出的标头

::: moniker range=">=vs-2017"

| 类别 | 标头 |
| - | - |
| [算法](../cpp/algorithms-modern-cpp.md) | 算法 > [, b>\<](cstdlib.md), [数值\<>](numeric.md) [ \<](algorithm.md) |
| 原子操作 |  原子 ><sup>11</sup> [ \<](atomic.md) |
| C 库包装 | [ \<](cfenv.md)<sup></sup> [ \<](cerrno.md) [ \<cassert >](cctype.md), [ccomplex > 11 a b, cctype >, cerrno >, cfenv > 11, \<](ccomplex.md) [ \<](cassert.md)<sup></sup> [ \<cfloat >](cfloat.md)、<sup></sup> [ \<cinttypes >](cinttypes.md)11、 [ \<ciso646 >](ciso646.md)<sup>b</sup>、 [ \<climits >](climits.md)、 [ \<clocale >](clocale.md) [ h\<>](cmath.md), [ csetjmp>,csignal>,cstdalign>11ab,cstdarg>\<](csetjmp.md) [ \<](cstdarg.md) [ \<](csignal.md) [ \<](cstdalign.md)<sup></sup> [ \<cstdbool >](cstdbool.md)<sup>11 a b</sup>, [ \<cstddef >](cstddef.md), [ \<cstdint >](cstdint.md)<sup>11</sup>, [ \<cstdio> >](cstdio.md), [ \<b >](cstdlib.md) [ cstring\<>](cstring.md),<sup></sup> [ \<](ctime.md)<sup></sup> [ \<](cuchar.md) [ \<](cwchar.md) [ ctgmath>11\<](ctgmath.md)a b, ctime >, cuchar > 11, cwchar > [ cwctype\<>](cwctype.md) |
| 概念 | \<概念 ><sup>20</sup> |
| [容器](../cpp/containers-modern-cpp.md) | |
| 序列容器 | <sup></sup><sup></sup> [数组\<>](array.md)11、 [ deque>、forward_list>11、list>、vector>\<](deque.md) [ \<](forward-list.md) [ \<](list.md) [ \<](vector.md) |
| 排序关联容器| [\<map>](map.md), [\<set>](set.md) |
| 无序关联容器 | unordered_map ><sup>11</sup>, [ unordered_set>\<](unordered-set.md)<sup>11</sup> [ \<](unordered-map.md) |
| 容器适配器 | [\<queue>](queue.md), [\<stack>](stack.md) |
| 容器视图 | \<跨越 ><sup>20</sup> |
| [错误和异常处理](../cpp/errors-and-exception-handling-modern-cpp.md) | <sup></sup> [ cassert\<>](cassert.md) [, exception\<>](exception.md) [, stdexcept>\<>](stdexcept.md) [, system_error\<>](system-error.md)11 |
| 常规实用工具 | \<任何 ><sup>17</sup>、 [ \<位组 >](bitset.md)、 \<charconv ><sup>17</sup>、 [ \<b >](cstdlib.md)、 \<执行 ><sup>17</sup>、 [ \<功能 >](functional.md) [内存\<>](memory.md),<sup></sup> \<<sup></sup><sup></sup> [ \<](ratio.md)memory_resource > 17, 可选 > 17, 比率 > 11, scoped_allocator > \< [ \<](scoped-allocator.md) <sup>11</sup>、<sup></sup><sup></sup><sup></sup> [ \<](type-traits.md) [ \<](utility.md) [元\<组 >](tuple.md)11、type_traits > [ 11\<、typeindex> >](typeindex.md)11、实用工具 >、变体 ><sup>17</sup> \< |
| [I/o 和格式设置](../cpp/string-and-i-o-formatting-modern-cpp.md) | <sup></sup><sup></sup> [ cinttypes\<>](cinttypes.md)11, [ cstdio>>,filesystem>17,m>,iomanip>\<](cstdio.md) [ \<](filesystem.md) [ \<](fstream.md) [ \<](iomanip.md) [ ios\<>](ios.md)、 [ iosfwd>、iostream>、istream>、ostream>、m>\<](iosfwd.md) [ \<](iostream.md) [ \<](istream.md) [ \<](ostream.md) [ \<](sstream.md)\< [ ,\<streambuf >](streambuf.md) [ ,\<strstream >](strstream.md)<sup>c</sup>, syncstream ><sup>20</sup> |
| Iterators | [\<iterator>](iterator.md) |
| 语言支持 | \< \< \< <sup></sup><sup></sup><sup></sup> [ cfloat\<>](cfloat.md) [, climits\<>](climits.md) [, codecvt\<>](codecvt.md)11 a, 比较 > 20, 协定 > 20,协同程序 ><sup>20</sup>, [ \<csetjmp >](csetjmp.md), [ \<csignal >](csignal.md), [ \<cstdarg >](cstdarg.md), [ \<cstddef >](cstddef.md), [ \<cstdint >](cstdint.md) <sup>11</sup><sup></sup> [, b\<>](cstdlib.md) [, exception\<>](exception.md) [, initializer_list\<>](initializer-list.md)11 [,限制>\<](limits.md) [ \<新 >](new.md), [ \<typeinfo >](typeinfo.md), \<版本 ><sup>20</sup> |
| 本地化 | [ \<](locale.md) <sup></sup> [ clocale>\<](cvt-wbuffer.md), [codecvt > 11 a, cvt/wbuffer >, cvt/wstring >, locale > \<](codecvt.md) [ \<](cvt-wstring.md) [ \<](clocale.md) |
| 数学和数字 | \<位 ><sup>20</sup>, [ \<cfenv >](cfenv.md)<sup>11</sup>, [ \<h >](cmath.md), [ \<复杂 >](complex.md), [ \<b >](cstdlib.md), [ \<限制 >](limits.md) [ 数值\<>](numeric.md),<sup></sup><sup></sup> [随机\<>](random.md)11 [,比率>11,valarray>\<](ratio.md) [ \<](valarray.md) |
| [内存管理](../cpp/smart-pointers-modern-cpp.md) | <sup></sup><sup></sup> [分配器>\<](new.md), \< [ \<](scoped-allocator.md) [内存\<>](memory.md), memory_resource > 17, new >, scoped_allocator > 11 [ \<](allocators-header.md) |
| 多线程 | <sup></sup><sup></sup><sup></sup><sup></sup> [原子\<>](atomic.md)11、 [ condition_variable>11、未来>11、mutex>11、\<](condition-variable.md) [ \<](future.md) [ \<](mutex.md) [ \<shared_mutex >](shared-mutex.md)<sup>14</sup>, [ \<线程 >](thread.md)<sup>11</sup> |
| 范围 | \<范围 ><sup>20</sup> |
| 正则表达式 | regex ><sup>11</sup> [ \<](regex.md) |
| 字符串和字符数据 | <sup></sup> [ cctype\<>](cctype.md), [ b>,cstring>,cuchar>11,cwchar>,cwctype\<](cstdlib.md) [ \<](cstring.md) [ \<](cuchar.md) [ \<](cwchar.md) [ \<>](cwctype.md) [ ,\<regex >](regex.md)<sup>11</sup>, [ \<string >](string.md), [ \<string_view >](string-view.md)<sup>17</sup> |
| 时间 | chrono ><sup>11</sup>, [ ctime\<>](ctime.md) [ \<](chrono.md) |

<sup>11</sup> c + + 11 标准版中添加了11。
c + + 14 标准版中添加了<sup>14</sup>个。
<sup>17</sup> (c + + 17 标准版)。
标准版 c + + 20 标准版中添加了<sup>20</sup> 。 \
c + + 17 标准版中<sup>的</sup>弃用。
<sup>b</sup>在标准版 c + + 20 标准版中删除。
<sup>c</sup> + + 98 标准版中已弃用。

::: moniker-end

::: moniker range="vs-2015"

|类别|标头|
|-|-|
|[算法](../cpp/algorithms-modern-cpp.md)|[\<algorithm>](algorithm.md)|
|C 库包装|[\<cassert>](cassert.md), [\<cctype>](cctype.md), [\<cerrno>](cerrno.md), [\<cfenv>](cfenv.md), [\<cfloat>](cfloat.md), [\<cinttypes>](cinttypes.md), [\<ciso646>](ciso646.md), [\<climits>](climits.md), [\<clocale>](clocale.md), [\<cmath>](cmath.md), [\<csetjmp>](csetjmp.md), [\<csignal>](csignal.md), [\<cstdarg>](cstdarg.md), [\<cstdbool>](cstdbool.md), [\<cstddef>](cstddef.md), [\<cstdint>](cstdint.md), [\<cstdio>](cstdio.md), [\<cstdlib>](cstdlib.md), [\<cstring>](cstring.md), [\<ctgmath>](ctgmath.md), [\<ctime>](ctime.md), [\<cwchar>](cwchar.md), [\<cwctype>](cwctype.md)|
|[容器](../cpp/containers-modern-cpp.md)||
|序列容器|[数组\<>](array.md)、 [ deque>、forward_list>、list>、vector>\<](deque.md) [ \<](forward-list.md) [ \<](list.md) [ \<](vector.md)|
|排序关联容器| [\<map>](map.md), [\<set>](set.md)|
|无序关联容器|unordered_map >, [ \<](unordered-map.md) [ unordered_set>\<](unordered-set.md)|
|适配器容器|[\<queue>](queue.md), [\<stack>](stack.md)|
|[错误和异常处理](../cpp/errors-and-exception-handling-modern-cpp.md)|exception > [、 stdexcept>>\<](stdexcept.md)、 [ system_error\<>](system-error.md) [ \<](exception.md)|
|[I/o 和格式设置](../cpp/string-and-i-o-formatting-modern-cpp.md)|[\<filesystem>](filesystem.md), [\<fstream>](fstream.md), [\<iomanip>](iomanip.md), [\<ios>](ios.md), [\<iosfwd>](iosfwd.md), [\<iostream>](iostream.md), [\<istream>](istream.md), [\<ostream>](ostream.md), [\<sstream>](sstream.md), [\<streambuf>](streambuf.md), [\<strstream>](strstream.md)|
|Iterators|[\<iterator>](iterator.md)|
|本地化|[\<codecvt>](codecvt.md), [\<cvt/wbuffer>](cvt-wbuffer.md), [\<cvt/wstring>](cvt-wstring.md), [\<locale>](locale.md)|
|数学和数字|[\<complex>](complex.md), [\<limits>](limits.md), [\<numeric>](numeric.md), [\<random>](random.md), [\<ratio>](ratio.md), [\<valarray>](valarray.md)|
|[内存管理](../cpp/smart-pointers-modern-cpp.md)|分配器 > [、内存\<>](memory.md)、 [ new\<>](new.md)、 [ scoped_allocator\<>](scoped-allocator.md) [ \<](allocators-header.md)|
|多线程|[原子\<>](atomic.md), [ condition_variable>,未来>,互斥>,shared_mutex>,线程\<](condition-variable.md) [ \<](future.md) [ \<](mutex.md) [ \<](shared-mutex.md) [ \<>](thread.md)|
|其他实用工具|[位组\<>](bitset.md), [ chrono>,功能性>,initializer_list>,元组>,type_traits\<](chrono.md) [ \<](functional.md) [ \<](initializer-list.md) [ \<](tuple.md) [ \<>](type-traits.md) [ ,\<typeinfo >](typeinfo.md), [ \<typeindex> >](typeindex.md), [ \<实用工具 >](utility.md)|
|字符串和字符数据|[\<regex>](regex.md), [\<string>](string.md), [\<string_view>](string-view.md)

::: moniker-end

## <a name="see-also"></a>请参阅

[使用C++库标头](using-cpp-library-headers.md)\
[C++标准库](cpp-standard-library-reference.md)
