# Отчёт о тестировании Credit Card Number Validator.
*Статус валидации карт: OK|FAIL*

### Функциональность валидации банковских карт.

На тестирование затрачено: 1.5 часа

## В процессе тестирования использовались следующие артефакты:

* American Express (AMEX)_FAIL
* Diners Club - Carte Blanche_FAIL
* Diners Club - International_FAIL
* Diners Club - North America_OK
* Discover_OK
* InstaPayment_OK
* JCB_OK
* Maestro_OK
* MasterCard_OK
* Visa Electron_OK
* VISA_OK

В результате тестирования выявлены следующие дефекты:
* American Express (AMEX)
* Diners Club - Carte Blanche
* Diners Club - International

## Описание процесса тестирования:

*Вставка номера банковской карты в код.*


## В качестве тестовых данных использовались данные:

1. [Руководство по установке IntelliJ IDEA](https://github.com/netology-code/javaqa-homeworks/blob/master/intro/idea.md) 
2. Наработки программиста:
```java
public class Main {
  public static void main(String[] args) {
    // TODO: подставлять номер карты нужно сюда между двойными кавычками, без пробелов
    String number = "5351719427810741";
    System.out.println(String.format("Result is %s", isValidCardNumber(number) ? "OK" : "FAIL"));
  }

  public static boolean isValidCardNumber(String number) {
    if (number == null) {
      return false;
    }

    if (number.length() != 16) {
      return false;
    }

    long result = 0;
    for (int i = 0; i < number.length(); i++) {
      int digit;
      try {
        digit = Integer.parseInt(number.charAt(i) + "");
      } catch (NumberFormatException e) {
        return false;
      }

      if (i % 2 == 0) {
        digit *= 2;
        if (digit > 9) {
          digit -= 9;
        }
      }
      result += digit;
    }

    return (result != 0) && (result % 10 == 0);
  }
}
```
3. [Example report](https://github.com/netology-code/javaqa-homeworks/blob/master/intro/report.md)

## Тестирование производилось в следующем окружении:

* Window 10 x 64
* openjdk version "11.0.8" 2020-07-14 
OpenJDK Runtime Environment 
AdoptOpenJDK (build 11.0.8+10) 
OpenJDK 64-Bit Server VM AdoptOpenJDK (build 11.0.8+10, mixed mode)
