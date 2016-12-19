---
title: "新的 (在 vtable 的新槽) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "new 关键字 [C++]"
ms.assetid: 1a9a5704-f02f-46ae-ad65-f0f2b6dbabc3
caps.latest.revision: 20
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 新的 (在 vtable 的新槽)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`new` 关键字指示虚拟成员将在 vtable 中获得新槽。  
  
> [!NOTE]
>  `new` 关键字具有许多用途和含义。  有关更多信息，请参阅解疑主题[new](../misc/new.md)。  
  
## 所有运行时  
 （无适用于所有运行时的语言功能的备注。）  
  
## Windows 运行时  
 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]中不支持  
  
## [!INCLUDE[clr_for_headings](../dotnet/includes/clr_for_headings_md.md)]  
 **备注**  
  
 在 **\/clr** 编译，`new` 指示虚拟成员将在 vtable 中获得新槽；函数不重写基类方法。  
  
 `new` 导致newslot 修饰符添加到该函数的 IL。有关 newslot 视图的更多信息，请参见 。  
  
-   [\<caps:sentence id\="tgt11" sentenceid\="e9bb59a12f97840a5c3173bb77c6b5b1" class\="tgtSentence"\>MethodInfo.GetBaseDefinition 方法\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.reflection.methodinfo.getbasedefinition.aspx)  
  
-   [\<caps:sentence id\="tgt12" sentenceid\="f6ceddd85a425f38e7ed06e94a9808a9" class\="tgtSentence"\>MethodAttributes 枚举\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.reflection.methodattributes.aspx)  
  
### 要求  
 编译器选项：**\/clr**  
  
### 示例  
 **示例**  
  
 下面的示例显示了 `new` 的效果。  
  
```  
// newslot.cpp  
// compile with: /clr  
ref class C {  
public:  
   virtual void f() {  
      System::Console::WriteLine("C::f() called");  
   }  
  
   virtual void g() {  
      System::Console::WriteLine("C::g() called");  
   }  
};  
  
ref class D : public C {  
public:  
   virtual void f() new {  
      System::Console::WriteLine("D::f() called");  
   }  
  
   virtual void g() override {  
      System::Console::WriteLine("D::g() called");  
   }  
};  
  
ref class E : public D {  
public:  
   virtual void f() override {  
      System::Console::WriteLine("E::f() called");  
   }  
};  
  
int main() {  
   D^ d = gcnew D;  
   C^ c = gcnew D;  
  
   c->f();   // calls C::f  
   d->f();   // calls D::f  
  
   c->g();   // calls D::g  
   d->g();   // calls D::g  
  
   D ^ e = gcnew E;  
   e->f();   // calls E::f  
}  
```  
  
 **Output**  
  
  **C::f\(\) 被调用。**  
 **D::f\(\) 被调用。**  
 **D::g\(\) 被调用。**  
 **D::g\(\) 被调用。**  
 **E::f\(\)被调用。**   
## 请参阅  
 [适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)   
 [重写说明符](../windows/override-specifiers-cpp-component-extensions.md)