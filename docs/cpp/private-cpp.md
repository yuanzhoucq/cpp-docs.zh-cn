---
title: 私有 （C++） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- private_cpp
dev_langs:
- C++
helpviewer_keywords:
- private keyword [C++]
ms.assetid: 94e99983-46a5-4e21-800c-28f8a7c6a8ff
caps.latest.revision: 10
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: baa3a23eacc8428bcbeb6ee5a88a835ff193ee02
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="private-c"></a>private (C++)
## <a name="syntax"></a>语法  
  
```  
private:  
   [member-list]  
private base-class  
```  
  
## <a name="remarks"></a>备注  
 当位于类成员列表之前时，`private` 关键字指定这些成员仅可从成员函数和该类的友元中进行访问。 这适用于声明到下一个访问指示符或类的末尾的所有成员。  
  
 当位于基类的名称之前时，`private` 关键字指定基类的公共成员和受保护成员为派生类的私有成员。  
  
 类中成员的默认访问是私有的。 结构或联合中成员的默认访问是公共的。  
  
 基类的默认访问对于类是私有的，而对于结构是公共的。  联合不能具有基类。  
  
 有关相关信息，请参阅[友元](../cpp/friend-cpp.md)，[公共](../cpp/public-cpp.md)，[保护](../cpp/protected-cpp.md)，和中的成员访问表[控制访问类成员](member-access-control-cpp.md).  
  
## <a name="clr-specific"></a>/clr 专用  
 在 CLR 类型中，C++ 访问说明符关键字 (**公共**， `private`，和`protected`) 可能会影响类型和方法与程序集相关的可见性。 有关详细信息，请参阅[成员访问控制](member-access-control-cpp.md)。  
  
> [!NOTE]
>  与已编译的文件[/LN](../build/reference/ln-create-msil-module.md)不受此行为。 在这种情况下，所有托管类（公共或私有）都将可见。  
  
## <a name="end-clr-specific"></a>END /clr 专用  
  
## <a name="example"></a>示例  
  
```  
// keyword_private.cpp  
class BaseClass {  
public:  
   // privMem accessible from member function  
   int pubFunc() { return privMem; }  
private:  
   void privMem;  
};  
  
class DerivedClass : public BaseClass {  
public:  
   void usePrivate( int i )  
      { privMem = i; }   // C2248: privMem not accessible  
                         // from derived class  
};  
  
class DerivedClass2 : private BaseClass {  
public:  
   // pubFunc() accessible from derived class  
   int usePublic() { return pubFunc(); }  
};  
  
int main() {  
   BaseClass aBase;  
   DerivedClass aDerived;  
   DerivedClass2 aDerived2;  
   aBase.privMem = 1;     // C2248: privMem not accessible  
   aDerived.privMem = 1;  // C2248: privMem not accessible  
                          //    in derived class  
   aDerived2.pubFunc();   // C2247: pubFunc() is private in  
                          //    derived class  
}  
```  
  
## <a name="see-also"></a>请参阅  
 [控制对类成员访问](member-access-control-cpp.md)   
 [关键字](../cpp/keywords-cpp.md)