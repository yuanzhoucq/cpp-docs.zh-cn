---
title: "编译器选项宏 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- compiler options, macros
ms.assetid: a869adc6-b3de-4299-b040-9ae20b45f82c
caps.latest.revision: 17
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5187996fc377bca8633360082d07f7ec8a68ee57
ms.openlocfilehash: dbce962873194c1bdcb063537247650cff568e35
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-options-macros"></a>编译器选项宏
这些宏来控制特定的编译器功能。  
  
|||  
|-|-|  
|[_ATL_ALL_WARNINGS](#_atl_all_warnings)|这使在项目中的错误的符号转换从以前版本的 atl。|  
|[_ATL_APARTMENT_THREADED](#_atl_apartment_threaded)|如果一个或多个对象使用单元线程处理中定义。|  
|[_ATL_CSTRING_EXPLICIT_CONSTRUCTORS](#_atl_cstring_explicit_constructors)|确保`CString`显式的防止无意的任何转换构造函数。|  
|[_ATL_ENABLE_PTM_WARNING](#_atl_enable_ptm_warning)|定义此宏，以便使用 c + + 标准兼容的语法，其中的非标准语法用来初始化指向成员函数的指针时，将生成 C4867 编译器错误。|  
|[_ATL_FREE_THREADED](#_atl_free_threaded)|如果一个或多个对象使用空闲或非特定线程中定义。|  
|[_ATL_MULTI_THREADED](#_atl_multi_threaded)|指示的项目符号将具有标记为这两种，免费或非特定语言的对象。 该宏[_ATL_FREE_THREADED](#_atl_free_threaded)应改为使用。|  
|[_ATL_NO_AUTOMATIC_NAMESPACE](#_atl_no_automatic_namespace)|这样可以防止使用的默认命名空间的 atl。 作为符号|  
|[_ATL_NO_COM_SUPPORT](#_atl_no_com_support)|这样可防止 COM 相关的代码与您的项目正在编译符号。|  
|[ATL_NO_VTABLE](#atl_no_vtable)|防止在类的构造函数和析构函数中初始化 vtable 指针符号。|  
|[ATL_NOINLINE](#atl_noinline)|指示函数的符号不应为内联。|  
|[_ATL_SINGLE_THREADED](#_atl_single_threaded)|如果所有对象都使用单线程模型中，定义。|  
  
##  <a name="_atl_all_warnings"></a>_ATL_ALL_WARNINGS  
 这使在项目中的错误的符号转换从以前版本的 atl。  
  
```
#define _ATL_ALL_WARNINGS
```  
  
### <a name="remarks"></a>备注  
 Visual c + +.NET 2002 中之前, ATL 禁用了大量警告，并保留其禁用，以便它们永远不会显示在用户代码中的状态。 尤其是在下列情况下：  
  
-   C4127 条件表达式是常量  
  
-   C4786 identifier︰ 标识符被截断为调试信息中 number 个字符  
  
-   C4201 使用了非标准扩展︰ 无名称结构/联合  
  
-   C4103 filename: #pragma 包用于更改对齐方式  
  
-   C4291 declaration:; 如果找到任何匹配运算符 delete如果初始化引发异常，不会释放内存  
  
-   C4268 identifier: const 使用编译器生成默认构造函数初始化的静态/全局数据填充了零对象  
  
-   C4702 无法访问的代码  
  
 在项目转换从以前版本中，通过库标头仍禁用这些警告。  
  
 通过将以下行添加到 stdafx.h 文件中包括库标头之前，可以更改此行为。  
  
 [!code-cpp[NVC_ATL_Utilities #&97;](../../atl/codesnippet/cpp/compiler-options-macros_1.h)]  
  
 如果此`#define`ATL 标头非常小心地保留这些警告的状态，以便它们不全局禁用 （或用户显式禁用个别警告，不，使它们） 的添加。  
  
 生成带有 Visual c + +.NET 2002年的新项目将采用此`#define`在 stdafx.h 文件中设置默认情况下。  
  
##  <a name="_atl_apartment_threaded"></a>_ATL_APARTMENT_THREADED  
 如果一个或多个对象使用单元线程处理中定义。  
  
```
_ATL_APARTMENT_THREADED
```  
  
### <a name="remarks"></a>备注  
 指定单元线程处理。 请参阅[指定项目的线程模型](../../atl/specifying-the-threading-model-for-a-project-atl.md)其他线程处理选项，并[选项、 ATL 简单对象向导](../../atl/reference/options-atl-simple-object-wizard.md)有关的说明的线程模型可用于 ATL 对象。  
  
##  <a name="_atl_cstring_explicit_constructors"></a>_ATL_CSTRING_EXPLICIT_CONSTRUCTORS  
 确保`CString`显式的防止无意的任何转换构造函数。  
  
```
_ATL_CSTRING_EXPLICIT_CONSTRUCTORS
```  
  
### <a name="remarks"></a>备注  
 这是在定义时，采用单个参数的所有 CString 构造函数进行了都编译只有显式关键字，这可以防止隐式转换的输入参数。 这意味着，当定义了 _UNICODE，如果再尝试使用 char * 字符串作为 CString 构造函数参数，将导致编译器错误。 在您需要防止窄和宽字符串类型之间的隐式转换的情况下使用此宏。  
  
 通过对所有构造函数的字符串参数中使用 _T 宏，可以定义 _ATL_CSTRING_EXPLICIT_CONSTRUCTORS 和避免编译错误而不考虑是否定义了 _UNICODE。  
  
##  <a name="_atl_enable_ptm_warning"></a>_ATL_ENABLE_PTM_WARNING  
 定义此宏，以便强制对成员函数的指针的 ANSI c + + 标准符合语法的使用。 使用此宏会导致在非标准语法用来初始化指向成员函数的指针时生成 C4867 编译器错误。  
  
```
#define _ATL_ENABLE_PTM_WARNING
```  
  
### <a name="remarks"></a>备注  
 ATL 和 MFC 库已更改以匹配 Visual c + + 编译器的改进标准 c + + 合规性。 根据 ANSI c + + 标准中，指向类成员函数的指针的语法应该是`&CMyClass::MyFunc`。  
  
 当[_ATL_ENABLE_PTM_WARNING](#_atl_enable_ptm_warning)未定义 （默认情况），ATL/MFC，则禁用 C4867 错误 （值得注意的是消息映射） 的宏映射中，以便在早期版本中创建的代码可以继续像以前那样生成。 如果您定义**_ATL_ENABLE_PTM_WARNING**，您的代码应符合 c + + 标准。  
  
 但是，非标准窗体已被弃用，因此您需要将现有代码移到 c + + 标准符合语法。 例如，以下内容︰  
  
 [!code-cpp[NVC_MFCListView #&14;](../../atl/reference/codesnippet/cpp/compiler-options-macros_2.cpp)]  
  
 应改为︰  
  
 [!code-cpp[NVC_MFCListView #&11;](../../atl/reference/codesnippet/cpp/compiler-options-macros_3.cpp)]  
  
 请注意，对于映射添加.字符的宏，不应添加其再次在代码中。  
  
##  <a name="_atl_free_threaded"></a>_ATL_FREE_THREADED  
 如果一个或多个对象使用空闲或非特定线程中定义。  
  
```
_ATL_FREE_THREADED
```  
  
### <a name="remarks"></a>备注  
 指定自由线程处理。 自由线程处理等同于多线程单元模型。 请参阅[指定项目的线程模型](../../atl/specifying-the-threading-model-for-a-project-atl.md)其他线程处理选项，并[选项、 ATL 简单对象向导](../../atl/reference/options-atl-simple-object-wizard.md)有关的说明的线程模型可用于 ATL 对象。  
  
##  <a name="_atl_multi_threaded"></a>_ATL_MULTI_THREADED  
 指示的项目符号将具有标记为这两种，免费或非特定语言的对象。  
  
```
_ATL_MULTI_THREADED
```  
  
### <a name="remarks"></a>备注  
 如果定义了该符号后，ATL 会中拉入正确同步到的全局数据的访问权限的代码。 新的代码应使用等效宏[_ATL_FREE_THREADED](#_atl_free_threaded)相反。  
  
##  <a name="_atl_no_automatic_namespace"></a>_ATL_NO_AUTOMATIC_NAMESPACE  
 这样可以防止使用的默认命名空间的 atl。 作为符号  
  
```
_ATL_NO_AUTOMATIC_NAMESPACE
```  
  
### <a name="remarks"></a>备注  
 如果未定义此符号，则将执行包括 atlbase.h**使用 ATL 的命名空间**默认情况下，这可能会导致命名冲突。 若要避免此情形，定义此符号。  
  
##  <a name="_atl_no_com_support"></a>_ATL_NO_COM_SUPPORT  
 这样可防止 COM 相关的代码与您的项目正在编译符号。  
  
```
_ATL_NO_COM_SUPPORT```  
  
##  <a name="atl_no_vtable"></a>  ATL_NO_VTABLE  
 A symbol that prevents the vtable pointer from being initialized in the class's constructor and destructor.  
  
```
ATL_NO_VTABLE
```  
  
### Remarks  
 If the vtable pointer is prevented from being initialized in the class's constructor and destructor, the linker can eliminate the vtable and all of the functions to which it points. Expands to **__declspec(novtable)**.  
  
### Example  
 [!code-cpp[NVC_ATL_COM#53](../../atl/codesnippet/cpp/compiler-options-macros_4.h)]  
  
##  <a name="atl_noinline"></a>  ATL_NOINLINE  
 A symbol that indicates a function should not be inlined.  
  
```
    ATL_NOINLINE inline
    myfunction
 { ... }
```  
  
### Parameters  
 *myfunction*  
 The function that should not be inlined.  
  
### Remarks  
 Use this symbol if you want to ensure a function does not get inlined by the compiler, even though it must be declared as inline so that it can be placed in a header file. Expands to **__declspec(noinline)**.  
  
##  <a name="_atl_single_threaded"></a>  _ATL_SINGLE_THREADED  
 Define if all of your objects use the single threading model  
  
```
_ATL_SINGLE_THREADED
```  
  
### Remarks  
 Specifies that the object always runs in the primary COM thread. See [Specifying the Project's Threading Model](../../atl/specifying-the-threading-model-for-a-project-atl.md) for other threading options, and [Options, ATL Simple Object Wizard](../../atl/reference/options-atl-simple-object-wizard.md) for a description of the threading models available for an ATL object.  
  
## See Also  
 [Macros](../../atl/reference/atl-macros.md)

