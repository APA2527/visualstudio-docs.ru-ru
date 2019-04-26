---
title: Пример кода для создания модульных тестов
description: Эта статья содержит пример кода, который может быть протестирован с помощью модульных тестов в Visual Studio.
ms.date: 11/04/2016
ms.topic: sample
helpviewer_keywords:
- unit test sample [Visual Studio]
- unit tests, samples
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0b914101a98f3eb40c479a3a39556e7e4138504c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62945725"
---
# <a name="sample-code-for-testing"></a>Пример кода для тестирования

Этот пример кода содержит класс *BankAccount* с различными методами, которые можно протестировать с помощью модульных тестов.

Этот код используется в следующих пошаговых руководствах:

- [Создание и запуск модульных тестов для управляемого кода](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md). Пошаговое руководство по созданию и настройке модульных тестов, их выполнению и изучению результатов.
- [Использование программы командной строки для тестирования](https://msdn.microsoft.com/Library/52c11992-9e94-4067-a4b7-59f19d69d867). В этом пошаговом руководстве с помощью программы командной строки *MSTest.exe* выполняются тесты и просматриваются результаты.

## <a name="sample-code"></a>Пример кода

Единственная умышленно допущенная в этом примере ошибка заключается в том, что у метода Debit в m_balance += amount вместо знака плюс перед знаком равно должен стоять минус.

```csharp
using System;

namespace BankAccountNS
{
    /// <summary>
    /// Bank Account demo class.
    /// </summary>
    public class BankAccount
    {
        private string m_customerName;

        private double m_balance;

        private bool m_frozen = false;

        private BankAccount()
        {
        }

        public BankAccount(string customerName, double balance)
        {
            m_customerName = customerName;
            m_balance = balance;
        }

        public string CustomerName
        {
            get { return m_customerName; }
        }

        public double Balance
        {
            get { return m_balance; }
        }

        public void Debit(double amount)
        {
            if (m_frozen)
            {
                throw new Exception("Account frozen");
            }

            if (amount > m_balance)
            {
                throw new ArgumentOutOfRangeException("amount");
            }

            if (amount < 0)
            {
                throw new ArgumentOutOfRangeException("amount");
            }

            m_balance += amount; // intentionally incorrect code
        }

        public void Credit(double amount)
        {
            if (m_frozen)
            {
                throw new Exception("Account frozen");
            }

            if (amount < 0)
            {
                throw new ArgumentOutOfRangeException("amount");
            }

            m_balance += amount;
        }

        private void FreezeAccount()
        {
            m_frozen = true;
        }

        private void UnfreezeAccount()
        {
            m_frozen = false;
        }

        public static void Main()
        {
            BankAccount ba = new BankAccount("Mr. Bryan Walton", 11.99);

            ba.Credit(5.77);
            ba.Debit(11.22);
            Console.WriteLine("Current balance is ${0}", ba.Balance);
        }
    }
}
```

/* Использованные в примерах компании, организации, продукты, доменные имена, адреса электронной почты, эмблемы, имена людей, географические названия и события являются вымышленными. Любые совпадения с реальными именами и названиями случайны. \*/

## <a name="create-the-project"></a>Создание проекта

Для работы с этим кодом сначала создадим для него проект в Visual Studio. Выполните шаги по созданию проекта из раздела [Пошаговое руководство. Создание и запуск модульных тестов для управляемого кода](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#create-a-project-to-test).

## <a name="see-also"></a>См. также

- [Пошаговое руководство: создание и запуск модульных тестов для управляемого кода](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)
- [Пошаговое руководство: Использование программы командной строки для тестирования](https://msdn.microsoft.com/Library/52c11992-9e94-4067-a4b7-59f19d69d867)
