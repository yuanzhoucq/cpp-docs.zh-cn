---
title: "lock::operator bool | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "operator bool"
  - "msclr.lock.operator bool"
  - "lock.operator bool"
  - "msclr::lock::operator bool"
  - "lock::operator bool"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "lock::operator bool"
ms.assetid: 007f0372-f812-4f1e-ba43-2584bd96eb11
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# lock::operator bool
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在条件表达式中，使用运算符 `lock` 。  
  
## 语法  
  
```  
operator bool();  
```  
  
## 返回值  
 `true`，如果锁保留，则为 `false`。  
  
## 备注  
 比 `bool` 安全的此运算符实际上转换为 `_detail_class::_safe_bool`，因为它无法转换为整型。  
  
## 示例  
 此示例使用在多个线程中类的一个实例。类使用自身上的锁确保每个线程对其内部数据的访问权限都是一致的。主应用程序线程使用类的同一实例的锁定定期检查任何辅助线程是否仍然存在，并且等待，直到退出所有辅助线程完成它们的任务。  
  
```  
// msl_lock_op_bool.cpp  
// compile with: /clr  
#include <msclr/lock.h>  
  
using namespace System;  
using namespace System::Threading;  
using namespace msclr;  
  
ref class CounterClass {  
private:  
   int Counter;     
  
public:  
   property int ThreadCount;  
  
   // function called by multiple threads, use lock to keep Counter consistent  
   // for each thread  
   void UseCounter() {  
      try {  
         lock l(this); // wait infinitely  
  
         Console::WriteLine("In thread {0}, Counter = {1}", Thread::CurrentThread->ManagedThreadId,   
            Counter);  
  
         for (int i = 0; i < 10; i++) {  
            Counter++;  
            Thread::Sleep(10);  
         }  
  
         Console::WriteLine("In thread {0}, Counter = {1}", Thread::CurrentThread->ManagedThreadId,   
            Counter);  
  
         Counter = 0;  
         // lock is automatically released when it goes out of scope and its destructor is called  
      }  
      catch (...) {  
         Console::WriteLine("Couldn't acquire lock!");  
      }  
  
      ThreadCount--;  
   }  
};  
  
int main() {  
   // create a few threads to contend for access to the shared data  
   CounterClass^ cc = gcnew CounterClass;  
   array<Thread^>^ tarr = gcnew array<Thread^>(5);  
   ThreadStart^ startDelegate = gcnew ThreadStart(cc, &CounterClass::UseCounter);  
   for (int i = 0; i < tarr->Length; i++) {  
      tarr[i] = gcnew Thread(startDelegate);  
      cc->ThreadCount++;  
      tarr[i]->Start();  
   }  
  
   // keep our main thread alive until all worker threads have completed  
   lock l(cc, lock_later); // don't lock now, just create the object  
   while (true) {  
      l.try_acquire(50); // try to acquire lock, don't throw an exception if can't  
      if (l) { // use bool operator to check for lock  
         if (0 == cc->ThreadCount) {  
            Console::WriteLine("All threads completed.");  
            break; // all threads are gone, exit while  
         }  
         else {  
            Console::WriteLine("{0} threads exist, continue waiting...", cc->ThreadCount);  
            l.release(); // some threads exist, let them do their work  
         }  
      }  
   }  
}  
```  
  
  **在线程 3，Counter \= 0**  
**在线程 3 ，Counter \= 10**  
**在线程 5 ，Counter \= 0**  
**在线程 5 ，Counter \= 10**  
**在线程 7 ，Counter \= 0**  
**在线程 7 ，Counter \= 10**  
**在线程 4 ，Counter \= 0**  
**在线程 4 ，Counter \= 10**  
**在线程 6 ，Counter \= 0**  
**在线程 6 ，Counter \= 10**  
**所有线程完成。**   
## 要求  
 **Header file** \<msclr\\lock.h\>  
  
 **Namespace** msclr  
  
## 请参阅  
 [锁定成员](../dotnet/lock-members.md)   
 [lock::is\_locked](../dotnet/lock-is-locked.md)