---
title: '&lt;iostream&gt;'
ms.date: 09/20/2017
f1_keywords:
- <iostream>
- iostream/std::cerr
- iostream/std::cin
- iostream/std::clog
- iostream/std::cout
- iostream/std::wcerr
- iostream/std::wcin
- iostream/std::wclog
- iostream/std::wcout
helpviewer_keywords:
- iostream header
ms.assetid: de5d39e1-7e77-4b55-bcd1-7c77b41515c8
ms.openlocfilehash: 03afb777dc3926284cf0dc625e94a716ecdf5413
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375345"
---
# <a name="ltiostreamgt"></a>&lt;iostream&gt;

声明控制从标准流读取和写入到标准流的对象。 这通常包括您需要从C++程序进行输入和输出的唯一标头。

## <a name="syntax"></a>语法

```cpp
#include <iostream>
```

> [!NOTE]
> \<iostream>库使用`#include <ios>`、`#include <streambuf>`和`#include <istream>``#include <ostream>`语句。

## <a name="remarks"></a>备注

这些对象分为两组：

- [cin](#cin)cin、cout、cerr 和[clog](#clog)都是面向字节的，执行传统的字节一次传输。 [cout](#cout) [cerr](#cerr)

- [wcin](#wcin)、[wcout](#wcout)、[wcerr](#wcerr) 和 [wclog](#wclog) 面向宽字节，与程序内部操作的宽字符相互转换。

对流执行某些操作（如标准输入）后，不能在同一流上执行不同方向的操作。 因此，例如，程序不能在[cin](#cin)和[wcin](#wcin)上互换运行。

在此标头中声明的所有对象都共享一个奇特的属性 - 您可以假定它们是在您定义的任何静态对象之前构造的，在包含\<iostream>的转换单元中。 同样，您可以假定这些对象不会在您定义的任何此类静态对象的析构函数之前销毁。 （但是，输出流在程序终止期间被刷新。因此，您可以在程序启动之前和程序终止后安全地读取或写入标准流。

然而，这种保证并不普遍。 静态构造函数可能调用另一个翻译单元中的函数。 由于转换单元参与静态构造的顺序不确定，被调用函数不能假定在此标头中声明的对象已构造。 若要在此类上下文中使用这些对象，必须先构造 [ios_base::Init](../standard-library/ios-base-class.md#init) 类的对象。

### <a name="global-stream-objects"></a>全局流对象

|||
|-|-|
|[cerr](#cerr)|指定 `cerr` 全局流。|
|[Cin](#cin)|指定 `cin` 全局流。|
|[堵塞](#clog)|指定 `clog` 全局流。|
|[cout](#cout)|指定 `cout` 全局流。|
|[wcerr](#wcerr)|指定 `wcerr` 全局流。|
|[wc因](#wcin)|指定 `wcin` 全局流。|
|[wclog](#wclog)|指定 `wclog` 全局流。|
|[wcout](#wcout)|指定 `wcout` 全局流。|

### <a name="cerr"></a><a name="cerr"></a>塞勒

对象 `cerr` 控制输出到与 \<cstdio> 中声明的对象 `stderr` 关联的流缓冲区的过程。

```cpp
extern ostream cerr;
```

#### <a name="return-value"></a>返回值

[ostream](../standard-library/ostream-typedefs.md#ostream) 对象。

#### <a name="remarks"></a>备注

该对象控制以字节流的形式无缓冲插入到标准错误输出的过程。 构造对象后，表达式 `cerr.`[flags](../standard-library/ios-base-class.md#flags) `&` [unitbuf](../standard-library/ios-functions.md#unitbuf) 非零，且 `cerr.tie() == &cout`。

#### <a name="example"></a>示例

```cpp
// iostream_cerr.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

using namespace std;

void TestWide( )
{
   int i = 0;
   wcout << L"Enter a number: ";
   wcin >> i;
   wcerr << L"test for wcerr" << endl;
   wclog << L"test for wclog" << endl;
}

int main( )
{
   int i = 0;
   cout << "Enter a number: ";
   cin >> i;
   cerr << "test for cerr" << endl;
   clog << "test for clog" << endl;
   TestWide( );
}
```

### <a name="cin"></a><a name="cin"></a>Cin

指定 `cin` 全局流。

```cpp
extern istream cin;
```

#### <a name="return-value"></a>返回值

[istream](../standard-library/istream-typedefs.md#istream) 对象。

#### <a name="remarks"></a>备注

该对象控制以字节流的形式从标准输入中进行提取的过程。 构造对象后，`cin.`[tie](../standard-library/basic-ios-class.md#tie) 调用会返回 `&`[cout](#cout)。

#### <a name="example"></a>示例

在此示例中，`cin`在流遇到非数字字符时设置失败位。 程序清除失败位，并从流中剥离无效字符以继续。

```cpp
// iostream_cin.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main()
{
   int x;
   cout << "enter choice:";
   cin >> x;
   while (x < 1 || x > 4)
   {
      cout << "Invalid choice, try again:";
      cin >> x;
      // not a numeric character, probably
      // clear the failure and pull off the non-numeric character
      if (cin.fail())
      {
         cin.clear();
         char c;
         cin >> c;
      }
   }
}
```

```Output
2
```

### <a name="clog"></a><a name="clog"></a>堵塞

指定 `clog` 全局流。

```cpp
extern ostream clog;
```

#### <a name="return-value"></a>返回值

[ostream](../standard-library/ostream-typedefs.md#ostream) 对象。

#### <a name="remarks"></a>备注

该对象控制以字节流的形式缓冲插入到标准错误输出的过程。

#### <a name="example"></a>示例

有关使用 `clog` 的示例，请参阅 [cerr](#cerr)。

### <a name="cout"></a><a name="cout"></a>cout

指定 `cout` 全局流。

```cpp
extern ostream cout;
```

#### <a name="return-value"></a>返回值

[ostream](../standard-library/ostream-typedefs.md#ostream) 对象。

#### <a name="remarks"></a>备注

该对象控制以字节流的形式插入到标准输出的过程。

#### <a name="example"></a>示例

有关使用 `cout` 的示例，请参阅 [cerr](#cerr)。

### <a name="wcerr"></a><a name="wcerr"></a>wcerr

指定 `wcerr` 全局流。

```cpp
extern wostream wcerr;
```

#### <a name="return-value"></a>返回值

[wostream](../standard-library/ostream-typedefs.md#wostream) 对象。

#### <a name="remarks"></a>备注

该对象控制以宽流的形式无缓冲插入到标准错误输出的过程。 构造对象后，表达式 `wcerr.`[flags](../standard-library/ios-base-class.md#flags) `&` [unitbuf](../standard-library/ios-functions.md#unitbuf) 非零。

#### <a name="example"></a>示例

有关使用 `wcerr` 的示例，请参阅 [cerr](#cerr)。

### <a name="wcin"></a><a name="wcin"></a>wc因

指定 `wcin` 全局流。

```cpp
extern wistream wcin;
```

#### <a name="return-value"></a>返回值

[wistream](../standard-library/istream-typedefs.md#wistream) 对象。

#### <a name="remarks"></a>备注

该对象控制以宽流的形式从标准输入中进行提取的过程。 构造对象后，`wcin.`[tie](../standard-library/basic-ios-class.md#tie) 调用会返回 `&`[wcout](#wcout)。

#### <a name="example"></a>示例

有关使用 `wcin` 的示例，请参阅 [cerr](#cerr)。

### <a name="wclog"></a><a name="wclog"></a>wclog

指定 `wclog` 全局流。

```cpp
extern wostream wclog;
```

#### <a name="return-value"></a>返回值

[wostream](../standard-library/ostream-typedefs.md#wostream) 对象。

#### <a name="remarks"></a>备注

该对象控制以宽流的形式缓冲插入到标准错误输出的过程。

#### <a name="example"></a>示例

有关使用 `wclog` 的示例，请参阅 [cerr](#cerr)。

### <a name="wcout"></a><a name="wcout"></a>wcout

指定 `wcout` 全局流。

```cpp
extern wostream wcout;
```

#### <a name="return-value"></a>返回值

[wostream](../standard-library/ostream-typedefs.md#wostream) 对象。

#### <a name="remarks"></a>备注

该对象对将标准输出作为宽流插入的操作进行控制。

#### <a name="example"></a>示例

有关使用 `wcout` 的示例，请参阅 [cerr](#cerr)。

`wcout` 语句中的 `CString` 实例必须转换为 `const wchar_t*`，如下例所示。

```cpp
CString cs("meow");

wcout <<(const wchar_t*) cs <<endl;
```

有关详细信息，请参阅[基本 CString 操作](../atl-mfc-shared/basic-cstring-operations.md)。

## <a name="see-also"></a>另请参阅

[标题文件引用](../standard-library/cpp-standard-library-header-files.md)\
[C++标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[电流编程](../standard-library/iostream-programming.md)\
[iostreams 约定](../standard-library/iostreams-conventions.md)
