---
title: selectany
ms.date: 11/04/2016
f1_keywords:
- selectany_cpp
helpviewer_keywords:
- __declspec keyword [C++], selectany
- selectany __declspec keyword
ms.assetid: 9c353017-5a42-4f50-b741-bd13da1ce84d
ms.openlocfilehash: e279184322c239e7768eb8fd4321ee451b2cb94c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213224"
---
# `selectany`

**Microsoft 专用**

告知编译器声明的全局数据项（变量或对象）是“任一拣选”COMDAT（已包装函数）。

## <a name="syntax"></a>语法

> **`__declspec( selectany )`***声明符*

## <a name="remarks"></a>备注

在链接时，如果显示了 COMDAT 的多个定义，则链接器会选取一个定义并丢弃其余的定义。 如果选择了链接器选项 [`/OPT:REF`](../build/reference/opt-optimizations.md) （"优化"），则会发生 COMDAT，以删除链接器输出中所有未引用的数据项。

声明中的构造函数和全局函数或静态方法的赋值不创建引用，并且不会阻止 /OPT: REF 清除。 此类代码的副作用不应依赖于不存在对数据的其他引用的情况。

对于动态初始化的全局对象， **`selectany`** 也会丢弃未引用对象的初始化代码。

全局数据项一般只能在 EXE 或 DLL 项目中初始化一次。 **`selectany`** 当同一标头出现在多个源文件中时，可以使用来初始化由标头定义的全局数据。 **`selectany`** 适用于 C 和 c + + 编译器。

> [!NOTE]
> **`selectany`** 只能应用于外部可见的全局数据项的实际初始化。

## <a name="example"></a>示例

此代码演示如何使用 **`selectany`** 特性：

```cpp
//Correct - x1 is initialized and externally visible
__declspec(selectany) int x1=1;

//Incorrect - const is by default static in C++, so
//x2 is not visible externally (This is OK in C, since
//const is not by default static in C)
const __declspec(selectany) int x2 =2;

//Correct - x3 is extern const, so externally visible
extern const __declspec(selectany) int x3=3;

//Correct - x4 is extern const, so it is externally visible
extern const int x4;
const __declspec(selectany) int x4=4;

//Incorrect - __declspec(selectany) is applied to the uninitialized
//declaration of x5
extern __declspec(selectany) int x5;

// OK: dynamic initialization of global object
class X {
public:
X(int i){i++;};
int i;
};

__declspec(selectany) X x(1);
```

## <a name="example"></a>示例

此代码演示如何使用 **`selectany`** 属性来确保在您同时使用 [`/OPT:ICF`](../build/reference/opt-optimizations.md) 链接器选项时数据 COMDAT 折叠。 请注意，必须将数据标记为 **`selectany`** ，并将其放置在 **`const`** （readonly）部分中。 您必须显式指定只读部分。

```cpp
// selectany2.cpp
// in the following lines, const marks the variables as read only
__declspec(selectany) extern const int ix = 5;
__declspec(selectany) extern const int jx = 5;
int main() {
   int ij;
   ij = ix + jx;
}
```

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[`__declspec`](../cpp/declspec.md)<br/>
[关键字](../cpp/keywords-cpp.md)
