---
title: "委托和事件 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__delegate 关键字"
  - "__event 关键字 [C++]"
  - "delegate 关键字 [C++]"
  - "委托 [C++], 从 C++ 托管扩展升级"
  - "event 关键字 [C++]"
  - "事件 [C++], 从 C++ 托管扩展升级"
ms.assetid: 3505c626-7e5f-4492-a947-0e2248f7b84a
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 委托和事件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

从 C\+\+ 托管扩展到 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)]，声明委托和事件的方式发生了更改。  
  
 不再需要双下划线，如下面的示例中所示：  下面是一个托管扩展中的代码示例：  
  
```  
__delegate void ClickEventHandler(int, double);  
__delegate void DblClickEventHandler(String*);  
  
__gc class EventSource {  
   __event ClickEventHandler* OnClick;    
   __event DblClickEventHandler* OnDblClick;    
};  
```  
  
 在新语法中，该代码类似如下所示：  
  
```  
delegate void ClickEventHandler( int, double );  
delegate void DblClickEventHandler( String^ );  
  
ref class EventSource {  
   event ClickEventHandler^ OnClick;   
   event DblClickEventHandler^ OnDblClick;   
};  
```  
  
 事件（和委托）是引用类型，由于新语法中使用了帽子 \(`^`\)，所以在新语法中非常明显。事件支持前面代码中显示的显式声明语法和常用形式。  在显式形式中，用户指定与事件关联的 `add`、`raise` 和 `remove` 方法。（仅 `add` 和 `remove` 方法是必选项；`raise` 方法是可选项。）  
  
 在托管扩展中，如果您提供这些方法，则无需再提供显式事件声明，但必须确定不存在的事件的名称。  所有方法均以 `add_EventName`、`raise_EventName` 和 `remove_EventName` 形式指定，如托管扩展规范中举出的示例所示：  
  
```  
// explicit implementations of add, remove, raise  
public __delegate void f(int);  
public __gc struct E {  
   f* _E;  
public:  
   E() { _E = 0; }  
  
   __event void add_E1(f* d) { _E += d; }  
  
   static void Go() {  
      E* pE = new E;  
      pE->E1 += new f(pE, &E::handler);  
      pE->E1(17);   
      pE->E1 -= new f(pE, &E::handler);  
      pE->E1(17);   
   }  
  
private:  
   __event void raise_E1(int i) {  
      if (_E)  
         _E(i);  
   }  
  
protected:  
   __event void remove_E1(f* d) {  
      _E -= d;  
   }  
};  
```  
  
 新语法简化了声明，如下面的转换所示。  事件在事件声明及其关联的委托类型后的一对大括号内指定两个或三个方法，如下所示：  
  
```  
public delegate void f( int );  
public ref struct E {  
private:  
   f^ _E; // delegates are also reference types  
  
public:  
   E() {  // note the replacement of 0 with nullptr!  
      _E = nullptr;   
   }  
  
   // the new aggregate syntax of an explicit event declaration  
   event f^ E1 {  
   public:  
      void add( f^ d ) {  
         _E += d;  
      }  
  
   protected:  
      void remove( f^ d ) {  
         _E -= d;  
      }  
  
   private:  
      void raise( int i ) {  
         if ( _E )  
            _E( i );  
      }  
   }  
  
   static void Go() {  
      E^ pE = gcnew E;  
      pE->E1 += gcnew f( pE, &E::handler );  
      pE->E1( 17 );   
      pE->E1 -= gcnew f( pE, &E::handler );  
      pE->E1( 17 );   
   }  
};  
```  
  
## 请参阅  
 [类或接口中的成员声明 \(C\+\+\/CLI\)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)   
 [委托](../windows/delegate-cpp-component-extensions.md)   
 [event](../windows/event-cpp-component-extensions.md)