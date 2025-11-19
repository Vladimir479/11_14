#define _CRT_SECURE_NO_DEPRECATE
#include <stdio.h>
#include <locale.h>
#include <math.h>
#define N 100
#define M_PI            3.14159265358979323846

// Прототипы функций
void full_elements(double* ptr_array, int n);
void put_elements(double* ptr_array, int n);
void calc_elements(double* ptr_array, int n);
void task1();
void task2();

int main() {
    setlocale(LC_ALL, "");
    task1();
    task2();
    return 0;
}

// Функция для заполнения массива значениями функции (Задание 2 лаб 8 вариант 2)
void full_elements(double* ptr_array, int n) {
    double x, step;
    double start = 1.0;  
    double end = 3.0;    

    step = (end - start) / (n - 1);  

    for (int i = 0; i < n; i++) {
        x = start + i * step; 
        // y = x² - cos²(πx)  (вариант 2 из таблицы)
        ptr_array[i] = x * x - cos(M_PI * x) * cos(M_PI * x);
    }
}

void put_elements(double* ptr_array, int n) {
    for (int i = 0; i < n; i++) {
        printf("%.3f ", ptr_array[i]);
    }
    printf("\n");
}

void calc_elements(double* ptr_array, int n) {
    for (int i = 0; i < n; i++) {
        ptr_array[i] = ptr_array[i] * ptr_array[i];
    }
}

void task1() {
    double array[N];
    int size;

    printf("Введите размер массива: ");
    scanf("%d", &size);

    full_elements(array, size);

    printf("Исходный массив (y = x*x - cos*cos (Пx) на [1;3]): ");
    put_elements(array, size);

    calc_elements(array, size);
    printf("Массив в квадрате: ");
    put_elements(array, size);
}

// Задание 1.3 лаб 11 - обработка элементов массива
void task2() {
    int A, sum = 0;
    int array[10];

    printf("\n=== Задание 1.3 лаб 11 ===\n");
    printf("Введите 10 положительных и отрицательных целых чисел через пробел: ");
    for (int i = 0; i < 10; i++) {
        scanf("%d", &array[i]);
    }

    printf("Введите число A: ");
    scanf("%d", &A);

    for (int i = 0; i < 10; i++) {
        if (array[i] == A) {
            sum += i;
        }
    }

    printf("Сумма индексов элементов, равных A: %d\n", sum);
}
