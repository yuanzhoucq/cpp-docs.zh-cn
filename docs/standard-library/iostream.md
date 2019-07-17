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
ms.openlocfilehash: fa90a861194275d8c82a407e2ca8db6e757aab35
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245230"
---
# <a name="ltiostreamgt"></a>&lt;iostream&gt;

声明控制从标准流读取和写入到标准流的对象。 包括通常是您需要执行操作的输入和输出中的唯一标头C++程序。

## <a name="syntax"></a>语法

```cpp
#include <iostream>
```

> [!NOTE]
> \<Iostream > 库使用`#include <ios>`， `#include <streambuf>`， `#include <istream>`，和`#include <ostream>`语句。

## <a name="remarks"></a>备注

这些对象分为两组：

- [cin](#cin)， [cout](#cout)， [cerr](#cerr)，并且[clog](#clog)面向字节，在进行传统的一次一字节传输。

- [wcin](#wcin)、[wcout](#wcout)、[wcerr](#wcerr) 和 [wclog](#wclog) 面向宽字节，与程序内部操作的宽字符相互转换。

后执行流，例如标准输入上的执行某些操作不能执行不同的方向的同一个流上执行操作。 因此，程序不能互换操作上都[cin](#cin)并[wcin](#wcin)，例如。

在此标头共享一个特殊属性声明的所有对象，可以假定定义，包括翻译单元中的任意静态对象之前构造\<iostream >。 同样，可以假定你定义的任何此类静态对象的析构函数之前不会销毁这些对象。 （但是，在程序终止过程中输出流将刷新。）因此，可以在程序启动之前和程序终止之后安全地读取或写入标准流。

这种保证并不通，但是。 静态构造函数可能调用另一个翻译单元中的函数。 所调用的函数不能假定此标头中声明的对象已被构造，给定在哪个翻译单元参与静态构造的不确定的顺序。 若要在此类上下文中使用这些对象，必须先构造 [ios_base::Init](../standard-library/ios-base-class.md#init) 类的对象。

### <a name="global-stream-objects"></a>全局流对象

|||
|-|-|
|[cerr](#cerr)|指定 `cerr` 全局流。|
|[cin](#cin)|指定 `cin` 全局流。|
|[clog](#clog)|指定 `clog` 全局流。|
|[cout](#cout)|指定 `cout` 全局流。|
|[wcerr](#wcerr)|指定 `wcerr` 全局流。|
|[wcin](#wcin)|指定 `wcin` 全局流。|
|[wclog](#wclog)|指定 `wclog` 全局流。|
|[wcout](#wcout)|指定 `wcout` 全局流。|

###  <a name="cerr"></a> cerr

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

###  <a name="cin"></a> cin

指定 `cin` 全局流。

```cpp
extern istream cin;
```

#### <a name="return-value"></a>返回值

[istream](../standard-library/istream-typedefs.md#istream) 对象。

#### <a name="remarks"></a>备注

该对象控制以字节流的形式从标准输入中进行提取的过程。 构造对象后，`cin.`[tie](../standard-library/basic-ios-class.md#tie) 调用会返回 `&`[cout](#cout)。

#### <a name="example"></a>示例

在此示例中，`cin`设置失败位流，就在非数字字符之间。 该程序清除失败位，并去除无效字符从流以继续。

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

###  <a name="clog"></a> clog

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

###  <a name="cout"></a> cout

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

### <a name="wcerr"></a> wcerr

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

### <a name="wcin"></a> wcin

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

### <a name="wclog"></a> wclog

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

### <a name="wcout"></a> wcout

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

```
CString cs("meow");

wcout <<(const wchar_t*) cs <<endl;
```

有关详细信息，请参阅[基本 CString 操作](../atl-mfc-shared/basic-cstring-operations.md)。

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)<br/>
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream 编程](../standard-library/iostream-programming.md)<br/>
[iostreams 约定](../standard-library/iostreams-conventions.md)<br/>
