---
title: Пример проекта для создания модульных тестов | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- unit test sample [Visual Studio]
- unit tests, samples
ms.assetid: db80aaf2-0652-4d3f-a8c5-2a98fd8502a2
caps.latest.revision: 32
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d495d0bf12c900d34a04a84e950b002494b7b5c3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660394"
---
# <a name="sample-project-for-creating-unit-tests"></a>Пример проекта для создания модульных тестов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Этот пример кода предназначен для использования в указанных ниже пошаговых руководствах.

- [Walkthrough: Creating and Running Unit Tests for Managed Code](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md) (Пошаговое руководство. Создание и запуск модульных тестов для управляемого кода). Пошаговое руководство по созданию и настройке модульных тестов, их выполнению и изучению результатов.

- [Пошаговое руководство. Запуск тестов и просмотр покрытия кода](https://msdn.microsoft.com/d4aab8e2-2140-4975-b4e3-41ef3fa944c8). В этом пошаговом руководстве описан порядок просмотра данных о покрытии кода, отражающих тестируемую часть кода проекта.

- [Walkthrough: using the command-line test utility](https://msdn.microsoft.com/library/52c11992-9e94-4067-a4b7-59f19d69d867) (Пошаговое руководство. Использование служебной программы для тестирования командной строки). В этом пошаговом руководстве с помощью программы командной строки MSTest.exe выполняются тесты и просматриваются результаты.

## <a name="sample-code"></a>Пример кода
 Единственная умышленно допущенная в этом примере ошибка заключается в том, что у метода Debit в m_balance += amount вместо знака плюс перед знаком равно должен стоять минус.

```
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

 /* Использованные в примерах компании, организации, продукты, доменные имена, адреса электронной почты, эмблемы, имена людей, географические названия и события являются вымышленными.  Любые совпадения с реальными именами и названиями случайны. \*/

## <a name="working-with-the-code"></a>Работа с кодом
 Для работы с этим кодом необходимо сначала создать для него проект в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Следуйте инструкциям из раздела, посвященного подготовке к выполнению [пошагового руководства по созданию и запуску модульных тестов](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md).

## <a name="see-also"></a>См. также раздел
 Пошаговое руководство [. Создание и запуск модульных тестов для управляемого кода](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md) [Пошаговое руководство. Запуск тестов и просмотр](https://msdn.microsoft.com/d4aab8e2-2140-4975-b4e3-41ef3fa944c8) [пошагового руководства по покрытию кода: использование служебной программы тестирования](https://msdn.microsoft.com/library/52c11992-9e94-4067-a4b7-59f19d69d867)
