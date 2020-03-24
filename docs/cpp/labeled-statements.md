---
title: 标记语句
ms.date: 11/04/2016
helpviewer_keywords:
- labeled statement
- statements, labeled
ms.assetid: 456a26d5-0fcc-4d1a-b71f-fa9ff3d73b91
ms.openlocfilehash: d971a0e9864aeada1db5f004ef70577512e78c76
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179687"
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

源程序中*标识符*标签的外观声明一个标签。 只有[goto](../cpp/goto-statement-cpp.md)语句才能将控件传输到*标识符*标签。 下面的代码段说明如何使用**goto**语句和*标识符*标签：

标签无法独立出现，必须总是附加到语句。 如果标签需要独立出现，则必须在标签后放置一个 null 语句。

标签具有函数范围，并且不能在函数中重新声明。 但是，相同的名称可用作不同函数中的标签。

```cpp
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

**Case**关键字后出现的标签也不能出现在**switch**语句的外部。 （此限制还适用于**default**关键字。）下面的代码片段演示了**case**标签的正确用法：

```cpp
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

**Case**关键字后出现的标签也不能出现在**switch**语句的外部。 （此限制还适用于**default**关键字。）下面的代码片段演示了**case**标签的正确用法：

```cpp
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

源程序中*标识符*标签的外观声明一个标签。 只有[goto](../cpp/goto-statement-cpp.md)语句才能将控件传输到*标识符*标签。 下面的代码段说明如何使用**goto**语句和*标识符*标签：

标签无法独立出现，必须总是附加到语句。 如果标签需要独立出现，则必须在标签后放置一个 null 语句。

标签具有函数范围，并且不能在函数中重新声明。 但是，相同的名称可用作不同函数中的标签。

```cpp
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

## <a name="see-also"></a>另请参阅

[ 语句概述](../cpp/overview-of-cpp-statements.md)<br/>
[switch 语句 (C++)](../cpp/switch-statement-cpp.md)
