#include <stdio.h>
#include <stdlib.h>
#include <locale.h>
#include <math.h>

// Функция F(x, y, z)
double F(double x, double y, double z) {
    if (x >= 3 && y < 4 && z > 0) {
        return sin(x) + 2 * y;
    }
    else if (x < 3 && (y >= 0 && y <= 3) && (z >= -1 && z < 0)) {
        return log(fabs(x - z)) + pow(cos(y), 4.0);
    }
    else if (y < 0 && z < -1) {
        return pow(x * y + z, 1.0 / 5.0) * cos(4.0 * y);
    }
    return 0.0;
}

int main(void) {
    setlocale(LC_ALL, "RUS");

    double x, y, z;
    double n, m, step;

    /* ================= ЗАДАНИЕ 1 ================= */
    puts("--- Задание 1 ---");
    puts("Введите x, y, z:");
    scanf_s("%lf %lf %lf", &x, &y, &z);

    printf("Результат: %lf\n", F(x, y, z));

    /* ================= ЗАДАНИЕ 2 ================= */
    puts("\n--- Задание 2: Табулирование ---");
    puts("Введите n, m, step:");
    scanf_s("%lf %lf %lf", &n, &m, &step);

    if (n > m || step <= 0) {
        puts("Ошибка: неверно задан отрезок [n, m] или шаг.");
        return 1;
    }

    printf("+------------+------------+\n");
    printf("|     X      |  F(x,y,z)  |\n");
    printf("+------------+------------+\n");

    for (x = n; x <= m + step / 2.0; x += step) {
        printf("| %10.4f | %10.4f |\n", x, F(x, y, z));
    }

    printf("+------------+------------+\n");

    return 0;
}
