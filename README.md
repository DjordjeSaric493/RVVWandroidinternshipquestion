# RVVWandroidinternshipquestion
easy asignment, I messed up 

evo kolika sam dijabola, prelak zadatak bio a pogubio se
package org.example


/**
Imam matricu nxn treba da vratim zbirove p1,p2,p3,p4 koji su zbirovi elemenata:
Levi deo (p1): elementi levo od obe dijagonale.

Gornji deo (p2): elementi iznad obe dijagonale.

Desni deo (p3): elementi desno od obe dijagonale.

Donji deo (p4): elementi ispod obe dijagonale.

 Ne računaš elemente glavne i sporedne dijagonale, pogledaj sliku u attachment

i\j  0   1   2   3   4
+---+---+---+---+---+
0  | G | . | . | . | S |
1  | 1 | G | . | S | 3 |
2  | 1 | 1 | G | 3 | 3 |
3  | 1 | S | 4 | G | 3 |
4  | S | . | . | . | G |
p1 (Levo): ispod glavne, levo od sporedne
j < i && j < n - 1 - i

p2 (Gore): iznad glavne, iznad sporedne
j < i && j > n - 1 - i

p3 (Desno): iznad glavne, desno od sporedne
j > i && j > n - 1 - i

p4 (Dole): ispod glavne, između sporedne i desne strane
j > i && j < n - 1 - i
 */
///TIP To <b>Run</b> code, press <shortcut actionId="Run"/> or
// click the <icon src="AllIcons.Actions.Execute"/> icon in the gutter.

fun calculateSums(matrix: Array<IntArray>, n: Int) {
    var p1 = 0  // Levi deo
    var p2 = 0  // Gornji deo
    var p3 = 0  // Desni deo
    var p4 = 0  // Donji deo

    for (i in 0 until n) {
        for (j in 0 until n) {
            // Preskoči ako je na glavnoj ili sporednoj dijagonali
            if (i == j || i + j == n - 1) continue

            // Dodaj u odgovarajući region
            when {
                j < i && j < n - 1 - i -> p1 += matrix[i][j]  // Levi deo
                j < i && j > n - 1 - i -> p2 += matrix[i][j]  // Gornji deo
                j > i && j > n - 1 - i -> p3 += matrix[i][j]  // Desni deo
                j > i && j < n - 1 - i -> p4 += matrix[i][j]  // Donji deo
            }
        }
    }

    println("Suma levog dela (p1): $p1")
    println("Suma gornjeg dela (p2): $p2")
    println("Suma desnog dela (p3): $p3")
    println("Suma donjeg dela (p4): $p4")
}

// Test primer
fun main() {
    val matrix = arrayOf(
        intArrayOf(1, 2, 3, 4, 5, 6),
        intArrayOf(7, 8, 9, 10, 11, 12),
        intArrayOf(13, 14, 15, 16, 17, 18),
        intArrayOf(19, 20, 21, 22, 23, 24),
        intArrayOf(25, 26, 27, 28, 29, 30),
        intArrayOf(31, 32, 33, 34, 35, 36)
    )
    calculateSums(matrix, 6)
}
