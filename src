//А591, Коцько П.А., метод Эрроу-Гурвица. Задание в программе - 4. Все вопросы - e49212@voenmeh.ru
#include <cmath>
#include <iostream>
#include <Eigen/Dense>

using namespace std;
using namespace Eigen;

double f(VectorXd x) {
  // Тут впишите функцию для расчета. Я решил для примера посчитать, так как пример очень редкий(я вообще не видел таких расчетов) 2-ю норму x(является мерой длины вектора x. Это означает, что vs попытаеvcz найти точку x, 
  //которая минимизирует длину вектора x(тут, она - точка x* = (0, 0) )
 return x.dot(x);
}

int main() {
  int n = 2;  
  VectorXd x(n), grad(n), d(n), H(n, n);
  double alpha = 0.1, beta = 0.5;
  
  // Инициализация x
  // Оценка градиента и "Гаусса" для x
  grad = ...;
  H = ...;
  
  // Проводить итерацию до сходимости 
  while (...) {
    // Гауссово приближение(аппроксимация)
    d = -H * grad;
    
    // Нахождение размера шага
    double t = 1;
    while (f(x + t * d) > f(x) + alpha * t * grad.dot(d)) {
      t *= beta;
    }
    
    // Делаем шажок в направлении поиска
    x += t * d;
    
    // Обновление -//- в новой точке.
    grad = ...;
    H = ...;
  }
  
  // Вывод минимальной точки и значение функции
  cout << "x* = " << x.transpose() << endl;
  cout << "f(x*) = " << f(x) << endl;
  
  return 0;
}
Если вы, по какой-то неведомой мне причине, используете Qt и вам запарно ставить "<Eigen/Dense>", то ловите "чистый" код.
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
//Альтернативный код, без "упрощения векторно-матричной жизни".
#include <cmath>
#include <iostream>

using namespace std;

// Тут по старинке, как и в том коде
double f(vector<double> x) {
  double sum = 0;
  for (double xi : x) {
    sum += xi * xi;
  }
  return sum;  // То же самое
}

int main() {
  int n = 2;  
  vector<double> x(n), grad(n), d(n), H(n * n);
  double alpha = 0.1, beta = 0.5;
  
  // 20-21 строки кода
  for (int i = 0; i < n; i++) {
    grad[i] = ...;
    for (int j = 0; j < n; j++) {
      H[i * n + j] = ...;
    }
  }
  
  // 25
  while (...) {
    // 27
    for (int i = 0; i < n; i++) {
      d[i] = 0;
      for (int j = 0; j < n; j++) {
        d[i] -= H[i * n + j] * grad[j];
      }
    }
    
    // 30
    double t = 1;
    vector<double> x_new = x;
    for (int i = 0; i < n; i++) {
      x_new[i] += t * d[i];
    }
    while (f(x_new) > f(x) + alpha * t * grad.dot(d)) {
      t *= beta;
      for (int i = 0; i < n; i++) {
        x_new[i] = x[i] + t * d[i];
      }
    }
    
    // 36
    x = x_new;
    
    // 39
    for (int i = 0; i < n; i++) {
      grad[i] = ...;
      for (int j = 0; j < n; j++) {
        H[i * n + j] = ...;
      }
    }
  }
  
  // Вывод
  cout << "x* = [";
  for (int i = 0; i < n; i++) {
    cout << x[i] << (i == n - 1 ? "]\n" : ", ");
  }
  cout << "f(x*) = " << f(x) << endl;
  
  return 0;
}
