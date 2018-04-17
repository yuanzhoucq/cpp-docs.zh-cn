---
title: 标记语句 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- labeled statement
- statements, labeled
ms.assetid: 456a26d5-0fcc-4d1a-b71f-fa9ff3d73b91
caps.latest.revision: 10
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 139b94ab0287de5449e0b03ca96f5443049cfb5c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="labeled-statements"></a>标记语句
标签用于将程序控制权直接转交给特定语句。  
  
```  
identifier :  statement  
case constant-expression :  statement  
default :  statement  
```  
  
 标签的范围为整个函数，已在其中声明该标签。  
  
## <a name="remarks"></a>备注  
 有三种标记语句。 它们全都使用冒号将某种标签与语句隔开。 case 和 default 标签特定于 case 语句。  
  
```cpp  
#include <iostream>   
using namespace std;   
  
void test_label(int x) {  
  
    if (x == 1){  
        goto label1;  
    }  
    goto label2;  
  
label1:  
    cout << "in label1" << endl;  
    return;  
  
label2:  
    cout << "in label2" << endl;  
    return;  
}  
  
int main() {  
    test_label(1);  // in label1   
    test_label(2);  // in label2  
}  
  
```  
  
 **Goto 语句**  
  
 外观*标识符*标签在源程序中的声明了一个标签。 仅[goto](../cpp/goto-statement-cpp.md)语句可以将控制转移到*标识符*标签。 下面的代码段演示了的使用`goto`语句和*标识符*标签：  
  
 标签无法独立出现，必须总是附加到语句。 如果标签需要独立出现，则必须在标签后放置一个 null 语句。  
  
 标签具有函数范围，并且不能在函数中重新声明。 但是，相同的名称可用作不同函数中的标签。  
  
```  
// labels_with_goto.cpp  
// compile with: /EHsc  
#include <iostream>  
int main() {  
   using namespace std;  
   goto Test2;  
  
   cout << "testing" << endl;  
  
   Test2:  
      cerr << "At Test2 label." << endl;  
}  
  
//Output: At Test2 label.  
```  
  
 **Case 语句**  
  
 后显示的标签**用例**关键字不能外部显示`switch`语句。 (此限制也适用于**默认**关键字。)下面的代码段演示如何正确使用**用例**标签：  
  
```  
// Sample Microsoft Windows message processing loop.  
switch( msg )  
{  
   case WM_TIMER:    // Process timer event.  
      SetClassWord( hWnd, GCW_HICON, ahIcon[nIcon++] );  
      ShowWindow( hWnd, SW_SHOWNA );  
      nIcon %= 14;  
      Yield();  
      break;  
  
   case WM_PAINT:  
      memset( &ps, 0x00, sizeof(PAINTSTRUCT) );  
      hDC = BeginPaint( hWnd, &ps );   
      EndPaint( hWnd, &ps );  
      break;  
  
   default:  
      // This choice is taken for all messages not specifically  
      //  covered by a case statement.  
  
      return DefWindowProc( hWnd, Message, wParam, lParam );  
      break;  
}  
```  
  
## <a name="labels-in-the-case-statement"></a>case 语句中的标签  
 后显示的标签**用例**关键字不能外部显示`switch`语句。 (此限制也适用于**默认**关键字。)下面的代码段演示如何正确使用**用例**标签：  
  
```  
// Sample Microsoft Windows message processing loop.  
switch( msg )  
{  
   case WM_TIMER:    // Process timer event.  
      SetClassWord( hWnd, GCW_HICON, ahIcon[nIcon++] );  
      ShowWindow( hWnd, SW_SHOWNA );  
      nIcon %= 14;  
      Yield();  
      break;  
  
   case WM_PAINT:  
      // Obtain a handle to the device context.  
      // BeginPaint will send WM_ERASEBKGND if appropriate.  
  
      memset( &ps, 0x00, sizeof(PAINTSTRUCT) );  
      hDC = BeginPaint( hWnd, &ps );  
  
      // Inform Windows that painting is complete.  
  
      EndPaint( hWnd, &ps );  
      break;  
  
   case WM_CLOSE:  
      // Close this window and all child windows.  
  
      KillTimer( hWnd, TIMER1 );  
      DestroyWindow( hWnd );  
      if ( hWnd == hWndMain )  
         PostQuitMessage( 0 );  // Quit the application.  
      break;  
  
   default:  
      // This choice is taken for all messages not specifically  
      //  covered by a case statement.  
  
      return DefWindowProc( hWnd, Message, wParam, lParam );  
      break;  
}  
```  
  
## <a name="labels-in-the-goto-statement"></a>goto 语句中的标签  
 外观*标识符*标签在源程序中的声明了一个标签。 仅[goto](../cpp/goto-statement-cpp.md)语句可以将控制转移到*标识符*标签。 下面的代码段演示了的使用`goto`语句和*标识符*标签：  
  
 标签无法独立出现，必须总是附加到语句。 如果标签需要独立出现，则必须在标签后放置一个 null 语句。  
  
 标签具有函数范围，并且不能在函数中重新声明。 但是，相同的名称可用作不同函数中的标签。  
  
```  
// labels_with_goto.cpp  
// compile with: /EHsc  
#include <iostream>  
int main() {  
   using namespace std;  
   goto Test2;  
  
   cout << "testing" << endl;  
  
   Test2:  
      cerr << "At Test2 label." << endl;  
// At Test2 label.  
}  
  
```  
  
## <a name="see-also"></a>请参阅  
 [C++ 语句概述](../cpp/overview-of-cpp-statements.md)   
 [switch 语句 (C++)](../cpp/switch-statement-cpp.md)