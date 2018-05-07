---
title: 编译器警告 (等级 1) C4743 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4743
dev_langs:
- C++
helpviewer_keywords:
- C4743
ms.assetid: 2ee76ea3-77f3-4c2f-9a57-0751823c89fd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 84b4d5f3aa465257d7efcf9f95584612214165b6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4743"></a>编译器警告（等级 1）C4743
*类型*中具有不同的大小*file1*和*file2*:*数*和*数*字节  
  
 在两个文件中定义或引用的外部变量，这些文件中具有不同类型和编译器确定中变量的大小*file1*中的变量的大小不同*file2*.  
  
 可以为 c + + 发出此警告时重要的用例。 如果你声明具有相同名称在两个不同的文件相同的类型，如果这些声明包含虚函数，并且如果声明不相同，编译器可以发出警告 C4744 虚函数表。 因为存在两个不同大小的虚函数表为同一类型，并且链接器必须选择其中一个来将合并到可执行文件，会出现的警告。  很可能这可能会导致程序调用错误的虚拟函数。  
  
 若要解决此警告，请使用相同的类型定义，或使用不同的类型或变量的名称。  
  
## <a name="example"></a>示例  
 此示例包含一个定义的类型。  
  
```  
// C4743a.cpp  
// compile with: /c  
class C {  
public:  
    virtual void f1(void);  
    virtual void f2(void);  
    virtual void f3(void);  
};  
  
void C::f1(void) {}  
void C::f2(void) {}  
void C::f3(void) {}  
C q;  
```  
  
## <a name="example"></a>示例  
 下面的示例生成 C4743。  
  
```  
// C4743b.cpp  
// compile with: C4743a.cpp /W1 /GL /O2  
// C4743 expected  
class C {  
public:  
    virtual void f1(void);  
    virtual void f2(void);  
    virtual void f3(void);  
    virtual void f4(void);  
    virtual void f5(void);  
};  
  
void C::f4(void) {}  
void C::f5(void) {}  
C x;  
  
int main() {}   
```