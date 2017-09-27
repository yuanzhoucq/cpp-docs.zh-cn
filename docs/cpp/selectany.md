---
title: "selectany |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- selectany_cpp
- selectany
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], selectany
- selectany __declspec keyword
ms.assetid: 9c353017-5a42-4f50-b741-bd13da1ce84d
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 9c17221e2d0875505d9aa3f1132ea4a4b6d4c489
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="selectany"></a>selectany
**Microsoft 专用**  
  
 告知编译器声明的全局数据项（变量或对象）是“任一拣选”COMDAT（已包装函数）。  
  
## <a name="syntax"></a>语法  
  
```  
__declspec( selectany ) declarator  
```  
  
## <a name="remarks"></a>备注  
 在链接时，如果显示了 COMDAT 的多个定义，则链接器会选取一个定义并丢弃其余的定义。 如果链接器选项[/opt: ref](../build/reference/opt-optimizations.md) （优化） 为选中状态，则将进行 COMDAT 清除以链接器输出中删除所有未引用的数据的项。  
  
 声明中的构造函数和全局函数或静态方法的赋值不创建引用，并且不会阻止 /OPT: REF 清除。 此类代码的副作用不应依赖于不存在对数据的其他引用的情况。  
  
 对于动态初始化的全局对象，`selectany` 也将放弃一个未引用对象的初始化代码。  
  
 全局数据项一般只能在 EXE 或 DLL 项目中初始化一次。 当相同的标头出现在多个源文件中时，`selectany` 可用于初始化由标头定义的全局数据。 `selectany` 可用于 C 和 C++ 编译器。  
  
> [!NOTE]
>  `selectany` 只能应用于外部可见的全局数据项的实际初始化。  
  
## <a name="example"></a>示例  
 此代码演示如何使用 `selectany` 特性：  
  
```  
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
 此代码演示如何使用`selectany`特性来确保数据 COMDAT 折叠，当你同时使用[/opt: icf](../build/reference/opt-optimizations.md)链接器选项。 请注意，数据必须标有`selectany`并放置在**const** （只读） 部分。 您必须显式指定只读部分。  
  
```  
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
  
## <a name="see-also"></a>另请参阅  
 [__declspec](../cpp/declspec.md)   
 [关键字](../cpp/keywords-cpp.md)
