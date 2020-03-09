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
ms.openlocfilehash: 2906e802072c43a93c59ca40d15e032adeeeef97
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78856464"
---
# <a name="ltiostreamgt"></a>&lt;iostream&gt;

声明控制从标准流读取和写入到标准流的对象。 这通常是你需要从C++程序执行输入和输出操作的唯一标头。

## <a name="syntax"></a>语法

```cpp
#include <iostream>
```

> [!NOTE]
> \<iostream > 库使用 `#include <ios>`、`#include <streambuf>`、`#include <istream>`和 `#include <ostream>` 语句。

## <a name="remarks"></a>备注

这些对象分为两组：

- [cin](#cin)、 [cout](#cout)、 [cerr](#cerr)和[堵塞](#clog)是面向字节的，可执行传统的一次性传输。

- [wcin](#wcin)、[wcout](#wcout)、[wcerr](#wcerr) 和 [wclog](#wclog) 面向宽字节，与程序内部操作的宽字符相互转换。

对流执行特定操作（如标准输入）后，不能对同一流执行不同方向的操作。 因此，程序不能在[cin](#cin)和[wcin](#wcin)上互换操作，例如。

此标头中声明的所有对象都共享特殊属性，您可以假设它们是在您定义的任何静态对象之前构造的，在包含 \<iostream > 的翻译单元中。 同样，你可以假定在你定义的任何此类静态对象的析构函数之前，这些对象不会被销毁。 （但是，在程序终止过程中输出流将刷新。）因此，您可以在程序启动之前和程序终止之后安全地读取或写入标准流。

但这种保证并不是通用的。 静态构造函数可能调用另一个翻译单元中的函数。 被调用的函数不能假定已构造了此标头中声明的对象，因为翻译单元在静态构造中的顺序不确定。 若要在此类上下文中使用这些对象，必须先构造 [ios_base::Init](../standard-library/ios-base-class.md#init) 类的对象。

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

###  <a name="cerr"></a>cerr

对象 `cerr` 控制输出到与 `stderr`cstdio> 中声明的对象 \< 关联的流缓冲区的过程。

```cpp
extern ostream cerr;
```

#### <a name="return-value"></a>返回值

[ostream](../standard-library/ostream-typedefs.md#ostream) 对象。

#### <a name="remarks"></a>备注

该对象控制以字节流的形式无缓冲插入到标准错误输出的过程。 构造对象后，表达式 `cerr.`[标志](../standard-library/ios-base-class.md#flags)`&` [unitbuf](../standard-library/ios-functions.md#unitbuf)为非零值，`cerr.tie() == &cout`。

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

###  <a name="cin"></a>cin

指定 `cin` 全局流。

```cpp
extern istream cin;
```

#### <a name="return-value"></a>返回值

[istream](../standard-library/istream-typedefs.md#istream) 对象。

#### <a name="remarks"></a>备注

该对象控制以字节流的形式从标准输入中进行提取的过程。 构造对象后，`cin.`[tie](../standard-library/basic-ios-class.md#tie) 调用会返回 `&`[cout](#cout)。

#### <a name="example"></a>示例

在此示例中，`cin` 在流出现在非数字字符的情况下设置失败位。 程序将清除失败位，并从流中去除无效字符以继续。

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

###  <a name="clog"></a>clog

指定 `clog` 全局流。

```cpp
extern ostream clog;
```

#### <a name="return-value"></a>返回值

[ostream](../standard-library/ostream-typedefs.md#ostream) 对象。

#### <a name="remarks"></a>备注

该对象控制以字节流的形式缓冲插入到标准错误输出的过程。

#### <a name="example"></a>示例

有关使用 [ 的示例，请参阅 ](#cerr)cerr`clog`。

###  <a name="cout"></a>cout

指定 `cout` 全局流。

```cpp
extern ostream cout;
```

#### <a name="return-value"></a>返回值

[ostream](../standard-library/ostream-typedefs.md#ostream) 对象。

#### <a name="remarks"></a>备注

该对象控制以字节流的形式插入到标准输出的过程。

#### <a name="example"></a>示例

有关使用 [ 的示例，请参阅 ](#cerr)cerr`cout`。

### <a name="wcerr"></a>wcerr

指定 `wcerr` 全局流。

```cpp
extern wostream wcerr;
```

#### <a name="return-value"></a>返回值

[wostream](../standard-library/ostream-typedefs.md#wostream) 对象。

#### <a name="remarks"></a>备注

该对象控制以宽流的形式无缓冲插入到标准错误输出的过程。 构造对象后，表达式 `wcerr.`[标志](../standard-library/ios-base-class.md#flags)`&` [unitbuf](../standard-library/ios-functions.md#unitbuf)为非零值。

#### <a name="example"></a>示例

有关使用 [ 的示例，请参阅 ](#cerr)cerr`wcerr`。

### <a name="wcin"></a>wcin

指定 `wcin` 全局流。

```cpp
extern wistream wcin;
```

#### <a name="return-value"></a>返回值

[wistream](../standard-library/istream-typedefs.md#wistream) 对象。

#### <a name="remarks"></a>备注

该对象控制以宽流的形式从标准输入中进行提取的过程。 构造对象后，`wcin.`[tie](../standard-library/basic-ios-class.md#tie) 调用会返回 `&`[wcout](#wcout)。

#### <a name="example"></a>示例

有关使用 [ 的示例，请参阅 ](#cerr)cerr`wcin`。

### <a name="wclog"></a>wclog

指定 `wclog` 全局流。

```cpp
extern wostream wclog;
```

#### <a name="return-value"></a>返回值

[wostream](../standard-library/ostream-typedefs.md#wostream) 对象。

#### <a name="remarks"></a>备注

该对象控制以宽流的形式缓冲插入到标准错误输出的过程。

#### <a name="example"></a>示例

有关使用 [ 的示例，请参阅 ](#cerr)cerr`wclog`。

### <a name="wcout"></a>wcout

指定 `wcout` 全局流。

```cpp
extern wostream wcout;
```

#### <a name="return-value"></a>返回值

[wostream](../standard-library/ostream-typedefs.md#wostream) 对象。

#### <a name="remarks"></a>备注

该对象对将标准输出作为宽流插入的操作进行控制。

#### <a name="example"></a>示例

有关使用 [ 的示例，请参阅 ](#cerr)cerr`wcout`。

`CString` 语句中的 `wcout` 实例必须转换为 `const wchar_t*`，如下例所示。

```cpp
CString cs("meow");

wcout <<(const wchar_t*) cs <<endl;
```

有关详细信息，请参阅[基本 CString 操作](../atl-mfc-shared/basic-cstring-operations.md)。

## <a name="see-also"></a>另请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)\
[C++ 标准库中的线程安全性](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream 编程](../standard-library/iostream-programming.md)\
[iostreams 约定](../standard-library/iostreams-conventions.md)
