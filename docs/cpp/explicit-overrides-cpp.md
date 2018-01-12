---
title: "显式重写 （c + +） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- virtual functions [C++], explicit overrides
- overriding, functions
- derived classes [C++], virtual functions
- explicit virtual function overrides
- explicit override of virtual function
ms.assetid: ee583234-5cda-4e90-b55e-3f9fbf079ced
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8e2047b15d245c7c4b8e093e23a9ca6c4f16ac44
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="explicit-overrides-c"></a>显式重写 (C++)
**Microsoft 专用**  
  
 如果在两个或多中声明了同一虚函数[接口](../cpp/interface.md)并且如果从这些接口派生的类，可显式重写每个虚函数。  
  
 有关在使用新的托管的语法的托管代码中重写上显式的信息，请参阅[显式重写](../windows/explicit-overrides-cpp-component-extensions.md)。  
  
 **结束 Microsoft 专用**  
  
## <a name="example"></a>示例  
 以下代码示例演示了如何使用显式重载：  
  
```  
// deriv_ExplicitOverrides.cpp  
// compile with: /GR  
extern "C" int printf_s(const char *, ...);  
  
__interface IMyInt1 {  
   void mf1();  
   void mf1(int);  
   void mf2();  
   void mf2(int);  
};  
  
__interface IMyInt2 {  
   void mf1();  
   void mf1(int);  
   void mf2();  
   void mf2(int);  
};  
  
class CMyClass : public IMyInt1, public IMyInt2 {  
public:  
   void IMyInt1::mf1() {  
      printf_s("In CMyClass::IMyInt1::mf1()\n");  
   }  
  
   void IMyInt1::mf1(int) {  
      printf_s("In CMyClass::IMyInt1::mf1(int)\n");  
   }  
  
   void IMyInt1::mf2();  
   void IMyInt1::mf2(int);  
  
   void IMyInt2::mf1() {  
      printf_s("In CMyClass::IMyInt2::mf1()\n");  
   }  
  
   void IMyInt2::mf1(int) {  
         printf_s("In CMyClass::IMyInt2::mf1(int)\n");  
   }  
  
   void IMyInt2::mf2();  
   void IMyInt2::mf2(int);  
};  
  
void CMyClass::IMyInt1::mf2() {  
   printf_s("In CMyClass::IMyInt1::mf2()\n");  
}  
  
void CMyClass::IMyInt1::mf2(int) {  
   printf_s("In CMyClass::IMyInt1::mf2(int)\n");  
}  
  
void CMyClass::IMyInt2::mf2() {  
   printf_s("In CMyClass::IMyInt2::mf2()\n");  
}  
  
void CMyClass::IMyInt2::mf2(int) {  
   printf_s("In CMyClass::IMyInt2::mf2(int)\n");  
}  
  
int main() {  
   IMyInt1 *pIMyInt1 = new CMyClass();  
   IMyInt2 *pIMyInt2 = dynamic_cast<IMyInt2 *>(pIMyInt1);  
  
   pIMyInt1->mf1();  
   pIMyInt1->mf1(1);  
   pIMyInt1->mf2();  
   pIMyInt1->mf2(2);  
   pIMyInt2->mf1();  
   pIMyInt2->mf1(3);  
   pIMyInt2->mf2();  
   pIMyInt2->mf2(4);  
  
   // Cast to a CMyClass pointer so that the destructor gets called  
      CMyClass *p = dynamic_cast<CMyClass *>(pIMyInt1);  
      delete p;  
}  
```  
  
```Output  
In CMyClass::IMyInt1::mf1()  
In CMyClass::IMyInt1::mf1(int)  
In CMyClass::IMyInt1::mf2()  
In CMyClass::IMyInt1::mf2(int)  
In CMyClass::IMyInt2::mf1()  
In CMyClass::IMyInt2::mf1(int)  
In CMyClass::IMyInt2::mf2()  
In CMyClass::IMyInt2::mf2(int)  
```  
  
## <a name="see-also"></a>请参阅  
 [继承](../cpp/inheritance-cpp.md)