---
title: selectany
ms.date: 11/04/2016
f1_keywords:
- selectany_cpp
helpviewer_keywords:
- __declspec keyword [C++], selectany
- selectany __declspec keyword
ms.assetid: 9c353017-5a42-4f50-b741-bd13da1ce84d
ms.openlocfilehash: e8ca82900ffd16264aca494950d4793029e55d9c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365601"
---
# <a name="selectany"></a>selectany

**微软特定**

告知编译器声明的全局数据项（变量或对象）是“任一拣选”COMDAT（已包装函数）。

## <a name="syntax"></a>语法

```
__declspec( selectany ) declarator
```

## <a name="remarks"></a>备注

在链接时，如果显示了 COMDAT 的多个定义，则链接器会选取一个定义并丢弃其余的定义。 如果选择了链接器选项[/OPT：REF（](../build/reference/opt-optimizations.md)优化），则将发生 COMDAT 消除以删除链接器输出中的所有未引用数据项。

声明中的构造函数和全局函数或静态方法的赋值不创建引用，并且不会阻止 /OPT: REF 清除。 此类代码的副作用不应依赖于不存在对数据的其他引用的情况。

对于动态初始化的全局对象 **，selectany**也将放弃未引用的对象的初始化代码。

全局数据项一般只能在 EXE 或 DLL 项目中初始化一次。 **当**同一标头出现在多个源文件中时，可以选择于初始化由标头定义的全局数据。 **选择在**C 和 C++ 编译器中都可用。

> [!NOTE]
> **selectany**只能应用于外部可见的全局数据项的实际初始化。

## <a name="example"></a>示例

此代码演示如何使用**selectany**属性：

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

此代码演示如何使用**selectany**属性来确保数据 COMDAT 折叠时，您也使用[/OPT：ICF](../build/reference/opt-optimizations.md)链接器选项。 请注意，数据必须使用**selectany**标记并放置在**const（** 只读）部分中。 您必须显式指定只读部分。

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

**结束微软特定**

## <a name="see-also"></a>另请参阅

[__declspec](../cpp/declspec.md)<br/>
[Keywords](../cpp/keywords-cpp.md)
