---
title: "编译器警告（等级 1）C4462 | Microsoft Docs"
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
  - "C4462"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4462"
ms.assetid: 4e20aca4-293e-4c75-a83d-961c27ab7840
caps.latest.revision: 4
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4462
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

无法确定此类型的 GUID。程序可能在运行时失败。  
  
 当作为某个 Windows 运行时应用程序或组件的类型参数之一的公共 `TypedEventHandler` 具有对封闭类的引用时，该应用程序或组件中将出现警告 C4462。  
  
 **这种代码将引发警告：**  
  
```  
namespace N  
{  
       public ref struct EventArgs sealed {};  
       public ref struct R sealed  
       {  
              R() {}  
              event Windows::Foundation::TypedEventHandler<R ^, EventArgs^>^ e;  
       };  
}  
  
[Platform::MTAThread]  
int main()  
{  
     auto x = ref new N::R();  
}  
  
```  
  
 **修复错误：**  
  
 有两种解决此错误的方法。  一种方法（如下一个示例所示）是为事件提供内部可访问性，使它对同一可执行文件中的代码可用，而不对其他 Windows 运行时组件中的代码可用。  
  
```  
  
internal:  
event Windows::Foundation::TypedEventHandler<R ^, EventArgs^>^ e;  
  
```  
  
 如果事件必须是公共的，则可以使用另一个解决方法，即通过默认接口公开它：  
  
```  
  
ref struct R;  
public interface struct IR { event Windows::Foundation::TypedEventHandler<R ^, EventArgs^>^ e; };  
  
public ref struct R sealed : [Windows::Foundation::Metadata::Default] IR  
{  
    R() {}  
    virtual event Windows::Foundation::TypedEventHandler<R ^, EventArgs^>^ e;  
};  
  
```  
  
 仅当 `Windows::Foundation::TypedEventHandler<R ^, EventArgs^>^` 类型是从另一个组件访问时，才使用该类型的 GUID。  在采用第一个解决方法后，该类型只能在自己的组件中进行访问，因而可以解决问题。  否则，编译器不得不假定出现最坏的情况并发出警告。