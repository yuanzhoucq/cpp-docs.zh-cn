---
title: lock::try_acquire
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- try_acquire
- lock.try_acquire
- msclr.lock.try_acquire
- lock::try_acquire
- msclr::lock::try_acquire
helpviewer_keywords:
- lock::try_acquire
ms.assetid: ef0649a9-e611-4495-84bd-2784533221d9
ms.openlocfilehash: ea16a495931c094a0088653bd0db9accca4bb486
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50440945"
---
# <a name="locktryacquire"></a>lock::try_acquire

获取一个对象，等待指定的时间内，并返回了锁`bool`报告成功的收购而不是引发异常。

## <a name="syntax"></a>语法

```
bool try_acquire(
   int _timeout_ms
);
bool try_acquire(
   System::TimeSpan _timeout
);
```

#### <a name="parameters"></a>参数

*超时) (_t*<br/>
超时值以毫秒为单位或作为<xref:System.TimeSpan>。

## <a name="return-value"></a>返回值

**true**已获取锁，如果**false**否则为。

## <a name="remarks"></a>备注

如果已获取锁，则此函数没有任何影响。

## <a name="example"></a>示例

此示例跨多个线程使用单个类的实例。  类自身上使用锁来确保对其内部数据的访问是为每个线程保持一致。  主应用程序线程的类的同一实例上使用锁来定期检查以查看任何工作线程仍存在，并等待，直到所有工作线程退出已完成其任务。

```cpp
// msl_lock_try_acquire.cpp
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
      if (l.try_acquire(50)) { // try to acquire lock, don't throw an exception if can't
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

```Output
In thread 3, Counter = 0
In thread 3, Counter = 10
In thread 5, Counter = 0
In thread 5, Counter = 10
In thread 7, Counter = 0
In thread 7, Counter = 10
In thread 4, Counter = 0
In thread 4, Counter = 10
In thread 6, Counter = 0
In thread 6, Counter = 10
All threads completed.
```

## <a name="requirements"></a>要求

**标头文件** \<msclr\lock.h >

**Namespace** msclr

## <a name="see-also"></a>请参阅

[lock 成员](../dotnet/lock-members.md)<br/>
[lock::acquire](../dotnet/lock-acquire.md)