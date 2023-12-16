package karazin.scala.users.group.week1.homework

import scala.annotation.tailrec
/**
 * Preface
 * Implement all the things with ???.
 * All implementations must be tail-recursive is possible.
 * Feel free to use internal methods/functions.
 * Feel free to adjust signatures of hacked methods/functions.
 *
 * 1. Boolean Operators
 * Required task
 * Implement eager boolean operations Not, And and Or.
 * Requirements:
 * a) the function should not use embedded boolean operations
 * b) the functions should be eager
 * c) the function should use `if` expression and `true` and `false` boolean literals 
 *
 * 2. Fermat Numbers
 * Required task
 * Implement function which should calculate n-th Fermat number:
 * Fn = 2 ^ (2 ^ n) + 1, n is non-negative
 * Requirements:
 * a) the function should not use multiplication and power operations
 * b) the functions should only use addition operation
 * For more details @see https://en.wikipedia.org/wiki/Fermat_number
 *
 * 3. Look-and-say Sequence
 * Required task
 * Implement function which should calculate n-th number of Look-and-say sequence
 * For more details @see https://en.wikipedia.org/wiki/Look-and-say_sequence
 *
 * 4. Kolakoski sequence
 * Optional super challenging task
 * Implement function which should calculate n-th number of Kolakoski sequence
 * For more details @see https://en.wikipedia.org/wiki/Kolakoski_sequence
 */

object Homework :

  object `Boolean Operators` :

    val int = 42

    def not(b: Boolean): Boolean = if (b) false else true// функция NOT, инвертирующая булево значение
    def and(left: Boolean, right: Boolean): Boolean = if (left) right else false  // функция AND, логическое "и" между двумя значениями
    def or(left: Boolean, right: Boolean): Boolean = if (left) true else right // функция OR, выполняющая логическое "или" между двумя значениями
 
  end `Boolean Operators`



  object `Fermat Numbers` :

  val multiplication: (BigInt, BigInt) => BigInt = (a, b) => { //реализация умножения
  }

  val power: (BigInt, BigInt) => BigInt = (base, exp) => { //реализация возведения в степень
  }

  val fermatNumber: Int => BigInt = n => {
    
  val addition: (BigInt, BigInt) => BigInt = (a, b) => if (b == 0) a else addition(a + 1, b - 1)
  // функция addition, представляющей собой сложение двух чисел a и b
  addition(1, power(2, power(2, n)))// рекурсивный вызов функции addition с параметрами 1 и результатом вызова функции power
  }

end `Fermat Numbers`



  object `Look-and-say Sequence` :
 
  val lookAndSaySequenceElement: Int => BigInt = n => {  // функция, вычисляющая n-й элемент последовательности Look-and-say
    @tailrec
    def lookAndSayHelper(count: Int, current: BigInt, acc: BigInt): BigInt = { // рекурсивная функция для построения элемента последовательности 
      if (count == 0) acc // если count достиг нуля, возвращаем аккумулятор(накопления результата в процессе выполнения рекурсивной функции)
      else {
        val digit = current % 10 // извлекаем последнюю цифру текущего числа 
        val newCount = countConsecutive(current, digit)// Считаем количество последовательных одинаковых цифр
        lookAndSayHelper(count - newCount, current / BigInt(10).pow(newCount), acc * BigInt(10) + newCount * 100 + digit)// Рекурсивный вызов с учетом нового элемента последовательности
      }
    }
    def countConsecutive(num: BigInt, digit: BigInt): Int = { // подсчет количества последовательных цифр
      if (num % 10 == digit) 1 + countConsecutive(num / 10, digit)
      else 0
    }

    lookAndSayHelper(n, 1, 0) // начальный вызов функции с параметрами n, 1 и 0
  }
end `Look-and-say Sequence`


end Homework
