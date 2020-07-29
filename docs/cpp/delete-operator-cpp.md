---
title: delete 运算符 (C++)
ms.date: 08/12/2019
f1_keywords:
- delete_cpp
helpviewer_keywords:
- delete keyword [C++], syntax
- delete keyword [C++], deallocating objects
- delete keyword [C++]
ms.assetid: de39c900-3f57-489c-9598-dcb73c4b3930
ms.openlocfilehash: 19f92e2aa62adf1ede4c0e6ab1187fd9e4106e68
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221687"
---
# <a name="delete-operator-c"></a>delete 运算符 (C++)

释放内存块。

## <a name="syntax"></a>语法

> [ `::` ] `delete` *强制转换表达式*\
> [ `::` ] `delete []` *强制转换表达式*

## <a name="remarks"></a>备注

*强制转换表达式*参数必须是指向以前为使用[new 运算符](../cpp/new-operator-cpp.md)创建的对象分配的内存块的指针。 **`delete`** 运算符的结果为类型 **`void`** ，因此不返回值。 例如：

```cpp
CDialog* MyDialog = new CDialog;
// use MyDialog
delete MyDialog;
```

对 **`delete`** 未使用分配的对象的指针使用会 **`new`** 产生不可预知的结果。 但是，可以 **`delete`** 对值为0的指针使用。 此设置意味着，当 **`new`** 发生故障时返回0时，删除失败的操作的结果 **`new`** 是无害的。 有关详细信息，请参阅[new 和 Delete 运算符](../cpp/new-and-delete-operators.md)。

**`new`** 和 **`delete`** 运算符还可用于内置类型（包括数组）。 如果 `pointer` 引用数组，请在之前放置空括号（ `[]` ） `pointer` ：

```cpp
int* set = new int[100];
//use set[]
delete [] set;
```

**`delete`** 在对象上使用运算符将释放其内存。 在删除对象后取消引用指针的程序可能会产生不可预知的结果或崩溃。

当 **`delete`** 用于释放 c + + 类对象的内存时，将在释放对象的内存之前调用该对象的析构函数（如果该对象具有析构函数）。

如果运算符的操作数 **`delete`** 是可修改的左值，则在删除对象后，其值将为 undefined。

如果指定了[/sdl （启用附加安全检查）](/cpp/build/reference/sdl-enable-additional-security-checks)编译器选项，则在删除该对象后，该运算符的操作数将 **`delete`** 设置为无效的值。

## <a name="using-delete"></a>使用 delete

[Delete 运算符](../cpp/delete-operator-cpp.md)有两个句法变体：一个用于单个对象，另一个用于对象的数组。 以下代码段显示了它们之间的差异：

```cpp
// expre_Using_delete.cpp
struct UDType
{
};

int main()
{
   // Allocate a user-defined object, UDObject, and an object
   //  of type double on the free store using the
   //  new operator.
   UDType *UDObject = new UDType;
   double *dObject = new double;
   // Delete the two objects.
   delete UDObject;
   delete dObject;
   // Allocate an array of user-defined objects on the
   // free store using the new operator.
   UDType (*UDArr)[7] = new UDType[5][7];
   // Use the array syntax to delete the array of objects.
   delete [] UDArr;
}
```

以下两种情况会产生未定义的结果：在对象上使用 delete （）的数组形式 `delete []` ，并在数组上使用 delete 的删除形式。

## <a name="example"></a>示例

有关使用的示例 **`delete`** ，请参阅[new 运算符](../cpp/new-operator-cpp.md)。

## <a name="how-delete-works"></a>delete 的工作方式

Delete 运算符调用函数**运算符 delete**。

对于不属于类类型（[类](../cpp/class-cpp.md)、[结构](../cpp/struct-cpp.md)或[联合](../cpp/unions.md)）的对象，将调用全局 delete 运算符。 对于类类型的对象，如果删除表达式以一元范围解析运算符（）开头，则将在全局范围内解析释放函数的名称 `::` 。 否则，delete 运算符将在释放内存之前为对象调用析构函数（如果指针不为 null）。 可为每个类定义 delete 运算符；如果给定类不存在这种定义，则会调用全局 delete 运算符。 如果删除表达式用于释放其静态对象具有虚拟析构函数的类对象，则将通过对象的动态类型的虚拟析构函数解析释放函数。

## <a name="see-also"></a>另请参阅

[带有一元运算符的表达式](../cpp/expressions-with-unary-operators.md)\
[字](../cpp/keywords-cpp.md)\
[new 和 delete 运算符](../cpp/new-and-delete-operators.md)
