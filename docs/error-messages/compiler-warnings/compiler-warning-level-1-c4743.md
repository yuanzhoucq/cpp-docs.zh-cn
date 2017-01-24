---
title: "编译器警告（等级 1）C4743 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4743"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4743"
ms.assetid: 2ee76ea3-77f3-4c2f-9a57-0751823c89fd
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4743
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'*type*'在'*file1*' 和 '*file2*'中具有不同的大小: *number* 和 *number* 字节  
  
 在两个文件中引用或定义的某个外部变量在这两个文件中具有不同类型，编译器确定该变量在 *file1* 中的大小与在 *file2*的大小不同。  
  
 以下是可以对 C\+\+ 发出此警告的重要情况。  如果在两个不同的文件中使用相同的名称声明相同的类型，并且这些声明包含虚函数且声明是不同的，则编译器可以针对虚函数表发出警告 C4744。  由于同一类型存在两个不同大小的虚函数表，并且链接器必须选择其中一个虚函数表并入可执行文件，因此出现此警告。这有可能导致程序调用错误的虚函数。  
  
 要消除此警告，要么使用相同的类型定义，要么对类型或变量使用不同的名称。  
  
## 示例  
 此示例包含类型的一个定义。  
  
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
  
## 示例  
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