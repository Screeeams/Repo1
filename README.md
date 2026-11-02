# Repo1



#include <stdio.h>
#include <stdlib.h>
#include <locale.h>
#include <math.h>

int main(void) {
    setlocale(LC_ALL, "RUS");

    double x, y, z;
    double n, m, step;
    double res = 0.0;

    /* ================= ЗАДАНИЕ 1 ================= */
    puts("--- Задание 1 ---");
    puts("Введите x, y, z:");
    scanf_s("%lf %lf %lf", &x, &y, &z);

    if (x >= 3 && y < 4 && z > 0) {
        res = sin(x) + 2 * y;
        printf("Результат: %lf\n", res);
    }
    else if (x < 3 && (y >= 0 && y <= 3) && (z >= -1 && z < 0)) {
        res = log(fabs(x - z)) + pow(cos(y), 4.0);
        printf("Результат: %lf\n", res);
    }
    else if (y < 0 && z < -1) {
        // Корень 5-й степени из (x*y + z) * cos(4y)
        res = pow(x * y + z, 1.0 / 5.0) * cos(4.0 * y);
        printf("Результат: %lf\n", res);
    }
    else {
        puts("Условия не выполнены");
    }

    /* ================= ЗАДАНИЕ 2 ================= */
    puts("\n--- Задание 2: Табулирование ---");
    puts("Введите n, m, step:");
    scanf_s("%lf %lf %lf", &n, &m, &step);

    if (n > m || step <= 0) {
        puts("Ошибка: неверно задан отрезок [n, m] или шаг.");
        return 1;
    }

    // Отрисовка шапки таблицы
    printf("+------------+------------+\n");
    printf("|     X      |  F(x,y,z)  |\n");
    printf("+------------+------------+\n");

    // Цикл от n до m с шагом step (y и z зафиксированы)
    for (x = n; x <= m + step / 2.0; x += step) {

        if (x >= 3 && y < 4 && z > 0) {
            res = sin(x) + 2 * y;
        }
        else if (x < 3 && (y >= 0 && y <= 3) && (z >= -1 && z < 0)) {
            res = log(fabs(x - z)) + pow(cos(y), 4.0);
        }
        else if (y < 0 && z < -1) {
            res = pow(x * y + z, 1.0 / 5.0) * cos(4.0 * y);
        }
        else {
            res = 0.0;
        }

        printf("| %10.4f | %10.4f |\n", x, res);
    }

    printf("+------------+------------+\n");

    return 0;
}
