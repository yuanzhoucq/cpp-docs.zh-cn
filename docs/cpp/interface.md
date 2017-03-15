---
title: "__interface | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "__interface"
  - "__interface_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__interface 关键字 [C++]"
ms.assetid: ca5d400b-d6d8-4ba2-89af-73f67e5ec056
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# __interface
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 可定义 Visual C\+\+ 接口，如下所示：  
  
-   可从零个或多个基接口继承。  
  
-   不能从基类继承。  
  
-   只能包含公共的纯虚方法。  
  
-   不能包含构造函数、析构函数或运算符。  
  
-   不能包含静态方法。  
  
-   不能包含数据成员；允许使用属性。  
  
## 语法  
  
```  
  
modifier  
 __interface interface-name {interface-definition};  
```  
  
## 备注  
 C\+\+ [类](../cpp/class-cpp.md)或[结构](../cpp/struct-cpp.md)可通过这些规则实现，但 `__interface` 会强制执行它们。  
  
 例如，以下是示例接口定义：  
  
```  
__interface IMyInterface {  
   HRESULT CommitX();  
   HRESULT get_X(BSTR* pbstrName);  
};  
```  
  
 有关托管接口的信息，请参阅[接口类](../windows/interface-class-cpp-component-extensions.md)。  
  
 请注意，您无需显式指示 `CommitX` 和 `get_X` 函数是纯虚函数。  第一个函数的等效声明为：  
  
```  
virtual HRESULT CommitX() = 0;  
```  
  
 `__interface` 表示 [novtable](../cpp/novtable.md) `__declspec` 修饰符。  
  
## 示例  
 以下示例演示如何使用接口中声明的属性。  
  
```  
// deriv_interface.cpp  
#define _ATL_ATTRIBUTES 1  
#include <atlbase.h>  
#include <atlcom.h>  
#include <string.h>  
#include <comdef.h>  
#include <stdio.h>  
  
[module(name="test")];  
  
[ object, uuid("00000000-0000-0000-0000-000000000001"), library_block ]  
__interface IFace {  
   [ id(0) ] int int_data;  
   [ id(5) ] BSTR bstr_data;  
};  
  
[ coclass, uuid("00000000-0000-0000-0000-000000000002") ]  
class MyClass : public IFace {  
private:  
    int m_i;  
    BSTR m_bstr;   
  
public:  
    MyClass()  
    {  
        m_i = 0;  
        m_bstr = 0;  
    }  
  
    ~MyClass()  
    {  
        if (m_bstr)   
            ::SysFreeString(m_bstr);  
    }  
  
    int get_int_data()  
    {  
        return m_i;  
    }  
  
    void put_int_data(int _i)   
    {  
        m_i = _i;  
    }  
  
    BSTR get_bstr_data()  
    {   
        BSTR bstr = ::SysAllocString(m_bstr);  
        return bstr;   
    }  
  
    void put_bstr_data(BSTR bstr)   
    {   
        if (m_bstr)   
            ::SysFreeString(m_bstr);  
        m_bstr = ::SysAllocString(bstr);  
    }  
};  
  
int main()  
{  
    _bstr_t bstr("Testing");  
    CoInitialize(NULL);  
    CComObject<MyClass>* p;  
    CComObject<MyClass>::CreateInstance(&p);  
    p->int_data = 100;  
    printf_s("p->int_data = %d\n", p->int_data);                
    p->bstr_data = bstr;  
    printf_s("bstr_data = %S\n", p->bstr_data);  
}  
```  
  
  **p\-\>int\_data \= 100**  
**bstr\_data \= Testing**   
## 结束 Microsoft 专用  
  
## 请参阅  
 [C\+\+ 关键字](../cpp/keywords-cpp.md)   
 [Interface Attributes](../windows/interface-attributes.md)