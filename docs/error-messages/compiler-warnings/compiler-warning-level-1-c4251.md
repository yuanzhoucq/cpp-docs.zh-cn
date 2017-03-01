---
title: "编译器警告 （等级 1） C4251 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4251
dev_langs:
- C++
helpviewer_keywords:
- C4251
ms.assetid: a9992038-f0c2-4fc4-a9be-4509442cbc1e
caps.latest.revision: 16
author: corob-msft
ms.author: corob
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
translationtype: Machine Translation
ms.sourcegitcommit: 3f69f0c3176d2fbe19e11ce08c071691a72d858d
ms.openlocfilehash: b75c3e6c93c0963a692b210b158339ea5e9eacac
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-1-c4251"></a>编译器警告（等级 1）C4251
identifier︰ 类 'type' 需要具有 dll 的接口将由客户端的类 type2  
  
 若要在导出具有的类时，数据损坏的可能性降到最低[__declspec （dllexport)](../../cpp/dllexport-dllimport.md)，确保︰  
  
-   所有静态数据是通过从 DLL 导出的函数的访问。  
  
-   您的类的任何内联的方法可以不修改静态数据。  
  
-   您的类的任何内联的方法使用 CRT 函数，或使用静态数据的其他库函数 (请参阅[潜在错误对象跨 DLL 边界传递 CRT](../../c-runtime-library/potential-errors-passing-crt-objects-across-dll-boundaries.md)有关详细信息)。  
  
-   您的类的任何方法 (而不考虑内联) 可以使用类型其中 EXE 和 DLL 中的实例化具有静态数据差异。  
  
 您可以避免通过定义一个 DLL，它定义了一个类具有虚函数和函数您可以调用来实例化并删除对象类型的导出类。  您可以然后只需调用虚函数的类型。  
  
 导出模板的详细信息，请参阅[从中查看EN-US;&16895;8](http://support.microsoft.com/default.aspx?scid=KB;EN-US;168958)。  
  
 如果从 c + + 标准库，编译调试版本中的类型派生，可以忽略 C4251 (**/MTd**)，其中编译器错误消息是指 _Container_base。  
  
```  
// C4251.cpp  
// compile with: /EHsc /MTd /W2 /c  
#include <vector>  
using namespace std;  
class Node;  
class __declspec(dllimport) VecWrapper : vector<Node *> {};   // C4251  
```
